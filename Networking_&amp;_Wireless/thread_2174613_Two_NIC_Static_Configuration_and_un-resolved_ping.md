---
title: "Two NIC Static Configuration and un-resolved ping"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by Hussnain_Raza on 2013-09-15
Hi,


I installed UBUNTU server 12.04 with 2 NIC named eth0 (Primary -- Static Public IP) & eth1 (Static LAN IP) to my surprise I am able to ping any domain ([www.google.com]("http://www.google.com")) or IP (8.8.8.8) over the Internet but I am unable to ping any IP on my LAN. Following is the configuration (with fake IP's) of Network Interfaces. Please help me out to get my problem solved, so I may be able to ping from eth1 interface to LAN and  from Internal LAN to eth1. furthermore please advise how the traffic will be forwarded from LAN to Internet using wth0 and eth1.

#eth0 is for Internet

auto eth0 
iface eth0 inet static
address 200.200.200.2
netmask 255.255.255.240
network 200.200.200.0
broadcast 200.200.200.15
gateway 200.200.200.1
dns-nameservers 8.8.8.8


#eth1 is for LAN

auto eth1
iface eth1 inet static
address 10.30.83.9
netmask 255.255.248.0

---

