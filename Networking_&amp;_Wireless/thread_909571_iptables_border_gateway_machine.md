---
title: "iptables: border gateway machine?"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Underpants on 2008-09-03
I need to set up some impromptu monitoring. I need to be able to watch all traffic between a router and a firewall. 

This is the layout I want.

```
INTERNET -> ROUTER -> BOX I WISH TO CREATE -> FIREWALL -> SWITCHES AND CORPORATE NETWORK
```

I was wanting to set up set up a box with two nics and set it up as a border gateway and use something like NTOP or iptraf to monitor what's going on. (I have some suspicious bandwidth usage that I need to track down) 


So, I'm guessing I need to set up a slick little iptabes configuration to basically pass all traffic back and forth with no restrictions whatsoever. 

I'm not sure on the capabilities of the monitoring software, but I believe a port mirror could work. I'd have to test it. I don't have the right kind of switch laying around to set that up. A hub should do the same thing, correct?



What do I need to do with the machine if I have to go the two nics route?


Here is an example iptables firewall that I've been using for quite a while. It's not exactly what I need but I just wanted to show that I half way know what I'm doing... but some assistance would be nice.

```
#!/bin/sh

IPTABLES=/sbin/iptables
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig
EXTIF="eth0"
INTIF="eth1"
EXTIP="x.x.x.x"
INTNET="192.168.11.0/24"
INTIP="192.168.11.254/24"
UNIVERSE="0.0.0.0/0"

# enable IP forwarding.
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

# Clear rules and set default policy to DROP
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -Z

## ----- Begin PREROUTING (port forwarding) Section -----
$IPTABLES -t nat -A PREROUTING -p tcp --dport 3389 -j DNAT --to-destination 192.168.11.164
$IPTABLES -t nat -A PREROUTING -p tcp --dport 22 -j DNAT --to-destination 192.168.11.160
$IPTABLES -t nat -A PREROUTING -p tcp --dport 3341 -j DNAT --to-destination 192.168.11.166
$IPTABLES -t nat -A PREROUTING -p tcp --dport 443 -j DNAT --to-destination 192.168.11.10
$IPTABLES -t nat -A PREROUTING -p tcp --dport 2525 -j DNAT --to-destination 192.168.11.10
$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.168.11.11
$IPTABLES -t nat -A PREROUTING -p tcp --dport 25 -j DNAT --to-destination 192.168.11.11

# ----- BEGIN VPN SECTION -----
$IPTABLES -t nat -A PREROUTING -p udp --dport 1194 -j DNAT --to-destination 192.168.11.160
$IPTABLES -t nat -A PREROUTING -p udp --dport 1195 -j DNAT --to-destination 192.168.11.11
# ----- END VPN SECTION -----

# ----- BEGIN VNC SECTION -----
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5500 -j DNAT --to-destination 192.168.11.160
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5501 -j DNAT --to-destination 192.168.11.161
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5502 -j DNAT --to-destination 192.168.11.162
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5503 -j DNAT --to-destination 192.168.11.163
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5504 -j DNAT --to-destination 192.168.11.164
$IPTABLES -t nat -A PREROUTING -p tcp --dport 5505 -j DNAT --to-destination 192.168.11.165
# ----- END VNC SECTION -----

## ----- End PREROUTING (port forwarding) Section -----

# loopback interfaces are valid.
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# local interface, local machines, going anywhere is valid
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
# remote interface, claiming to be local machines, IP spoofing, get lost
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT
# Allow any related traffic coming back to the MASQ server in. STATEFULLY TRACKED
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT

# ----- Begin OPTIONAL INPUT Section -----
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 2222 -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p tcp --dport 2222 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 10000 -j ACCEPT
# ----- End OPTIONAL INPUT Section -----

# Catch all rule, all other incoming is denied
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# Workaround bug in netfilter
# See http://www.netfilter.org/security/2002-04-02-icmp-dnat.html
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP
# loopback interface is valid.
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# local interfaces, any source going to local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT
# local interface, MASQ server source going to the local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT
# outgoing to local net on remote interface, stuffed routing, deny
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j REJECT
# anything else outgoing on remote interface is valid
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
# Catch all rule, all other outgoing is denied and logged. 
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# ----- Begin OPTIONAL FORWARD Section -----
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.164 --dport 3389
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.160 --dport 22
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.166 --dport 3341
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.10 --dport 443
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.10 --dport 2525
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.11 --dport 80
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.11 --dport 25

# ----- BEGIN VPN SECTION -----
$IPTABLES -A FORWARD -p udp -i $EXTIF -d 10.10.11.160 --dport 1194
$IPTABLES -A FORWARD -p udp -i $EXTIF -d 10.10.11.10 --dport 1195 
# ----- END VPN SECTION -----

# ----- BEGIN VNC SECTION -----
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.160 --dport 5500
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.161 --dport 5501
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.162 --dport 5502
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.163 --dport 5503
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.164 --dport 5504
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 192.168.11.165 --dport 5505
# ----- END VNC SECTION -----

# ----- End OPTIONAL FORWARD Section -----

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch all rule, all other forwarding is denied and logged. 
$IPTABLES -A FORWARD -j REJECT

# Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE


```

---

