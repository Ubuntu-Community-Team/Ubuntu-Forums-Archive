---
title: "Network connection to and from Ubuntu Server 15.10 on Hyper-V is down"
date: 2016-02-24
forum: Networking &amp; Wireless
---

### Post by Ppaa on 2016-02-24
Hi!

I have home network with fttx-router (192.168.1.1) and desktop (win10 with Hyper-V host) with working Ubuntu server 15.10 (passat) until 02/20/2016. Then, suddenly, he ceased to be available from the internal and external network.
 New test virtual guest server 14.04.04 (samum) is available from internal and external network.
Network parameters (sorry for screenshots)
 Passat (not connected)
[ATTACH=CONFIG]267472[/ATTACH]
Samum (all ok)
[ATTACH=CONFIG]267473[/ATTACH]

Please help me, how to solve this problem. Web-server with my site on passat is down :(

---

### Post by Ppaa on 2016-02-24
Uncheck Vlan ID in Hyper-V and problem solved.

---

