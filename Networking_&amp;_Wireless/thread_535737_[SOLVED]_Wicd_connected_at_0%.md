---
title: "[SOLVED] Wicd connected at 0%"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by tiachopvutru on 2007-08-26
The first time I used Wicd, I was able to connect wirelessly to the router just fine. After I rebooted, however, it stopped working... When I set a Static IP, it's able to connect at 0%, otherwise, it stucks at "Obtaining IP Address" and won't connect... Neither would let me access the Internet, though. The router is WEP encryption, and although it's far away (since it's not mine, it's someone else's who I got permission from to access, but that's only thing I can do), connecting wasn't a problem when I used to use Windows XP. Wicd detects the essid, but that's it.

The computer I'm trying to figure out how to access to router is an old PC with Xubuntu 7.04 installed. And the wireless device is WG111T


EDIT:
Nevermind, I set a Static IP Address and in Preference, set wext instead of ndiswrapper for WPA Supplicant Driver and now it works...

---

