---
title: "Random, unusably-high latency on wifi"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by wmdiem on 2008-08-21
I have been having random network issues with my ubuntu laptop. After lots of troubleshooting I've realised that my ping time (to the router) is going from its typical 5-10ms up to around 15000ms or more. Basically everything including DNS and DHCP, and sometimes even the pings, times out and the net effect is that I have no network connection. 
I've tried removing and restarting ath_pci (sudo modprobe -r ath_pci) and it has no effect. No other computers on the network are having this problem. Restarting the computer seems to fix it, at least for a minute. 
Does anyone know what causes this? Is there some other way to force the wificard down without restarting the computer? One of the main reasons I switched to ubuntu from vista was to increase uptime, so having to unexpectedly shut down my computer when I'm in the middle of things just to get networking back up is really irking me. 
Thanks a lot for any help.

---

### Post by wmdiem on 2008-08-21
Does anyone have any idea what will cause latency in a wifi connection other than a weak signal or network congestion? 
I'm really lost on troubleshooting this. 
Any help would really be great.

---

### Post by wmdiem on 2008-08-21
More trouble shooting:

First the settup: Gateway (192.168.0.1) >ethernet> Router1 (192.168.1.1) >wifi> Router2 (192.168.10.1) >ethernet> two workstations (XP and ubuntu)

From the ubuntu machine: 
"ping -I eth1 www.google.com" works fine
"ping -I eth1 192.168.1.1" gets no replies (in the first 10 sec)
"ping -I wlan1 www.google.com" gets no replies (in the first 10 sec)
"ping -I wlan1 192.168.1.1" gets no replies (in the first 10 sec)
"ping -I eth1 192.168.10.1" works (less then 1ms)

From the XP machine (over ethernet) both the google and the router reply quickly (200ms for google 2ms for Router1). 

I'm really confused at this point.

---

