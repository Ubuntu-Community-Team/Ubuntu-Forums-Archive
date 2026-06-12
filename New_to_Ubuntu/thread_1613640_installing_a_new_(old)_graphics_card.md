---
title: "installing a new (old) graphics card"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by R.I.C. on 2010-11-04
I am running Ubuntu 10.10 on a Dell Dimension 1100 with integrated graphics card.  I'm trying to "upgrade" to an NVIDIA Geforce 5500 FX card.  If I simply try to plug in the card, the monitor won't work (regardless if it's plugged in to the new or old card).  So what I've been trying is to install the drivers first, then plug in the card.  I see that the one I need is the 173, and that it is supposed to work with 10.10.  Is this correct?  The first time I tried, it crashed everything and I reinstalled the OS.

Am I going about this the right way?  Do I need to disable the integrated card in BIOS before doing anything?

Thanks.

---

### Post by cariboo on 2010-11-04
As of right now, there are no restricted drivers for your video card. I would suggest you remove /etc/X11/xorg.conf, then insert the card and reboot. The operating system has to be able to detect the video card in order for it to know which drivers to load, so pre-installing the drivers, won't do a lot of good.

---

### Post by R.I.C. on 2010-11-05
OK, so I've done this now twice, and both time, nothing happens.  I reboot, but the monitor never works.  I've tried two different PCI slots.  Is there any way to tell if the card actually works?  Any other suggestions?  Thanks.

---

### Post by R.I.C. on 2010-11-05
Stupid question:  can I insert the card while the computer is on?  Or is that just asking for electrocution?

---

### Post by R.I.C. on 2010-11-05
And to further clarify, my "monitor" is a Sony 40" 1080p TV.  It is connected via VGA.

---

### Post by spook1980 on 2010-11-05
check your bios settings dude.
it may have a setting for onbord graphics or pci card.

so plug in your graphics card. plug your monitor into your your onbored vga port, get into your bios check the settings if its set to onbored graphics fix it.

unplug vga cable plug into graphics card n reboot.

---

### Post by R.I.C. on 2010-11-05
If I plug in the card, the monitor won't work, regardless of where it's plugged in.  In BIOS, I can't find anything that has anything to do with PCI slots.  The "primary graphics control" settings have two options - onboard or auto.  It's set to auto...

---

### Post by R.I.C. on 2010-11-05
Awesomely, because I ran sudo nvidia-xconfig (after simply getting ride of the file didn't do anything), I am now stuck in tty1 with the integrated card....

---

