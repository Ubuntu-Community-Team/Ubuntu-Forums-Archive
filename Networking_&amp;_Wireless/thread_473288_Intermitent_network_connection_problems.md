---
title: "Intermitent network connection problems"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by ninja1 on 2007-06-13
Hi

I'm experiencing random disconnections on my internet DSL connection. I don't know what is going on because I haven't changed any settings since I installed Ubuntu Feisty.  Here is a copy of my ifconfig output from terminal.  I also saw MULTICAST and weird ip address in my Routing table inside Network Tools. Please help if you can. Thanks


ninja@NINJA--PC:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:19:5B:3D:08:53  
          inet addr:72.253.98.87  Bcast:72.253.111.255  Mask:255.255.240.0
          inet6 addr: fe80::219:5bff:fe3d:853/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18233805 (17.3 MiB)  TX bytes:3032775 (2.8 MiB)
          Interrupt:19 Base address:0xd800 

ninja@NINJA--PC:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:5b:3d:08:53
Sending on   LPF/eth0/00:19:5b:3d:08:53
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 72.253.96.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 72.253.96.1
bound to 72.253.98.87 -- renewal in 65805 seconds.

---

