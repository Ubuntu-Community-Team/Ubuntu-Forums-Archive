---
title: "No wired Network after upgrading to Hardy and iwlwifi"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Little_Tee on 2008-07-16
Hi there,

I upgraded my ubuntu version on my Compaq nx7400 a few weeks ago to Hardy, kernel 2.6.24-19-generic, which resulted in my Wireless network (Intel Corporation PRO/Wireless 3945ABG) not working anymore. I fixed this using the [iwlwifi project]("http://intellinuxwireless.org/?p=iwlwifi"), and now it's working great again (except for the led, indicating the wireless is on). HOWEVER, this resulted in my wired network connection (Broadcom Corporation BCM4401) not working anymore. Eth0: device not recognised. It is detected by lspci, but basicaly it's recognised anymore as my eth0 device. I cannot select it anymore in network-admin. 
I think it removed the b44 module in the installing process, which I think I need for my ethernet card. Trying to add it again with modprobe b44 (as root) , I get "Error inserting b44 (/lib/....b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)"
dmesg | tail -1  gives me: 
b44: Unknown symbol ssb_dma_translation

Any suggestions on how to get both my wireless + wired  internet connections running?

Thanks !

---

### Post by iris-n on 2008-07-19
Hi Little,

It was unclear if it was the upgrade or the wireless that made your wired networking malfunction. However, in my machine it was the upgrade to hardy, as for some unknown reason it automatically blacklists the b44 driver. I just commented out that line, and it went up again. As for the wireless, i'm sorry i can't help, as i use a different card.

Hope that helps,

Iris

---

