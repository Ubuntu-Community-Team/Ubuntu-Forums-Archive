---
title: "new born among you"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by robert.ion on 2007-05-31
Hi. I am new born in linux world. My born was assisted by ubuntu comunity :)
So. I write my first script for my first ubuntu server for secure it. I connect to server throught ssh and when i run the script I got the message:
BAD STATE `' 
and my ssh sesion is disconnected and ip 192.168.42.198 is loosing the internet access, but my  ip (192.168.42.3) still have internet connection.
I don-t know why, can you help me? please ?
Here is my script . I tryed to copy exactly.

#!/bin/sh
#nano -w/ IMRfirewall
RDS_IP="xxx.xxx.xxx.xxx"
IPTABLES="/sbin/iptables"
RDS_NIC="eth0"
INT_NIC="eth1"
INT_IP="192.168.42.40"
INT_LAN="192.168.42.0/24"

#delete previous rules
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F
$IPTABLES -X

#by default drop all
$IPTABLES -t filter -P INPUT DROP
$IPTABLES -t filter -P OUTPUT DROP
$IPTABLES -t filter -P FORWARD DROP

#input chain
#do not allow pachets that are not connection request (syn)
$IPTABLES -t filter -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
$IPTABLES -t filter -A INPUT -p all -m state --state INVALID -j DROP

#permit established connection
$IPTABLES -t filter -A INPUT -m state --state ESTABLISHED, RELATED -j ACCEPT

#ssh from outside to inside
$IPTABLES -t filter -A INPUT -p tcp -i $RDS_NIC --dport 22 -d $RDS_IP -s xxx.xxx.xxx.xxx/xx -m state --state NEW -j ACCEPT

#ssh from inside to server
$IPTABLES -t filter -A INPUT -p tcp -i $INT_NIC --dport 22 -d $INT_IP -s 192.168.42.3 -m state --state NEW -j ACCEPT

#smtp for all
$IPTABLES -t filter -A INPUT -p tcp -i $RDS_NIC --dport 25 -d $RDS_IP -m state --state NEW -j ACCEPT

#dns for all
$IPTABLES -t filter -A INPUT -p tcp -i $RDS_NIC --dport 53 -d $RDS_IP -m state --state NEW -j ACCEPT
$IPTABLES -t filter -A INPUT -p udp -i $RDS_NIC --dport 53 -d $RDS_IP -m state --state NEW -j ACCEPT

#http for all
$IPTABLES -t filter -A INPUT -p tcp -i $RDS_NIC --dport 80 -d $RDS_IP -m state --state NEW -j ACCEPT

#https for all
$IPTABLES -t filter -A INPUT -p tcp -i $RDS_NIC --dport 443 -d $RDS_IP -m state --state NEW -j ACCEPT

#ping and trace route anti flood
$IPTABLES -t filter -A INPUT -p icmp --icmp-type 0 -i $RDS_NIC -s any/0 -d $RDS_IP -m limit --limit 3/s -j ACCEPT
$IPTABLES -t filter -A INPUT -p icmp --icmp-type 3 -i $RDS_NIC -s any/0 -d $RDS_IP -m limit --limit 3/s -j ACCEPT
$IPTABLES -t filter -A INPUT -p icmp --icmp-type 8 -i $RDS_NIC -s any/0 -d $RDS_IP -m limit --limit 3/s -j ACCEPT
$IPTABLES -t filter -A INPUT -p icmp --icmp-type 11 -i $RDS_NIC -s any/0 -d $RDS_IP -m limit --limit 3/s -j ACCEPT
$IPTABLES -t filter -A INPUT -p icmp --icmp-type 5 -i $RDS_NIC -s any/0 -d $RDS_IP -m limit --limit 3/s -j ACCEPT

#traceroute
$IPTABLES -t filter -A INPUT -p udp -i $RDS_NIC -s any/0 -d $RDS_IP --dport 33434:33523 -j ACCEPT

#permit to all pachets from inside
$IPTABLES -t filter -A INPUT -i $INT_NIC -s $INT_LAN -m state --state NEW -j ACCEPT

#permit to all pachets to lo interface
$IPTABLES -t filter -A INPUT -i lo -m state --state NEW -j ACCEPT

#output chain
#PERMIT TO established connection
$IPTABLES -t filter -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -t filter -A OUTPUT -o lo -j ACCEPT
$IPTABLES -t filter -A OUTPUT -o $RDS_NIC -j ACCEPT
$IPTABLES -t filter -A OUTPUT -o $INT_NIC -j ACCEPT

#forward chain
$IPTABLES -t filter -A FORWARD -p tcp ! --syn -m state --state NEW -j DROP
$IPTABLES -t filter -A FORWARD -p all -m state --state INVALID -j DROP

#permit to established connection
$IPTABLES -t filter -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

#susspect ip that are used for virtual networks
$IPTABLES -t filter -A FORWARD -i $RDS_NIC -s 10.0.0.0/8 -j DROP
$IPTABLES -t filter -A FORWARD -i $RDS_NIC -s 172.16.0.0/12 -j DROP
$IPTABLES -t filter -A FORWARD -i $RDS_NIC -s 192.168.0.0/16 -j DROP

#access without restrictions (my ip)
$IPTABLES -t filter -A FORWARD -p all -s 192.168.42.3 -i $INT_NIC -m state --state NEW -j ACCEPT

#just 80 port for browsing
$IPTABLES -t filter -A FORWARD -p tcp -s 192.168.42.198 -i $INT_NIC --dport 80 -m state --state NEW -j ACCEPT

#masquarading
$IPTABLES -t nat -A POSROUTING -s $INT_LAN -o $RDS_NIC -j SNAT --to-source $RDS_IP

---

### Post by robert.ion on 2007-05-31
any idea ?

---

