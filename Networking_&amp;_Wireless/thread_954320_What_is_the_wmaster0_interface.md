---
title: "What is the wmaster0 interface?"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Deeta on 2008-10-21
Hiya all :)

I just upgraded to intrepid and found a new interface in my ifconfig.

wmaster0 to be exact.
Its specifications look pretty much like unspecified garbage...

Anyone got a clue why it is listed and what purpose it has? (or whether is is some kinda of bug?)

```

diddl@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:e2:41:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27280 (27.2 KB)  TX bytes:27280 (27.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:6b:63:05:b3  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe63:5b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82695951 (82.6 MB)  TX bytes:7700630 (7.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-6B-63-05-B3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thanks so much for your help :)

Deeta

---

### Post by DFlame on 2008-10-21
Some info here: [http://ubuntuforums.org/showthread.php?t=697807](http://ubuntuforums.org/showthread.php?t=697807)

Not entirely sure myself though.

DFlame

---

### Post by meditatingfrog on 2009-05-07
I upgraded to Jaunty Jackalope.  I have the same interface, did notice that the HW address includes the wlan0 hw address...

---

