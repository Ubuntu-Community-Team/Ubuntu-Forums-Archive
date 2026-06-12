---
title: "Warning: Those Upgrading From Feisty To Gutsy Using Ndiswrapper"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-13
Anyone planning to upgrade from feisty to gutsy with a working ndiswrapper installation ---

Gutsy introduces a new kernel in the installation.  ndiswrapper is a custom kernel module that is dynamically loaded into the kernel either at boot or the command line.  What this means is that with the upgrade in the kernel, the old ndiswrapper kernel module contained in the older fiesty kernel will no longer be available when booting into the new kernel.

I do not know if the gutsy kernel headers will be included in the upgrade.  If they are not you will either have to downloaded them: (sudo aptitude install linux-headers-`uname -r`), or if you dont have an internet connection, you will have to get them from a gutsy installation disk (sudo apt-cdrom add, sudo aptitude update, sudo aptitude install linux-headers-`uname -r`).

If you have installed ndiswrapper from source in fiesty, **you do not need to downloaded the ndiswrapper source package again, but you will need to compile ndiswrapper again against the newer gutsy kernel headers and then reinstall ndiswrapper**.  You will also have to reinstall the windows driver (or whatever driver you were using into the card) back inside ndiswrapper. 

The ndiswrapper link in my signature will help guide you if you forget how to install ndiswrapper from source.

---

