---
title: "2 ISP no nat"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by ajoian on 2007-05-30
I have this problem :


internet -------- ISP1 ---- | router hw (nat) | ---- (private ip) ------ |workstation
|
|
|
|
---ISP2 --------- (public ip) -------------------------- |same workstation

Explanation:

I have an workstation with 2 internet links like so:
- eth0 is the NIC connected to the router network and I receive the private ip (192.168.0.XXX)
- eth1 is the other NIC linked directly to the provider and I receive a public ip (86.106.xxx.xxx)

After prolonged studies of chapter 4.2.1 of lartc:
- I've created 2 routing tables (T1,T2) for each provider;
- I've chose the preferred default route thru the hardware router and the private ip;
- i did the load balancing with nexthop and weight 4 for ISP2;

The problem is that I don't have access thru ISP1. And i have no idea way i cant use BOTH of my connections at the same time.
This is the config (the 2 tables T1 and T2 are already created):
Code:
IF1="eth0"
IF2="eth1"
IP1="192.168.0.xxx"
IP2="86.106.xxx.xxx"

P1="192.168.0.1"
P2="86.106.xxx.1"

P1_NET="192.168.0.0/24"
P2_NET="86.106.xxx.0/24"

ip route add $P1_NET dev $IF1 src $IP1 table T1
ip route add default via $P1 table T1
ip route add $P2_NET dev $IF2 src $IP2 table T2
ip route add default via $P2 table T2

ip route add $P1_NET dev $IF1 src $IP1
ip route add $P2_NET dev $IF2 src $IP2

ip route add default via $P1
ip rule add from $IP1 table T1
ip rule add from $IP2 table T2

ip route add default scope global nexthop via $P1 dev $IF1 weight 1 nexthop via $P2 dev $IF2 weight 10


ip route show command output is this :
Code:

# ip route show
192.168.0.0/24 dev eth0 proto kernel scope link src 192.168.0.xxx
86.106.xxx.0/24 dev eth1 proto kernel scope link src 86.106.xxx.xxx
172.16.205.0/24 dev vmnet1 proto kernel scope link src 172.16.205.1
172.16.173.0/24 dev vmnet8 proto kernel scope link src 172.16.173.1
169.254.0.0/16 dev eth1 scope link
default via 86.106.xxx.1 dev eth1


Thank you in advance. I need a gurus opinion!!!

---

