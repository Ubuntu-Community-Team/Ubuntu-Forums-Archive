---
title: "i need a solution for my wpa problem"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by PixelCloud on 2006-08-23
I pretty much have everyone working on my new ubuntu install except for wpa support (i think i have it installed i just have NO idea how to make it work).

I'm currently using wifi radar and ndiswrapper for my wireless card and its working well for unsecure and WEP networks. I've also installed wpa_supplicant.

I've read that ndiswrapper and network-manager-gnome do not work together. 

How can i get wifi radar to support my wpa ap? (aka what do i put in the place for WPA driver)

---

### Post by ddales on 2006-08-29
Same problem here:

Intel 32bit Dapper 6.06.1
ndiswrapper 1.8 from repository
smc2802w EU V2 XP driver

Works fine plane but not with WEP

---

### Post by 13east on 2006-08-29
i seem to have the same prblm was other people here: i can't connect to any wireless connection that has any sort of wep encryption on it (64 or 128bit)

after many tries i finally got the ndis wrapper working for my wifi card ([http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ndis+wrapper](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ndis+wrapper) w/ a broadcom bcm4306 on a pavillion zv5000z)
but can't seem to get online using with network manager or wifi radar when either the wep encryption is enabled or when mac filtering is enabled.  so for immediate resolution, i turned off all security feature.  does anyone know how to fix this bug? any help would be much appreciated.

p.s. as a side note = with mac filtering enabled, my wifi card doesn't seem to be able to detect any wifi connection in ubuntu or windows (i'm wondering if its just a built in defect).  does anyone know how to solve this at least in linux os?

thank you.

---

