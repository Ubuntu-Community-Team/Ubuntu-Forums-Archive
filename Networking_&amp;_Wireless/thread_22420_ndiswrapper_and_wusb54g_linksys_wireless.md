---
title: "ndiswrapper and wusb54g linksys wireless"
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by ckr on 2005-03-27
Hey,

Yes it's another ndiswrapper question.

I had this adapter working in warty.  Now in hoary I'm having the following problems.

Ndiswrapper loads, the driver loads correctly.  Ndiswrapper -l shows driver present, hardware present.  Unfortunately, wlan0 will not get created.  I have done ndiswrapper -m, which says it makes the wlan0 alias, and indeed the default location shows that the alias has been created.  

I did see somewhere an error message that indicated that the driver could not initialize the device.  Would there be some reason that the windows driver that worked with warty's ndiswrapper would fail in hoary?  Any ideas how to force wlan0 to be created?

I tried doing lspci to map ndiswapper to a specific device, but the listings show no clear indication which device is the wireless.  They are all listed as unknown devices.  The gnome networking applet does not have an add button for connections.  Is there supposed to be one?  I cannot find any gui applets pertaining to wireless at all.

Here's my specs if they help:

amd 64 3000+,  nforce 3 motherboard (msi k8 neo plat. I think), 1 Gb mem, radeon 9600xt, wusb54g linksys usb wireless adapter.

Thanks,

Brian.

---

### Post by Rogers on 2005-04-21
[http://www.runithard.com/HOWTO-BCOM64WIRELESS/](http://www.runithard.com/HOWTO-BCOM64WIRELESS/)

I wrote a HOWTO for BROADCOM wireless cards .... i'm running an ACER FERRARI  \\:D/ 

Hope it helps.

---

