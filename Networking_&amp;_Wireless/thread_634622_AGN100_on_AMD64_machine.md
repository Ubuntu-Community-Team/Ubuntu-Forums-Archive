---
title: "AGN100 on AMD64 machine"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by grappler on 2007-12-07
I am trying to get Linksys WMP54GX wireless card working on an AMD Athlon 64 X2 Dual Core machine.

I have installed ndiswrapper from the Gutsy release and tried various versions of the drivers - including the ones used (successfully) on the Windows partition. While they seem to detect the hardware - checked with ndiswrapper -l - none of them provide me with a wireless device - wlan0 (I did ndiswrapper -m).

I get the following message in dmesg:

kernel is 64-bit, but Windows driver is not 64-bit; bad magic: 010B

I looked on the web for a 64-bit windows driver for AGN100 (the chipset for WMP54GX) without success. Does anyone know where I could find one or perhaps how I can find a way round this problem?

Thanks

Grappler

---

### Post by grappler on 2007-12-08
I installed the 32-bit version of gutsy and used a 32-bit driver. This is a kludge of course, and I'd prefer to have the 64-bit version running. Any ideas?

thanks

Grappler

---

### Post by dreamfly281 on 2008-01-03
Maybe this will be helpful for you.  [http://sourceforge.net/projects/agnx80211driver/](http://sourceforge.net/projects/agnx80211driver/)

---

