---
title: "Nvidia preventing ubuntu from booting properly."
date: 2011-04-28
forum: New to Ubuntu
---

### Post by xd20 on 2011-04-28
So I had Wubi install ubuntu 10.04 back in october and I couldn't get ubuntu to load past the loading screen.  I turned off the splash and it was revealed to have a bunch of error codes.  So I came on here for some tips, and was eventually led to the notion that my nvidia card is causing the issues.  I went and turned on onboard graphics in the BIOS, since originally it was set to PCI.  I restart and load ubuntu, and it works fine.

Except, I get on ubuntu and install the proper nvidia drivers, reboot, change the BIOS option back to PCI and ubuntu fails to load yet again.

So I have to keep it set to onboard in order for it to work.  This wouldn't be a problem except that my onboard is really horrible so I use my PCI graphics for everything.  The card I use is a (PNY GeForce 8400gs 512mb PCI card).  

I can't figure out how come it doesn't let ubuntu load with my nvidia card.  My onboard is just some generic intel thing with 64 mb video memory.  Except in the bios i can only select up to 8mb when selecting onboard O_o.

I've tried installing using the alternate version of ubuntu but it doesn't make it passed the partitioning part, and keeps failing to create those special partitions.  I tried installing using a USB but with the same issues.  The only way I can install ubuntu is when I disable the PCI card.  Once installed however, and I turn the graphics card back on, ubuntu fails to load again.

Does anyone know what might be causing the issue?

---

### Post by xd20 on 2011-04-28
Any help is appreciated.

---

### Post by Jinren on 2011-04-28
Does your computer have a TV tuner?

I just had [a similar problem]("http://ubuntuforums.org/showthread.php?t=1738106"), which I solved by disabling the device (although there are more difficult/less extreme methods if you want to keep using it). For some reason I didn't fully understand, the proprietary Nvidia driver won't work alongside it.

---

