---
title: "I want to have wired AND wireless internet shared with my WIRELESS router, help!"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by s3a on 2008-06-13
My isp guy had problems using Ubuntu and Xubuntu to set up my wired router and when he used windows xp on his laptop, it worked, so I don't know if something happened there but the next time he came, he typed 192.168.0.1 (or 192.168.1.1). I now have a d-link wired router sharing my internet perfectly however, I got a wireless router and I want to no how I can set it up so that it shares internet with a wire to my comp (so I can get the full speed) without needing a password and I want to give internet to my mom's comp as well as my laptop wirelessly with WPA. When I connect the wireless router and type 192.168.0.1 or 192.168.1.1, firefox (and dillo) both say they cant connect (I also tried with the wired router and now for some reason, I get the same problem).

When I connect the wireless router to the ethernet port on my laptop, and type ifconfig I get:

deniz@deniz-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:39:62:E0:A2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4985224 (4.7 MiB)  TX bytes:550383 (537.4 KiB)

eth1:avah Link encap:Ethernet  HWaddr 00:00:39:62:E0:A2  
          inet addr:169.254.8.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9348 (9.1 KiB)  TX bytes:9348 (9.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:8B:97:3C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:108 (108.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-95-8B-97-3C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

deniz@deniz-desktop:~$

so...what do I do? I really would like to get this wireless router up and running because also using a phone cable extension is slowing my internet A LOT.

---

### Post by ModelM on 2008-06-14
You only need one router on the network and, indeed, it takes some pretty fancy footwork to have two routers on a network.

I'm sure what you want to do is to use the new wireless router as a wireless access point in order to add wireless access to the network. That way computers could connect to the network with an ethernet cable, or wireless, and have access to each other & the internet.

This is possible and, in fact, that's the setup I have here at my home.

To begin, disconnect the wireless router & set it aside. Now get the network setup & running just as it was the day before you bought the wireless router. We want to add wireless to a working network rather than troubleshoot more than one thing.

And, tell us what brand/model wireless router you have.

---

