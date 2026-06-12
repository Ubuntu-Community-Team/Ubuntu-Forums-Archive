---
title: "WAP Problem (minor) using WAP_Supplicant"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by Stelmate on 2005-11-08
Okay here my delima,
I'm trying to switch over to WAP and wapsupplicant actually works for me but 
not on bootup.  I used the option B: (last option on [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto))
and before I had my wifi card automatically connecting to the AP on boot but now it tries but not with wapsupplicant I have to do a 
ifdown wlan0
wpa_supplicant -B -w -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper
ifup wlan0

Can anyone point me in the right direction, I really want this to work at boot.

Thanks,
Stelmate

---

