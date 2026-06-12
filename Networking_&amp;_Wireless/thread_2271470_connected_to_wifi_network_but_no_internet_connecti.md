---
title: "connected to wifi network but no internet connection"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by viva2 on 2015-03-30
hi, so I've had ubuntu along with win8,1 for a while but I haven't used it for some time. I logged in again and updated from 12.0 to 14.04 and there my problems began. I seem to be able to connect to the wireless network but I have no Internet connection. I tried some solutions posted here before but none worked really (am not very tech savvy). if you could shed some light on what I could try I would be very grateful!

---

### Post by rigged 00 on 2015-03-31
Hi
Please post the output of each "cat /etc/network/interfaces" + "nm-tool"  + "iwconfig" + "ifconfig" + "cat /etc/resolv.conf" + "ip route".

Also out of interest are you able to ping the gateway/router on it's local IP when connected to the WiFi

---

