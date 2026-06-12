---
title: "some quuestions on the WiFi Edgy Guide for BCM43xx chipsets"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by xpan on 2006-12-21
hi,

I am trying to read through this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

in order to install my broadcom 4318 internal wifi chipset (using Acer Laptop 3120WLMi)

Unfortunately ndiswrapper does not work. It seems impossible for it to turn on the wireless antenna.

so:

in section: 1.3.1. Step 1: Obtaining the Firmware

should I, or shouldn't I get the wl_apsta.o file? I use Edgy Eft with kernel 2.6.17-10-generic

and if i get it, where shall I save it?

later on it says:

> 
You may have to extract the .sys file before the next step: if you downloaded an .exe, try to unzip it. If that fails, try to cabextract it (install the cabextract package). The file of interest is .sys. If you downloaded a .o, it is the file of interest.

I have two versions of the driver. I have downloaded the bcm4318x32.dapper.native.tar.gz files and the .exe file from broadcom's site (from which I took the .inf and .sys files and everything else).

Which one should I use?

And finally, before starting the operation, should I or shouldn't I blacklist the module that has been already installed with the normal Edgy installation (the one which does not work)...

thanks for your time

---

