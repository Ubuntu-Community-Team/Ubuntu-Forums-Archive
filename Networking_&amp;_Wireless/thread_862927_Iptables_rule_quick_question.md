---
title: "Iptables rule quick question"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by lavacano on 2008-07-18
Heya I got iptables and nat masquerade up from the tutorial at [http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)

so my problem is I'm rejecting some stuff from my ISP, this isnt a major blocker or anything but I was wondering if I could hush Rejectwall from a couple sources while still reporting from everything else.

```

root@chad.ath.cx:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       udp  --  anywhere             anywhere            udp spt:netbios-ns dpt:netbios-ns 
Rejectwall  all  --  anywhere             anywhere            
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,ACK/FIN 
Badflags   tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH 
Badflags   tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
Badflags   tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,PSH,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
Firewall   icmp --  anywhere             anywhere            
ACCEPT     all  --  73.246.0.1           anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID,NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain Badflags (11 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Badflags: ' 
DROP       all  --  anywhere             anywhere            

Chain Firewall (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Firewall: ' 
DROP       all  --  anywhere             anywhere            

Chain Rejectwall (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Rejectwall: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

```

```

root@chad.ath.cx:~# cat iptables.sh
#!/bin/sh
# 
# this script requires iptables package to be
# installed on your machine


# Where to find iptables binary
IPT="/sbin/iptables"
# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="eth0"
LAN="eth1"
# First we need to clear up any existing firewall rules
# and chain which might have been created
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# Default policies: Drop any incoming packets
# accept the rest.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# To be able to forward traffic from your LAN
# to the Internet, we need to tell the kernel
# to allow ip forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerading will make machines from the LAN
# look like if they were the router
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE


#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 2222 -j DNAT --to-destination 192.168.2.2:22
#$IPT -A FORWARD -i $WAN -p tcp  --dport 22 -m state --state NEW -j ACCEPT

# Do not allow other new or invalid connections to reach your internal network
$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN -j ACCEPT

# log those packets and inform the sender that the packet was rejected
$IPT -N Rejectwall
$IPT -A Rejectwall -m limit --limit 10/minute -j LOG --log-prefix "Rejectwall: "
$IPT -A Rejectwall -j REJECT
# use the following instead if you want to simulate that the host is not reachable
# for fun though
#$IPT -A Rejectwall -j REJECT  --reject-with icmp-host-unreachable

$IPT -A INPUT -p icmp -j ACCEPT

# Accept ssh connections from the Internet
$IPT -A INPUT -i $WAN -p tcp --dport 22 -j ACCEPT

# or only accept from a certain ip
#$IPT -A INPUT -i $WAN -s 125.124.123.122 -p tcp --dport 22 -j ACCEPT

# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall

# Here we define a new chain which is going to handle
# packets we don't want to respond to
# limit the amount of logs to 10/min
$IPT -N Firewall
$IPT -A Firewall -m limit --limit 10/minute -j LOG --log-prefix "Firewall: "
$IPT -A Firewall -j DROP

# here we create a chain to deal with unlegitimate packets
# and limit the number of alerts to 10/min
# packets will be drop without informing the sender
$IPT -N Badflags
$IPT -A Badflags -m limit --limit 10/minute -j LOG --log-prefix "Badflags: "
$IPT -A Badflags -j DROP 

# A list of well known combination of Bad TCP flags
# we redirect those to the Badflags chain
# which is going to handle them (log and drop)
$IPT -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,URG URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j Badflags 

# Accept certain icmp message, drop the others
# and log them through the Firewall chain
# 0 => echo reply
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
# 3 => Destination Unreachable
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
# 11 => Time Exceeded
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
# 8 => Echo
# avoid ping flood
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j Firewall 

```

and here's the kicker:

```

Jul 17 21:25:57 chad kernel: [76908.500491] Rejectwall: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:24:26:02:08:00 SRC=73.246.0.1 DST=255.255.255.255 LEN=356 TOS=0x00 PREC=0x00 TTL=64 ID=2180 PROTO=UDP SPT=67 DPT=68 LEN=336 
Jul 17 21:26:06 chad kernel: [76917.151029] Rejectwall: IN=eth0 OUT= MAC= SRC=24.16.175.13 DST=224.0.0.251 LEN=69 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=49 
Jul 17 21:26:09 chad kernel: [76920.150345] Rejectwall: IN=eth0 OUT= MAC= SRC=24.16.175.13 DST=224.0.0.251 LEN=69 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=49 
Jul 17 21:26:32 chad kernel: [76943.125189] Rejectwall: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:24:26:02:08:00 SRC=73.246.0.1 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=64 ID=3011 PROTO=UDP SPT=67 DPT=68 LEN=312

```

and etc. etc. etc.  

Any help is muchas appreciated

---

### Post by dmizer on 2008-07-18
if all you need to do is share your internet connection, ditch that howto.  you seem to have way more iptables rules than is necessary for a functioning internet connection sharing NAT.

reset your iptables to default (this will remove any custom chains you've built, so if you need custom chains, don't do this):
```
sudo iptables -F
```

check out this howto instead: [https://help.ubuntu.com/community/Internet/ConnectionSharing?](https://help.ubuntu.com/community/Internet/ConnectionSharing?)

---

