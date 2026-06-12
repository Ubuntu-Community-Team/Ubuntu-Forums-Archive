---
title: "Wired Connection"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by Macrosystems on 2008-11-30
I had to switch from my notebook to desktop this weekend, and to my surprise, I no longer can access the internet. There is no wireless card on the machine, so I have to type this from another machine. I've got the desktop hooked up exactly the same way as I had my notebook, but it doesn't work. The network applet shows theres a connection, but I can't view any webpages, ssh or anything. Here is the output of ifconfig:> eth1      Link encap:Ethernet  HWaddr 00:08:a1:0a:2e:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64 (64.0 B)  TX bytes:6423 (6.2 KB)
          Interrupt:20 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:0d:60:23:b5:e4  
          inet6 addr: fe80::20d:60ff:fe23:b5e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3172 (3.0 KB)  TX bytes:5553 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140248 (136.9 KB)  TX bytes:140248 (136.9 KB)


Any help or advice would be AWESOME.

---

