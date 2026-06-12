---
title: "can't make &quot;outside&quot; connection"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by caspdj on 2007-06-13
Hello I have an xetrasys xn-2433g wireless card on my laptop.  i used ndiswrapper to install the drivers. I disabled ipv6 by editing my /etc/modprobe.d/aliases and setting to off the appropriate line. now i can connect to my router's config   192.168.etc.etc but i can't connect to any "outside" site. not google not yahoo etc.  i have to use my windows box for such any ideas?


edit:  here is the iwconfig output:  Link encap:Ethernet  HWaddr 00:E0:98:BF:97:89  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:537 errors:1 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28263 (27.6 KiB)  TX bytes:5103 (4.9 KiB)
          Interrupt:10

---

### Post by jmbargar on 2007-06-13
It seems you have not configured the apropiate dns. Do you get the google website if you put [http://64.233.183.147/](http://64.233.183.147/) in your web browser? If it is try to put this in /etc/resolv.conf

80.58.61.250
80.58.61.254

Best regards

J. Manuel Barrios

---

### Post by caspdj on 2007-06-13
thanks much that worked

---

