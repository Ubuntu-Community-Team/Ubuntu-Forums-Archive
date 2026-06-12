---
title: "I constantly have to enable my WL driver on startup"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Hoaxe on 2008-09-15
hey, 

like the title says,

When is start up the computer, I ALWAYS have to go in the restricted driver manager and enable the WL driver that my wireless card uses.

The weird thing is that when looking at the restricted driver modules on startup, my nvidia is always enabled (as it should be) but my WL driver isn't. And yet, the box next to it is always checked. That's very weird.

maybe i blacklisted it or something weird?

I'm not sure. does any one know what's wrong with my driver?
thanks.

---

### Post by CalderCoalson on 2008-10-15
Me too...

I have an HP DV6800z, with a BCM4328 wireless card.  Until today, I had to use ndiswrapper to get wireless to work, but Broadcom released a driver, and I tried that, then weird stuff started happening.  I enabled that, uninstaller ndiswrapper, and it worked until I restarted.  When I restarted, it didn't work, even though it showed up as enabled in the Hardware Drivers section, it said "Not in use".  When I disabled and re-enabled it, it worked fine.  Then I tried using the 'wl' driver because it's actually open source.  I restarted, typed "sudo modprobe wl" and I had wireless.  I can do this every time I restart the computer, but it's kind of a pain, so how do I get it to load by default.  Supposedly modprobe actually "adds and removes modules from the Linux kernel" so theoretically, they should load with the kernel, but apparently not.  I'm sure this is a really easy fix, so any help whatsoever will be much appreciated.

---

### Post by Ayuthia on 2008-10-15
It looks like the module is not being loaded upon boot.  Try the following:
```
echo wl|sudo tee -a /etc/modules
```
That will add the wl module to /etc/modules.  This file is read when booting so that it will load the drivers that are in that file.  Hope that helps.

---

### Post by CalderCoalson on 2008-10-15
Thank you thank you thank you for the speedy response!  I was stupid assuming /etc/modules was a directory, so I didn't know what people meant by "add to /etc/modules".  :D

---

