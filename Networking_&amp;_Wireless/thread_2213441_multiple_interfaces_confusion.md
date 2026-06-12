---
title: "multiple interfaces confusion"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by viktor.rebeja on 2014-03-26
Hello everyone, 
I would like to ask how Ubuntu choose from multiple interface communication when is more than one. Initially the system creates* ppp0* connection with *wvdial*. After I realize a new connection to an Access Point but who doesn't have acces to the net. It happens sometimes that I don't have access to both network directions and the system is confused what to use. What configuration I need to set up to have access to the net over *ppp0* and *wlan0*  to be available locally avoiding system confusion on what to use Thank you very much.

[COLOR=#000000][FONT=Verdana]This is the file from /etc/network/interfaces 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**Cod:**

> auto wlan0
iface wlan0 inet dhcp

auto ppp0
iface ppp0 inet wvdial

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This is the command to connect to Acces Point after login
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**Cod:**

> iwconfig wlan0 essid ZTE

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]And this is the network state given by ifconfig[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**Cod:**

> ppp0      Link encapoint-to-Point Protocol  
          inet addrx.42.xx.210  P-t-Px.xx.64.xx  Mask:255.xx.255.xx
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:8790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5546942 (5.5 MB)  TX bytes:1211674 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:9e:de:d8  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fe9e:ded8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1720823 (1.7 MB)  TX bytes:309323 (309.3 KB)

[/FONT][/COLOR]

---

### Post by TheFu on 2014-03-26
It does it the same way every other OS does, but the metric value in the routing table.
**route** will display it.
Having 2 "default routes" with the same metric will cause all sorts of issues.

---

