---
title: "Cannot connect to internet Ubuntu 8.04"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by babelproofreader on 2008-11-18
I have two Ubuntu boxes both with Ubuntu 8.04 on them, but one cannot connect to the internet through the same wired connection. For the one that works ifconfig gives

eth0      Link encap:Ethernet  HWaddr 00:16:e6:52:3a:c5  
          inet addr:87.250.172.31  Bcast:87.250.172.255    Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe52:3ac5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13619625 (12.9 MB)  TX bytes:2438671 (2.3 MB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64200 (62.6 KB)  TX bytes:64200 (62.6 KB)

and the content of /etc/network/interfaces is

auto lo
iface lo inet loopback

whilst for the one that won't connect ifconfig gives

eth0      Link encap:Ethernet  HWaddr 00:0b:6a:ec:11:c5  
          inet6 addr: fe80::20b:e6ff:feec:11c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:516597 (504.4 KB)  TX bytes:42339 (41.3 KB)
          Interrupt:18 Base address:0xcd00 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:6a:ec:11:c5  
          inet6 addr:169.254.7.193 Bcast:169.254.255.255 Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xcd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69938 (68.2 KB)  TX bytes:69938 (68.2 KB)

and the contents of /etc/network/interfaces is

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

In all other respects the network settings are exactly the same in admin-network, admin-network tools and preferences-network proxy for both computers with regard to IP addresses, DNS servers etc so I don't really understand why I am having problems connecting one of the computers. Any help would be greatly appreciated.

---

### Post by superprash2003 on 2008-11-18
how do you connect to the internet?? via a dialer in windows xp?? do you use pppoeconf in ubuntu?

---

### Post by Iowan on 2008-11-18
Depending on how you connect to internet (that address doesn't look like a "normal" router-DHCP-assigned address), some modems "lock onto" a MAC address and must be reset (power cycled) to recognize a different MAC.  If you reset the modem with the second one attached, it might work - but the first might not be able to connect without (again) resetting the modem. If that happens, you might consider a router as a buffer.

---

### Post by babelproofreader on 2008-11-20
I do not connect to the internet via a modem or router; there is an internet cable which I plug directly into my on-board ethernet card.

---

