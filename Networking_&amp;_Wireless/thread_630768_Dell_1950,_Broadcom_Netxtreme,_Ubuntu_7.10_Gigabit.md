---
title: "Dell 1950, Broadcom Netxtreme, Ubuntu 7.10 Gigabit Issues"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by doodah2001 on 2007-12-03
I'm running Ubuntu 7.10 (Gutsy) 64 bit server on a Dell 1950 Poweredge with Broadcom Netxtreme network drivers.  I've created an NFS share between some terrabyte storage and the servers which are also on a gigbit connection.  Everything is through a gigabit switch.  With the speeds I'm getting, it seems as if the network drivers are capped at 100Mbps.  I've tried enabling large frames (ifconfig eth0 mtu 9000) and that didn't work either as that stopped my server from being able to use the LAN altogether.  I'm pretty sure that it's the actual broadcom drivers but I was wondering if anyone else has had issues or hasn't been able to utilize the potential of the gigabit drivers.  Any thoughts on where to look to up the speed would be great.

---

