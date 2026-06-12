---
title: "wifi randomly disconnects"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by rumca.js on 2010-05-04
Recently I updated system to lucid lynx.
Now my wifi randomly disconnects. I do not know with may be cause of that.

What I have done:
- set in power managment laptop lid action as blank screen.
- set in screensaver preferences "Regard the computer as idle after" 59minutes (max is 2 hours)
- unset Lock screen when screen saver is active

I not know what I may do know. Since I cannot predict when connection will be broken.
Also why does the connection not reconnects? It hangs on the dialog box with wep key input (but the key is present in the input box) - so wtf?

lspci output:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:8a:45:2a  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17703000 (17.7 MB)  TX bytes:690966 (690.9 KB)

I configured connection manually so I would have static ip.

---

