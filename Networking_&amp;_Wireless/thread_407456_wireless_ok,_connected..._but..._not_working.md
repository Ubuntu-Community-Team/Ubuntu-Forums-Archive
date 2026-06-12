---
title: "wireless ok, connected... but... not working?"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by IGNIZ on 2007-04-12
hi, i use feisty fawn and it works out of the box. 

but after last update my internet connection is DEAD!

i've an usr5423 dongle (it works just plugging it) and a dsl-g624T wireless router, to make it works i had to blacklist ipv6 and to change the dns manually, but it worked.

now i'm connected (iwlist says i'm connected and there are no problems) but i just can't surf the net, firefox tells me he can't find the servers... BUT i'm connected!!! :confused:

maybe is the wirelessmanager i installed with automatix? i mean, the one i can't uninstall because automatix doesn't run if he doesn't find an internet connection? -_-

---

### Post by garrido on 2007-04-12
Show us the results from iwconfig, pls.

---

### Post by Dual Cortex on 2007-04-12
Happens to me as well in every fresh install.
Type iwconfig and identify your network adapter (see if it's called eth0, or eth1, or wlan0, etc.)
Then just type dhclient [NAME]
Also, sometimes for no reason the settings you type for network don't get saved.
Type iwconfig and see if the key is there (if you use one) and the freq., ESSID is correct.
That did the job for me. Sometimes I just needed a restart. What was the last update? New kernel image/headers?

---

### Post by IGNIZ on 2007-04-12
> **Dual Cortex said:**
> Happens to me as well in every fresh install.
Type iwconfig and identify your network adapter (see if it's called eth0, or eth1, or wlan0, etc.)
Then just type dhclient [NAME]
Also, sometimes for no reason the settings you type for network don't get saved.
Type iwconfig and see if the key is there (if you use one) and the freq., ESSID is correct.
That did the job for me. Sometimes I just needed a restart. What was the last update? New kernel image/headers?

oh yes! it worked! 
but i have to do it at every restart -_-

---

