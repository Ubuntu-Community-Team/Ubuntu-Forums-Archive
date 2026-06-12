---
title: "Graphics Driver problem"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by bwallum on 2009-06-07
Hi

I can't seem to get to the bottom of failures in the Xserver at boot up. It falls back to the console, flashes slowly 3 times then up pops a box saying that I need to manually configure the Xserver and that it will start in low res. When the Desktop comes up I get a stretched display on a 19" widescreen Xerox monitor.

If I try to use the nVidia X Server Settings I am told that I need to run nvidia-xconfig as root then restart X. That doesn't work so I am in a perpetual loop. I have tried loading the 64bit nVidia 185 driver (which works a treat on my other box) and it appeared to all go well but distorted low res is all I get on reboot.

How do I get back to a default setting and restart? xorg.conf is minimal just when I grasped the various sections of xorg.conf I find every thing is 'configured'. Where is the real configuration going on?

I'm on an AMD64 bit pc with an nVidia 6600LE card, running Jaunty AMD64.

Regards
Bob

---

### Post by fslezak on 2009-06-07
Can you send a screenshot of your desktop and a screenshot of the message.

---

### Post by bwallum on 2009-06-08
I'm not too sure exactly how I fixed this problem so be careful if following this.

I first installed the nvidia driver 180 from System>Administration>Hardware Drivers. It produced a stretched screen and wanted me to run nvidia-xconfig which took me back to the start as above.

I then tried to install the latest 64bit nvidia driver 185.18.14 as below:

[http://ubuntuforums.org/showthread.php?t=1140071](http://ubuntuforums.org/showthread.php?t=1140071)

When trying to turn off the X server I found that I couldn't. There was a lock on screen 0. I rm'd the lock file (sudo rm /tmp/.X0-lock) cd'd to Desktop and ran the nvidia install file again.

Upon reboot all was well! I have the nvidia 64bit 185.14 driver installed, with System>Preferences>Nvidia X Server Settings fully working. All nice and stable but as I say, not too sure how it was really achieved.

Thanks for responding
Bob

---

