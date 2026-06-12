---
title: "wireless woes"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by GolfGeek on 2006-12-03
It seems the only way I can get my laptop (compaq presario 2100) to connect is via wire. I recently upgraded to edgy (clean install) with the hope that wpa encryption was functional. 

When I go to networking it sees both wired and wireless connections. I entered a new ssid for the router (netgear wpn824) today. When I right click eth1 and click Properties I enut nothingter the essid. It asks for a network password (but no  reference to WEP or WPA). I have tried entering the router password and the wpa passphrase but nothing has any eH to show the ssid. I have bever gotten to the point of being asked for a pasphrase. I also installed network manager using sudo apt-get install network-manager and it installed without error. At thi point I have no idea where to go next. I would love to get this running withour cat5 cables across the kitchen floor!!

Just as a side opint, I went into the router settings this morning, changed the ssid, disabled broadcast and reentered a new passphrase. When I was done, my girlfriend's xp laptop indicated a new wireless connection was available. Went into it, changed the passphrase and was done. As much as I dislike windows, it works. Any direction is appreciated.

---

### Post by GolfGeek on 2006-12-03
After reading another thread I ran iwconfig and got the following

eth0      Link encap:Ethernet  HWaddr 00:0F:20:20:05:82  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe20:582/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1940448 (1.8 MiB)  TX bytes:286943 (280.2 KiB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

