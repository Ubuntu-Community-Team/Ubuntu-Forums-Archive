---
title: "Broadcom wireless, Gutsy, ndiswrapper"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by rebbi on 2007-10-23
Howdy,

I have an HP laptop (DV6326us) with a Broadcom wireless card built in. (Dell 1390 mini PCI, rev. 1). In other distros, I've used ndiswrapper to install the bcmwl5.inf files, and it works well. With Gutsy, I've used the Restricted Drivers manager to install the firmware for the bcm43xx driver. The wireless works quite well, although about 20% of the time, my wireless card won't come back up after a suspend to RAM (the indicator light stays orange instead of going blue) or else it just seems to drop the connection. I'd like to try to use ndiswrapper as an alternative, but can't seem to get it to work under Gutsy. I've installed the gtk front-end for ndiswrapper and installed the .inf file, but my indicator light still comes up orange instead of blue, and networkmanager doesn't see any networks. Is there a confirmed procedure for using ndiswrapper with Gutsy? Is there some place I need to be blaSFcklisting the bcm43xx driver by hand?

Thanks in advance!!](*,)

SF

---

### Post by growltiger on 2007-10-23
No solution.  But if misery likes company, my situation is a bit more horrorific:  my system hangs after I provide the password.  (So I can see the available wireless networks.)

I, too, am using ndiswrapper to load a Broadcom wireless card (a Hawking SkyHawk).  The driver is different, though.  It is a tnet1130.  After the gutsy gibbon upgrade, I removed and then reinstalled ndiswrapper and the driver.  No joy!  :mad:

---

### Post by growltiger on 2007-10-23
Okay, I got it too work, sort of...

If I boot without a wired ethernet connection, I hang on authentication.
If I boot with a wired ethernet connection, I connect.
If I then disconnect the wire the wireless network springs to life without the password challenge.  This was an upgrade so no doubt that information is stored somewhere in the bowels of /etc.

This is not an acceptable work-around, but it is a work around.

---

### Post by kevdog on 2007-10-23
Installing ndiswrapper on gusty is the exact same as in feisty with the bcm43xx driver being blacklisted in the /etc/modprobe.d/blacklist file.  Exact for the change of location of the /etc/iftab file, I havent found, and the bcm43xx driver as part of the restricted driver package, I havent found anything different on gutsy compared to feisty.

---

### Post by mgolden on 2007-10-23
My ndiswrapper does work, (I have a Dell Inspiron 6400) but it for some reason it requires a sudo modprobe ndiswrapper every time I power up.  No idea what could be causing it, ideas would be appreciated.

---

### Post by kevdog on 2007-10-23
echo ndiswrapper | sudo tee -a /etc/modules

Do that once and that should do the trick!

---

### Post by rebbi on 2007-10-24
> **kevdog said:**
> echo ndiswrapper | sudo tee -a /etc/modules

Do that once and that should do the trick!

Okay, ndiswrapper is working great now!

The steps:

1) Downloaded the ndisgtk gui from the repos.
2) Used it to install the bcmwl5.inf files
3) added "blacklist bcm43xx" to /etc/modprobe.d/blacklist
4) added ndiswrapper to /etc/modules

Rebooted. Done!

By the way, I'm convinced that the Broadcom cards in the newer HP laptops **work much better**, still, with ndiswrapper than with bcm43xx. On my laptop, wireless connections don't drop out, and most impressive, my wireless connection comes right back up after a suspend, every time. Cool!

:guitar:

SF

---

### Post by hwertz on 2007-10-27
> **rebbi said:**
> Okay, ndiswrapper is working great now!

The steps:

1) Downloaded the ndisgtk gui from the repos.
2) Used it to install the bcmwl5.inf files
3) added "blacklist bcm43xx" to /etc/modprobe.d/blacklist
4) added ndiswrapper to /etc/modules

Rebooted. Done!

By the way, I'm convinced that the Broadcom cards in the newer HP laptops **work much better**, still, with ndiswrapper than with bcm43xx. On my laptop, wireless connections don't drop out, and most impressive, my wireless connection comes right back up after a suspend, every time. Cool!

:guitar:

SF
     Thanks!
     As for the cards working better with ndiswrapper -- yes, they do.  My Dell's got a BCM4318, and basically the newer bcm43xx chips like that, bcm43xx "works" but can't control the transmit power and I think receive sensitivity.  It's a shame too, it's a great chip other than Broadcom being tight with the programming specs.

---

### Post by rebbi on 2007-10-27
> **hwertz said:**
> Thanks!
     As for the cards working better with ndiswrapper -- yes, they do.  My Dell's got a BCM4318, and basically the newer bcm43xx chips like that, bcm43xx "works" but can't control the transmit power and I think receive sensitivity.  It's a shame too, it's a great chip other than Broadcom being tight with the programming specs.

Well, that may explain the dropouts and such!

SF

---

