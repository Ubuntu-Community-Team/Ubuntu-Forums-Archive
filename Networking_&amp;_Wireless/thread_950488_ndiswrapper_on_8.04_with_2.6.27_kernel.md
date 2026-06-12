---
title: "ndiswrapper on 8.04 with 2.6.27 kernel"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Jamson on 2008-10-17
Hey,

I had installed ndiswrapper through the Ubuntu 8.04 CD, and that went well. From there, i installed the .ini and voila, it all worked great. However, i was noticing terrible IDE performance on my 8200 chipset motherboard (not compatible with the SATA controller or something, got around it via. the generic_ide... command).

I found a kernel update program through the forums, and it rebuilt the Ubuntu 8.04 kernel to 2.6.27, and now my SATA chipset works fine (yay!). However, ndiswrapper is reporting to be working correctly, but it isn't picking up the wlan0 adapter. ndiswrapper -l shows that the device is noticed and working, but Network Manager and Wicd aren't seeing the wlan0 thing.

What can i do?

---

### Post by Ayuthia on 2008-10-17
> **Jamson said:**
> Hey,

I had installed ndiswrapper through the Ubuntu 8.04 CD, and that went well. From there, i installed the .ini and voila, it all worked great. However, i was noticing terrible IDE performance on my 8200 chipset motherboard (not compatible with the SATA controller or something, got around it via. the generic_ide... command).

I found a kernel update program through the forums, and it rebuilt the Ubuntu 8.04 kernel to 2.6.27, and now my SATA chipset works fine (yay!). However, ndiswrapper is reporting to be working correctly, but it isn't picking up the wlan0 adapter. ndiswrapper -l shows that the device is noticed and working, but Network Manager and Wicd aren't seeing the wlan0 thing.

What can i do?

Did you recompile ndiswrapper?  I thought that I read somewhere that ndiswrapper is having problems compiling with the 2.6.27 kernel.

---

### Post by Jamson on 2008-10-17
I tried re-installing it, if that is what you meant - through .deb packages.

How would i go about recompiling?

---

### Post by Ayuthia on 2008-10-18
ndiswrapper the application still appears to be there, but my guess is that the ndiswrapper.ko (kernel module) is not there for 2.6.27.  Wireless drivers have a kernel module that makes them work.  Since you compiled a kernel on your own, the ndiswrapper.ko file is no longer there.  Even if you have the .deb file to install it, I don't think that it will work just because Ubuntu creates a special ndiswrapper.ko for each kernel.

You will need to go to the ndiswrapper website ([http://ndiswrapper.sourceforge.net/index.html](http://ndiswrapper.sourceforge.net/index.html)) and download the most recent version and try to compile it.  I say try mainly because I have heard that 1.53 is not working with 2.6.27.

The other option is to either try the Intrepid beta (which uses the 2.6.27 kernel) or wait until the 30th for the actual release.

---

### Post by grogger13 on 2008-11-07
Has anyone revisited this since 8.10 upgrade.  I haven't gotten my wireless working on 2.6.27 i had to boot to 2.6.24 in grub to get wifi working.  I use ndiswrapper with my dell draft n 1500 (broadcom) and i'm using intrepid

---

