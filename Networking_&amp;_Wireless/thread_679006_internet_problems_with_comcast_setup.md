---
title: "internet problems with comcast setup"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by alloftheabove on 2008-01-26
I'm using Ubuntu 7.10, and I just had an internet modem set up by comcast.  The problem is, I have use of the internet with firefox, but add/remove programs won't reload like it should, and when I run apt-get install bluefish, it says it can't find the package.  This indicates to me that ubuntu also can't connect to the online package repos.  Here is ifconfig info:

alex@alex-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:39:AF:75  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe39:af75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:1 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43185 (42.1 KB)  TX bytes:5387 (5.2 KB)
          Interrupt:9 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by alloftheabove on 2008-01-26
BUMP

Is anyone even looking here?  I need HELP.

---

