---
title: "Connectivity problems with 2 NICs"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by noharm on 2007-11-06
By searching the forums I didn't find a solution that fits me.
I've two NICs that connect to 2 entirely different networks.
While connecting to the 192.x.x.x works perfect, 172.x.x.x doesn't work most of the time
No firewall rules are active, ip_foward is 1, network manager is disabled to avoid any interference

My suspicion is that the 172.18.20.0 0.0.0.0 gateway causes the problem, however that is added automatically.

I would really appreciate if someone could give me the golden hint by looking at the follwing configuration ...

/etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.181.10
netmask 255.255.0.0
gateway 192.168.181.2

auto eth0

iface eth1 inet static
address 172.18.20.118
netmask 255.255.255.0
up route add -host 172.18.20.1 dev eth1
up route add -net 172.18.20.0 gw 172.18.20.1 netmask 255.255.255.0 dev eth1
down route del -host 172.18.20.1 dev eth1
down route del -net 172.18.20.0 gw 172.18.20.1 netmask 255.255.255.0 dev eth1
auto eth1

routing table

Destination Gateway Genmask Flags Metric Ref Use Iface
172.18.20.1 0.0.0.0 255.255.255.255 UH 0 0 0 eth1
172.18.20.0 172.18.20.1 255.255.255.0 UG 0 0 0 eth1
172.18.20.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth1
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.181.2 0.0.0.0 UG 0 0 0 eth0

---

### Post by spd106 on 2007-11-06
What are you trying to achieve? What do you mean by doesn't work most of the time?

I don't think you need to add the extra routes, it is automatically added when you add the interface address details.

---

### Post by noharm on 2007-11-06
What I would like to achieve is the following: when being connected to the machine, I would like to be able to connect to hosts like 192.168.181.12, 192.168.181.13 or the Internet (this works fine always). However I would also like to be able to connect to hosts like 172.18.20.104, 172.18.20.114, etc., this only works randomly (using a different notebook using the cable of the 172.18.20.X segment works fine and without problems).

In similar setups in previous occasions I was using SuSE (and faced no problems using Yast for the setup)

---

### Post by mips on 2007-11-06
Hmm, I've done this many times and never had to add or remove any routes. It just works.

The only difference to your config is I would specify the eth1 gateway address as the ip address of eth0.

---

