---
title: "Cry a river, build a bridge and get over over it....(Help, please?)"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2007-06-05
Ok,

Not sure about anyone else but Bridging in Linux is harder than appreciating what a teacher is trying to do for you (Kidding lol). Anyway I followed the tut [here](http://linux-net.osdl.org/index.php/Bridge) to no avail and to be honest it doesn't make much sense. Each time I try I lose my internet connection to my computer and my bridge has gone no-where, and each time I have to boot in recovery mode to reset the faulty new settings. 

My ifconfig read out:
[PHP]eth0      Link encap:Ethernet  HWaddr 00:13:8F:81:27:EB  
          inet6 addr: fe80::213:8fff:fe81:27eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47040 (45.9 KiB)  TX bytes:468 (468.0 b)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra1       Link encap:Ethernet  HWaddr 00:17:9A:C9:24:FC  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fec9:24fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2832 errors:41 dropped:41 overruns:0 carrier:0
          collisions:588 txqueuelen:1000 
          RX bytes:3379807 (3.2 MiB)  TX bytes:495079 (483.4 KiB)
          Interrupt:19 
[/PHP]

So can anybody craft a magic way that not only will my internet work but it will run happily with a 360 running through my wireless card?

**Situation:**

I am running Linux feisty Fawn 7.04. I am accessing the internet through my steady wireless connection. On Windows I have my 360 bridged up to by wireless connection and they both run well, but I wanna have my connection routed through my Linux partition instead, I already have my 360 in the router's DMZ and port forwarding enabled for it. 

**What I am asking?**

A quick tut on how I can resolve these issues and bridge the two super powers :-|

---

