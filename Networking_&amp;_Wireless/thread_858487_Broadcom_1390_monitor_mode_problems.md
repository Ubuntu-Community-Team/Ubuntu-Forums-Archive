---
title: "Broadcom 1390 monitor mode problems"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Pensive Koala on 2008-07-13
I have the...rather storied Broadcom 1390 wireless card, as do so many others.  Ubuntu correctly configured it with b43-fwcutter during install, and I have reinstalled it since.  Everything I have heard and read tells me that monitor mode should work perfectly well for me.  However, when I run airmon-ng, I get:
```
wlan0                   iwl3945 - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

                                (monitor mode enabled on mon0)
```
Does anyone know why this is happening, and how I can stop it?

---

