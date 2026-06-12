---
title: "Post Aircard Setup, can't resolve DNS unless ON Aircard"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by gambetty on 2008-10-19
Hi All

Today, I successfully setup my sprint aircard, following the instructions on the sprint site (very well written, easy to follow, though I suggest NOT using KPPP for KDE4-- it crashes too much), on my toshiba tecra m9 laptop, Ubuntu 8.04.  This was the LAST thing I HAD to get working before complete separating myself from windows dependency.  

As a matter of fact, I am on the forums now with the card.

But thats the problem:  After setting this up, the ONLY way I can resolve addresses is WITH the card.  

If I disconnect, I can ONLY see my local network (192.168.1.x).

I can ping internet addresses by number, but cannot resolve  [www.yahoo.com](www.yahoo.com), or anything else.

Of course, from other windows or ubuntu workstations on my network, I can see everything I want.

I checked my /etc/resolv.conf file, and it reverts to my usual dns entry of 192.168.0.1 (which is right) from the sprint dns servers after dropping off the connection.

I am just not sure where else to look.........any advice?

Thanks, Seth

---

### Post by gambetty on 2008-10-20
Anyone?

Here's output from ifconfig with my wireless card on (below with off)

seth@ravel:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:b7:ae:3f:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xbfe0 Memory:ffcc0000-ffce0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100540 (98.1 KB)  TX bytes:100540 (98.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.1.123.10  P-t-P:68.28.49.69  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10024959 (9.5 MB)  TX bytes:576573 (563.0 KB)

sl0       Link encap:Serial Line IP  
          inet addr:192.168.0.1  P-t-P:192.168.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

AND OFF

eth0      Link encap:Ethernet  HWaddr 00:15:b7:ae:3f:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xbfe0 Memory:ffcc0000-ffce0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103340 (100.9 KB)  TX bytes:103340 (100.9 KB)

sl0       Link encap:Serial Line IP  
          inet addr:192.168.0.1  P-t-P:192.168.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:a2:8d:95  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fea2:8d95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68401 (66.7 KB)  TX bytes:63958 (62.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-A2-8D-95-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

