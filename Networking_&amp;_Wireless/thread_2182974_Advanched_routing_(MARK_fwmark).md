---
title: "Advanched routing (MARK fwmark)"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by iwl on 2013-10-23
Hi group,

I struggle for some days allready getting routing between 2 192.168.1.0/24 networks going with address translation.
I does not work my setup-Script:

#!/bin/sh
iptables -t mangle -F
iptables -t nat -F
ifconfig eth1 192.168.1.1 netmask 255.255.255.0 up
ifconfig eth3 192.168.1.1 netmask 255.255.255.0 up
sysctl net.ipv4.conf.eth1.rp_filter=0
sysctl net.ipv4.conf.eth3.rp_filter=0
sysctl net.ipv4.ip_forward=1
ip route flush table eth3
ip rule flush
ip rule add fwmark 1 table eth3 
ip route add to 192.168.1.0/24 dev eth3 table eth3
ip route add to 192.168.1.0/24 dev eth1
arp -i eth1 -Ds 192.168.1.10 eth1 pub
arp -i eth3 -Ds 192.168.1.2 eth3 pub
iptables -t mangle -A PREROUTING -d 192.168.1.10 -j MARK --set-mark 1
iptables -t mangle -A OUTPUT -d 192.168.1.10 -j MARK --set-mark 1
iptables -t mangle -A PREROUTING -i eth3 -j MARK --set-mark 2
iptables -t nat -A PREROUTING -d 192.168.1.10 -j DNAT --to-destination 192.168.1.5
iptables -t nat -A POSTROUTING -s 192.168.1.5 -m mark --mark 2 -j SNAT --to-source 192.168.1.10

I can't ping 192.168.1.10 (192.168.1.5 wired to eth3) from 192.168.1.2 (wired to eth1)

It sometime works when I add rule
ip rule add from 192.168.1.2 table eth3
but I need connection to 192.168.1.5 in eth1 also

---

