---
title: "Erratic behaviour on Asus laptop - sometimes no connect..."
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by blackSP on 2008-06-23
Although 8.04 gnome works perfect on my Asus F8P laptop sometimes it won't connect to the web. I've got a wireless set-up.

After 10 to 20 seconds or so it asks for the WPA key which I then have to enter 2 or 3 times before it connects. After which it works flawless.

Actually, 9 out of 10 times it works flawless, it's that one time that bugs me.

Anybody recognizes this?

ifconfig -a gives:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1800 (1.7 KB)  TX bytes:1800 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:44:52:a7  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1220916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1055934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1142581666 (1.0 GB)  TX bytes:294932302 (281.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-44-52-A7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Thanks!

---

### Post by blackSP on 2008-06-24
The problem is getting worse, now 1 out of 2 times when switching the laptop on I have to enter the WPA code.

Is there any way to fix this?

---

### Post by blackSP on 2008-06-25
bump

---

### Post by blackSP on 2008-06-26
bump-bump

---

### Post by blackSP on 2008-06-26
[LEFT]Thanks everybody for being so helpful.

Luckily, after a few days of trying, I fixed the problem. I made good notes so I won't have to ask anybodies help next time.[/LEFT]

---

