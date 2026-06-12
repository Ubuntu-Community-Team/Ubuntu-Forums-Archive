---
title: "Connected to wireless network but not able to use internet"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by jimjesus on 2008-05-04
I had posted here earlier about wicd not being able to see my wireless networks and I fixed it with the fwcutter driver so I can now connect to a wireless network and have the connected symbol in my tray, but when I try and use firefox or pidgin, they can't connect. Does anyone know what causes this and how to remedy it?

Edit: I can still connect to the internet through wired connections on said laptop.

---

### Post by superprash2003 on 2008-05-05
please post output of ifconfig (in the terminal).. also see if you are able to ping your router or not

---

### Post by jimjesus on 2008-05-05
ifconfig outputs:

```
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:80:c3:f7  
          inet addr:192.168.0.135  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe80:c3f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2901810 (2.7 MB)  TX bytes:462552 (451.7 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105921 (103.4 KB)  TX bytes:105921 (103.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:46:e7:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2322364 (2.2 MB)  TX bytes:60175 (58.7 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:90:4b:46:e7:a8  
          inet addr:169.254.8.221  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-46-E7-A8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I can now connect to the internet and I can access my router, however I couldn't this morning, so it seems strange that it works now but didn't for the previous two days when all the other wireless computers worked.

EDIT: So now I can't connect to the internet with wireless and I can't access my router through that computer while on wireless. It works on occasion, but I'll have to hit refresh about 6 times before a page will load.

---

### Post by stockdam on 2008-05-05
I've had problems with my wireless connection also. I've only been using Ubuntu for a couple of days. Sometimes the wireless connection just doesn't work and I have to enter the WPA key again or change the DNS settings......I'll have to look into it more to find out what is happening. Once connected it works fine but for some reason it doesn't always connect even though the settings are saved correctly.

---

### Post by superprash2003 on 2008-05-06
changing your dns servers could help [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

