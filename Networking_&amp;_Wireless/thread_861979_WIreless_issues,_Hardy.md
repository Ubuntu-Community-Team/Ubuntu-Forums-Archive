---
title: "WIreless issues, Hardy"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by LaGzo on 2008-07-17
Hi, I'm having problems with my wireless internet. I just installed 8.04.

1. The livecd wireless worked no problems
2. Installed Ubuntu to drive, wireless doesn't work
3. Tried ndiswrapper, no go
4. I'm stuck now...

I believe I have a broadcom 4311 rev 02 card. Is my card even compatible with Ubuntu?

---

### Post by bluefrog on 2008-07-17
fair chance not to have the proprietary drivers installed.

I have rev1 not rev2 though.

---

### Post by LaGzo on 2008-07-18
Ok, so I think the ndiswrapper driver is deleting itself after every restart? I followed lswest's method in this thread [http://ubuntuforums.org/showthread.php?t=780212](http://ubuntuforums.org/showthread.php?t=780212). It works but when I restart and try to connect I can't. When I go to right click the wireless icon -> connection information it says ndiswrapper in the driver section. When I restart, theres nothing there. Oh and I did the script, but I may be doing something wrong?

---

### Post by LaGzo on 2008-07-18
Well I can't sleep so I came up with an idea. Maybe the script is wrong?

> 
sudo modprobe -r ssb
sudo modprobe -r b43
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

That is what I type to get it to work. In the startup script or something, the sudo command isn't there. Maybe I need to add the command to the startup script? Or it's not even executing the script at startup?

---

### Post by David Robertson on 2008-07-18
I had my wireless drop out between 2.6.24-18 & 19. I had to unload additional modules:

> # Swap ssb and ndiswrapper modules (releases wireless adaptor from ssb)
modprobe -r b43
modprobe -r b44
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b43legacy
modprobe b44
modprobe b43


I have a (hp) compaq presario v6500 series notebook containing bcm94311 rev 2 wireless.

Useful Links: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) - All about installing and has been updated with the extra instructions.

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) - Lots of info on cards

Hope this helps - my little blue stays on all the time now!

---

### Post by LaGzo on 2008-07-18
So I'm supposed to edit the ndiswrapper file with this?
> Modifying /etc/modprobe.d/ndiswrapper

Version 0.3

This is a much slicker solution than the previous versions (listed below), but it's unproven. This will customize how ndiswrapper loads:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 

The commands I used before already work for me, I just need them to be executed at every startup automatically. But, will this work?

Also when my wifi isn't working and ndiswrapper is not stated as the driver it's using wlan0, when it is working it's wlan1.

---

### Post by LaGzo on 2008-07-19
Bump

---

### Post by MindZEye on 2008-07-19
I had the exact same issue as this, the only solution I could find was to downgrade my linux-image-* package to revision 16 I think it was.

---

