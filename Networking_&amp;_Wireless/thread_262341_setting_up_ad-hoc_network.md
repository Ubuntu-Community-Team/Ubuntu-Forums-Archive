---
title: "setting up ad-hoc network"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by weizilla on 2006-09-21
I'm trying to set up an ad-hoc network between two computers, but for some reason it's not working.

So far I run this on both computers as root with different ips at the last step:
iwconfig [wireless device] essid taco
iwconfig [wireless device] mode ad-hoc
iwconfig [wireless device] channel 7
ifconfig [wireless device] 192.168.0.1

However, after this, neither computer can ping each other. Also, sometimes one computer can see the other computer's broadcast and sometimes it doesn't. 
Both of these computers can connect to a normal wireless access point fine so I don't know what the problem maybe. Is there a command that I may be missing or something?
Any help is appreciated.

---

### Post by spd106 on 2006-09-22
Check that the drivers for your cards support ad-hoc mode. I know some don't have this function or that you have to do it some other way than just iwconfig mode adhoc. For example with madwifi-ng (ath0) you have to create a new interface in adhoc mode. Ndiswrapper drivers can also be a bit hit and miss. My Broadcom card doesn't seem to work in adhoc mode, but it's fine in managed mode.

---

