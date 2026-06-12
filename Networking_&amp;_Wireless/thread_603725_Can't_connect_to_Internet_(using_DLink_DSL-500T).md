---
title: "Can't connect to Internet (using DLink DSL-500T)"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by MrQuangnd on 2007-11-05
I tried check my PC about network card, ethernet and read many topics what have the same problem(but I can't find the answer)...before put this topic here:

I had messages following:

> 
**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:02:44:B2:0B:D3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:feb2:bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4957 (4.8 KB)  TX bytes:14495 (14.1 KB)
          Interrupt:17 Base address:0xb800 

 **sudo dhclient**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:44:b2:0b:d3
Sending on   LPF/eth0/00:02:44:b2:0b:d3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 1596 seconds.

** lspci | grep -i ether**
02:03.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)


I must check more anything now?

I'm using Ubuntu 7.10 and I try to manual network as Automatic Configuration DHCP (Wired Connection). 
Stop a little...I have some strangle things...After I ping a address (ping [www.ubuntu.com),I](www.ubuntu.com),I) can connect to this website but the connection was not finish (not load entire site) :(

help me... :(

---

