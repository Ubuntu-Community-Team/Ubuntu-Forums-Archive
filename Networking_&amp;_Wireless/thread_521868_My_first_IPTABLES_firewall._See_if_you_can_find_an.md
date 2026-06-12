---
title: "My first IPTABLES firewall. See if you can find anything wrong..."
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-08-09
```

#!/bin/sh

IPTABLES=/sbin/iptables
AWK=/usr/bin/awk
IFCONFIG=/sbin/ifconfig

EXTIF="eth0"
INTIF="eth1"
EXTIP="`$IFCONFIG $EXTIF | $AWK /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
INTNET="10.10.1.0/24"
INTIP="10.10.1.1/32"
UNIVERSE="0.0.0.0/0"

# enable IP forwarding.
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

# Clear rules and set default policy to DROP
$IPTABLES -F
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -Z

# ----- Begin PREROUTING (port forwarding) Section -----
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 3389 -j DNAT --to-destination 10.10.1.10
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 22 -j DNAT --to-destination 10.10.1.11
# ----- End PREROUTING (port forwarding) Section -----


# loopback interfaces are valid.
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
# local interface, local machines, going anywhere is valid
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
# remote interface, claiming to be local machines, IP spoofing, get lost
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j REJECT
# Allow any related traffic coming back to the MASQ server in. STATEFULLY TRACKED
$IPTABLES -A INPUT -i $EXTIF -m state --state ESTABLISHED,RELATED -j ACCEPT

# incoming openvpn traffic is valid
$IPTABLES -A INPUT -i tun0 -j ACCEPT

#----- Begin OPTIONAL INPUT Section -----
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 10000 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p tcp --dport 2222 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -p tcp --dport 2222 -j ACCEPT
# ----- End OPTIONAL INPUT Section -----

# Catch all rule, all other incoming is denied
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT

# openvpn traffic going out is valid
$IPTABLES -A OUTPUT -o tun0 -j ACCEPT

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
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 10.10.1.11 --dport 22 -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i $EXTIF -d 10.10.1.10 --dport 3389 -j ACCEPT
# ----- End OPTIONAL FORWARD Section -----

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch all rule, all other forwarding is denied and logged. 
$IPTABLES -A FORWARD -j REJECT

# Enabling SNAT (MASQUERADE) functionality on $EXTIF
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE


```


Learning iptables so I can provide a lower cost router to a bunch of my clients (vs. cisco / astaro / sonicwall)

This is my basic script for use at home. It's also got openvpn running on it. 

See if you can poke any holes in the code, or use it as an example for yourself!

---

### Post by Underpants on 2007-08-09
I have a problem with the OPENVPN rules. the router can connect and ping remote machines. but anything behind the NAT (machine I'm chatting on) cannot reach remote machines.

Ideas?

---

### Post by Underpants on 2007-08-10
bump, anyone?

---

