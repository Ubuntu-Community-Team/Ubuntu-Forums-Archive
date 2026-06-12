---
title: "How do I get WPA to work?"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by infocom on 2006-08-20
Hi
I have been struggling for days to get wireless to work on Ubuntu. The furthest I have got is to get it working when WPA-PSK is disabled. It will not work when it is enabled.

I cannot get Network Manager to work. It sits on my tray and is always saying No Networks Detected and gives me the option of "Enabling Networks", which I can click forever and it never gets enabled. 

So does anyone know how to get it to work with WPA-PSK enabled with a pass phrase?

Thanks
Laurie

---

### Post by infocom on 2006-08-21
Anyone have any ideas?

---

### Post by lupine_nickt on 2006-08-21
To use WPA-PSK, you need to run a program called WPA Supplicant ('sudo apt-get install wpasupplicant'). 

'man wpa_supplicant' gives you all the info you need to set it up, or there are somewhat easier-to-digest HOWTO's around.

xF,

...Nick

---

