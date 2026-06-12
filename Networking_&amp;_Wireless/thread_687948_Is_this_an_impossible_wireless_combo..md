---
title: "Is this an impossible wireless combo."
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by OpEdMunkey on 2008-02-04
I've tried many of the posts and I think I may have stumbled upon an unbeatable combination of hardware and software dedicated to not working. Your thoughts are appreciated.

Xubuntu 6.06
Broadcom 4318 Rev2 PCMCIA wireless adapter..of course - the USRobitics MAXg 5411 version
Compaq 1700T PIII 512M, 850hz

US Robotics Router 5461
WPA2 and WPA
TKIP and AES
NOT broadcasting SSID
MAC filtering enabled

Known good:
wireless card connects  when running XP
wired connection works great for Xubuntu

Be helpful of course if I knew what I were doing. Do I need an entry in /etc/network/interface(s) as well as an entry in wpa_supplicant or are they mutually exclusive? If I weren't so lazy I'd reconfigure the AP with WEP and turn broadcasting on, but I've been saving that as sort of a last resort. 

Started working on this when Dapper was released. Figured it's about time I got it working.

---

