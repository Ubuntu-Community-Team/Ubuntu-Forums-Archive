---
title: "Problem with internet sharing"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by mexus on 2008-11-18
I have one ubuntu 8.10 server running perfect .... sharing internet (NAT).
Now i'm making one for my office and there is a problem:

eth0 192.168.99.254 netmask 255.255.255.0 (LOCAL NETWORK)
eth1 192.168.0.252    netmask 255.255.255.0 (Internet)

/etc/sysclt.conf:
net.ipv4.ip_forward=1

The problem is that form the client:
I can ping 192.168.99.254 (192.168.0.252)
I can't ping 192.168.0.1 
Where is the problem?????

Here is the script i use:

```

#!/bin/sh
IPTABLES=/sbin/iptables
LAN=192.168.99.254
LAN_ETH=eth0
INET_IP=192.168.0.252
INET_ETH=eth1
route add default gw 192.168.0.1
echo "1" > /proc/sys/net/ipv4/ip_forward
$IPTABLES -P OUTPUT DROP
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -F INPUT
$IPTABLES -F OUTPUT
$IPTABLES -F FORWARD
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD ACCEPT
#allow access to loopack
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT
#Deny all, allow LAN
$IPTABLES -A FORWARD -i $LAN_ETH -s $LAN -p tcp --sport 137:139 -d ! $LAN -j DROP
$IPTABLES -A FORWARD -i $LAN_ETH -s $LAN -p udp --sport 135:139 -d ! $LAN -j DROP
$IPTABLES -A FORWARD -i $LAN_ETH -s $LAN -p tcp --sport 445 -d ! $LAN -j DROP
$IPTABLES -A FORWARD -i $LAN_ETH -s $LAN -p udp --sport 445 -d ! $LAN -j DROP
 
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT 

 
$IPTABLES -A INPUT -i $LAN_ETH -s $LAN -j ACCEPT
 
$IPTABLES -A OUTPUT -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

 
$IPTABLES -t nat -A POSTROUTING -o $INET_ETH -s $LAN -d ! $LAN -j SNAT --to $INET_IP
 

```

---

### Post by SpaceTeddy on 2008-11-19
there are two (possible) causes here:
1.) back-channel is missing 

> $IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT 

allows the replies to pass through your firewall - but where do you allow the replies to pass back ? as far as i know, icmp is a stateles protocol not being picked up by the --state module - this it will not enter the connection tracking and the reply packet is dropped

2.) return route is missing

does your client on the 192.168.0.0/24 network know where to find the 192.168.254.0/24 network ? did you add routes to the network on the client on the clients default gateway ? if not, then the client does not know where to send the replies to and they get "lost" somehwere on the internet until they time out.

hope it helps...

[EDIT]
what i just saw... your ACCEPT rules for samba do not specify the -m state --state NEW flags - they really should, because at the moment they accept for more than you probably want...

---

