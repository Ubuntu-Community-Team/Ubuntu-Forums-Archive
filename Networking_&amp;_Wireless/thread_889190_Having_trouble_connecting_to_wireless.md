---
title: "Having trouble connecting to wireless"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by neighteight on 2008-08-13
I am able to see all local signals and connect to them but when I open Mozilla it appears I don't have a signal. Any thoughts?

---

### Post by Ryan450 on 2008-08-14
Going to need a lot more information on this to figure out whats really wrong here.

Connect to the wireless network as you normally would, then open up a terminal run these commands.

ifconfig -a

iwconfig -a

reply back with the output of those commands and we'll see what kind of state your network card really is in.

---

### Post by neighteight on 2008-08-15
n8@n8-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:bf:75:2a  
          inet addr:24.145.128.248  Bcast:255.255.255.255  Mask:255.255.255.192
          inet6 addr: fe80::2e0:b8ff:febf:752a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:467070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223838234 (213.4 MB)  TX bytes:13158816 (12.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77400 (75.5 KB)  TX bytes:77400 (75.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:13:3e:45  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11158 (10.8 KB)  TX bytes:52868 (51.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-13-3E-45-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

n8@n8-laptop:~$ 
n8@n8-laptop:~$ iwconfig -a
-a        No such device

n8@n8-laptop:~$

---

