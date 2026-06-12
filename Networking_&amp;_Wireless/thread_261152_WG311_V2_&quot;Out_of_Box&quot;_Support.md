---
title: "WG311 V2 &quot;Out of Box&quot; Support?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by jbcook on 2006-09-19
Okay, I hope I don't get flamed for this. I searched the forums quite a bit and didn't find my answer. I have a Netgear WG311 V2 wireless card. The Ubuntu hadware compatiblity chart says this card is suppose to work out of the box.

I am using the live cd at this point, I'm not sure if I want to do a full install yet. But, my wireless card will not see the wireless network. I have a wlan0 in network interfaces and the hardware manager shows that the card is loaded with the proper drivers. If I remember right it shows that ACX111 is loaded.

I would rather not have to use the ndiswrapper if I don't have too. Actually, I'm not even sure if I can since I'm just using the live cd so far.

Anyway, does anybody have a suggestion on where to go from here? When the hardware compatibility chart says "out of the box" support, does that mean when you do a full install only? Thanks everybody!

Edit: I am using version 6.06.1 Desktop.

---

### Post by apoth on 2006-10-08
Try something like ```
options acx firmware_ver=1.2.0.30
``` in /etc/modprobe.d/options

---

