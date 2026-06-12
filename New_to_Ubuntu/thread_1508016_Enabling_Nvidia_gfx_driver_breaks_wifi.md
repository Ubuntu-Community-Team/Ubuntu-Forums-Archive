---
title: "Enabling Nvidia gfx driver breaks wifi"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by johny_h on 2010-06-12
Hi Guys,

I'm relatively new to Linux and I'm now having a small problem with Ubuntu 10.04, Nvidia and my wifi.

Ok, I installed Ubuntu 10.04(64-bit) on my PC, everything seemed cool. My wifi card's working properly, I connected to my router and downloaded ll the updates. I then wanted to get the desktop effects working, so I downloaded the Nvidia driver through the System>Administrator>Hardware Drivers and installed the Nvidia Proprietary driver. My desktop effects are now enabled, with wobbly windows and stuff, but now my pc won't connect to the internet anymore.

I then disabled the nvidia (through System>Administrator>Hardware Drivers), rebooted and the wifi worked again. I enabled the drivers, rebooted and the internet wouldn't work again.

Oh, and when I say the internet isn't working, I mean the computer connects to the router but I can't ping the router, and when I try to visit a site I get the normal couldn't connect message in Firefox.

I tried to download the drvers from Nvidia's site, then ran /etc/init.d/gdm stop, installed the package, and then rebooted, but then I get a message saying that it couldn't load the Nvidia Kernel Module.

So for now, the only way for me to get graphics acceleration is to activate the drivers, but then I lose wifi. Has this happened to anybody, or could somebody please help me troubleshoot this?

Also, I can boot into windows and my wifi card works fine there. I also have a usb dongle that I tried to use but that also only works if the gfx driver is disabled. I use a static IP and DNS.

My pc specs are:
Processor: AMD 720BE
Mobo: Asus m4a785-m
Wifi card: Zuxa PCI 802.11n
GFX: Asus GTX 285

I also tried reinstalling about 4 or 5 times but it never works.

Thanks,
-Johnny_h

---

