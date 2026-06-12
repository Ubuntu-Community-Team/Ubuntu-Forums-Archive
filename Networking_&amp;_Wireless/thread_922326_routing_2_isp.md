---
title: "routing 2 isp"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by boiko_tri on 2008-09-17
Hi sory for my english but i have problem
I need to route 2 isp 1 isp have ip 192.168.1.2  2 isp is 10.6.100.160  and i using local network 172.16.1.1/32
 i writed the script but doesnt work 
#!/bin/bash
route del default
route del default

ip route add 10.6.0.0/16 dev eth0 src 10.6.160.100 table T1
ip route add default via 10.6.0.1 table T1

ip route add 192.168.1.0/24 dev eth1 src 192.168.1.2 table T2
ip route add default via 192.168.1.1 table T2

ip route add 10.6.0.0/16 dev eth0 src 10.6.160.100
ip route add 192.168.1.0/24 dev eth1 src 192.168.1.2

ip route add default via 192.168.1.1

ip rule add from 10.6.160.100 table T1
ip rule add from 192.168.1.2 table T2

ip route add 172.16.0.0/16 dev eth2 table T2
ip route add 192.168.2.0/24 dev eth4 table T2
ip route add 192.168.11.0/24 dev eth4 table T2

ip route add 172.16.0.0/16 dev eth2 table T1
ip route add 192.168.2.0/24 dev eth4 table T1
ip route add 192.168.11.0/24 dev eth4 table T1


where is a problem ?
2 isp using vpn 10.6.160.100

---

