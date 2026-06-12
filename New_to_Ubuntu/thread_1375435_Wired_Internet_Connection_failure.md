---
title: "Wired Internet Connection failure"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-01-07
So I recently re-installed Ubuntu 9.10 Karmic. I've had no real trouble connecting to wireless, but my dorm only uses wired (archaic I know). Anyway, when I plug it in, it says "Auto Etho Connected" but I can't get online. I know its not my ethernet cord because I've used it before and I have a duel boot so when I tried it on Windows 7, it connected to the internet via wired immediately. I ran ifconfig in the terminal and heres what I got


eth0      Link encap:Ethernet  HWaddr 00:23:5a:3c:05:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140520 (140.5 KB)  TX bytes:8492 (8.4 KB)
          Interrupt:29 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:00:4e:9d  
          inet addr:10.1.100.65  Bcast:10.1.101.255  Mask:255.255.254.0
          inet6 addr: fe80::224:2cff:fe00:4e9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2519615 (2.5 MB)  TX bytes:572439 (572.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-00-4E-9D-30-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000

I'm really stumped on this one. Right now I'm stuck using Windows 7 just so I can get online in my dorm, and I HATE IT! If anyone has a solution, it would be greatly appreciated

---

