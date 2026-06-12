---
title: "Wireless gets signal, but no internet"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by snick512 on 2007-12-29
Erm.. I have a linksys WRT-pieceofcrap-

Has Wireless Of course. 

I have security set to WEP 64bit with 1 passphrase, and one key.

Linux connects, and gets 60 percent signal but no internet. When i go to look at the 'connection information' everything has invalid IP's (0.0.0.0). So I think I'm missing a step. I remember doing some kind of command line to configure the wireless all the way.. instead of using the GUI.

Can someone help me out with this please?

(I really miss using linux, but I have to use windows until i get my wired net back:( and windows sucks as a main os!)

Thank you

---

### Post by kevdog on 2007-12-29
Linksys WRT54xx router??  Those are great routers if they can be flashed with dd-wrt firmware.  As far as your wireless card can you post

lshw -C network

Are you using a USB device?

---

### Post by snick512 on 2007-12-29
WRT54G - v6.

yes, a "USB Wireless 802.11 b/g Adapter"

It came on the HP, (Built in)

---

### Post by kevdog on 2007-12-29
Ok -- you are going to have to go on the internet and search for your computer and the type of internal usb wireless adapter that is contained inside.  (that is what you are telling me).  There is nothing you are going to be able to type at the command line that will tell you the chipset of the usb device.  The chipset discovery is key, since this will lead us to a driver, which will lead us to an installation method, which will lead us to configuring the driver, which will lead us to an internet connection. 

I thing you can flash v6 with the dd-wrt firmware.  May need to check on that.

---

