---
title: "Need to know if my wireless card could work on ubuntu"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by awperk on 2007-02-28
I have a decent desktop that i don't use much because i mostly use my laptop. My plan is to install ubuntu on the desktop but i want to make sure that my wireless will be able to work so i can do some updates and download some apps. Well my card is a Siemens SpeedStream 1024 wireless pci card. I read the sticky about compatible cards but siemens wireless has changed names a few times and i couldn't find any answers on the compatibility of my card. If my card is compatible, how would i go about getting the correct drivers and such.

thanks!

---

### Post by Praill on 2007-02-28
It looks like it shouldnt be too hard to install (if ubuntu doesnt install it for you).
[This site]("http://linux-wless.passys.nl/query_hostif.php?hostif=PCI") has a comprehensive list of wireless cards and their compatible linux drivers.
For your card it seems either
[http://hostap.epitest.fi/]("http://hostap.epitest.fi/") (Prism chipset)
or
[http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/") (Broadcom chipset)
would do the trick.

You can see if ubuntu will automatically detect the card using the live cd, but its not always accurate (ie. the live cd didnt recognise my card, but the installation did).

---

