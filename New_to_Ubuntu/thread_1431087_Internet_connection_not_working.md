---
title: "Internet connection not working"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Brasil on 2010-03-16
Hi guys, having some trouble with my internet connection. I had it working a week or so ago until I started messing around trying to get mythweb to be visible externally (and toying with vnc, ssh, etc). I have two routers with two different ISPs, it used to work with both and now works with neither! I'm using 9.04. My ubuntu box can see the router just fine, but I can't connect out with anything. The routers are both working OK and I can access the net just fine with both from my xp box. I've tried firefox, ping and wget - none of them work regardless of if I use the name or numeric address.  Obviously I've tweaked something somewhere and broken it...

brasil@brasil-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:0d:5f:20  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe0d:5f20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2678875 (2.6 MB)  TX bytes:24350840 (24.3 MB)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4306594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4306594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:476525650 (476.5 MB)  TX bytes:476525650 (476.5 MB)

---

### Post by Brasil on 2010-03-16
I think I may have botched my attempt to set up a static ip. In any event, it's all working again.

---

