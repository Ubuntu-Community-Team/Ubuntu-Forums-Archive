---
title: "Packets redirect help?"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by najajj on 2008-08-14
Hello all,

I have a L2TP tunnel setup on Ubuntu Server, all tunnnel traffic is in tun0. 

What I want to do is forward all tunnel traffic from tun0 to 172.16.1.3, meaning using 172.16.1.3 as tun0's gateway. 172.16.1.3 is reachable from eth0. 

In the meantime, the source address and destination address should keep the same. I don't do NAT on packets.

I tried several route and iptables but I still don't get it. Could someone give me some advices?

Thanks a lot

---

