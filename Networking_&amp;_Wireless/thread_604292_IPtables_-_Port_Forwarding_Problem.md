---
title: "IPtables - Port Forwarding Problem"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by chrisdavid_175 on 2007-11-06
hey everybody... i've been having trouble trying to configure iptables to properly forward a port to ssh but still drop all other packets. here is my configuration script:

code:

> 
#!/bin/bash
#script to setup this box as a router

#
#identify variables
#
INET_INT="eth1"
LAN_IP="192.168.54.1"
LAN_INT="eth0"
LO_IP="127.0.0.1"
LO_INT="lo"
IPTABLES="/sbin/iptables"
MODPROBE="/sbin/modprobe"
DEPMOD="/sbin/depmod"
SSH="10022"
WWW="10080"

#
#load modules
#
$DEPMOD -a
$MODPROBE ip_tables
$MODPROBE ip_conntrack
$MODPROBE iptable_filter
$MODPROBE iptable_mangle
$MODPROBE iptable_nat
$MODPROBE ipt_LOG
$MODPROBE ipt_limit
$MODPROBE ipt_state

#
#enable ip forwarding
#
echo "1" > /proc/sys/net/ipv4/ip_forward

#
#flush all rules in filter and nat tables
#
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F

#
#configure rules for filters and tables
#

#
#log everything else
#
$IPTABLES -A INPUT -i $INET_INT -j LOG --log-ip-options

#
#configure rules to accept packets
#
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A INPUT -p tcp -i $INET_INT --dport $SSH -j ACCEPT
$IPTABLES -A INPUT -p tcp -i $INET_INT --dport $WWW -j ACCEPT

#
#configure port forwarding
#
$IPTABLES -t nat -A PREROUTING -p tcp -i $INET_INT --dport $SSH -j DNAT --to $LAN_IP:22

#
#enable nat for internal network
#
$IPTABLES -t nat -A POSTROUTING -o $INET_INT -j MASQUERADE

#
#drop everything else on external interface
#
$IPTABLES -A INPUT -i $INET_INT -j DROP




i can ssh from the internet through 10022 when i don't use the DROP rule and i can also ssh through 10022 when i use the drop rule but i also have to ACCEPT port 22. any help would be greatly appreciated.

---

