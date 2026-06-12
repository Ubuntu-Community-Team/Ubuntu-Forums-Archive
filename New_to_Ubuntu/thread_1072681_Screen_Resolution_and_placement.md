---
title: "Screen Resolution and placement"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Irresistible Force on 2009-02-17
Hello, I only started using Ubuntu (and Linux in general) yesterday so I bear with me.  I'm trying to set up a HTPC linked to my WXGA plasma TV.

I've got a couple of problems: after logging in the screen resolution changes and the WXGA output is way off to the left.

I've installed a dual boot setup with Ubuntu 8.10 and XP.  The graphics card is an nidia 8200.  I activated the 177 driver with the driver manager included in Ubuntu.

I used gksudo nvidia-settings to change the resolution to 1360x768 and saved xorg.conf   . After a reboot the login screen is displayed at the correct resolution, but once I've logged in the resolution reverts to 1024x768 and the settings are at 'Auto' in the nVidia X Server Settings dialog.  I've tried inserting xrandr lines into the gdm.conf but I don't really know what I'm doing and just killed the gnome.

Even when I adjust the screen to the correct resolution it's a long way off to the left, cutting off part of the desktop.  I've tried adjusting the TV but it can't move and resize enough.  I tried using xvidtune but it says the modeline is not supported by my hardware config.  When I took the modeline given by xvidtune, and put it into the xorg.conf it just resulted in a black screen and I had to revert back.  Again, don't really know what I'm doing but I've spent a fair amount of time googling and trying to follow forum solutions as closely as possible.

Any help or pointers to the relevant guides would be much appreciated.  The main reason I'm trying Ubuntu is because I had couldn't get XBMC to work on XP!  Good job my CD player works!

---

### Post by Irresistible Force on 2009-02-19
Anyone got any ideas? Anyone having similar problems?

---

### Post by Irresistible Force on 2009-02-19
If anybody else has had this problem, I have found a work around:  I used a HDMI cable instead.  It automatically adjusts the resolution to 1280x720 and there's no timing problems (screen position) because it's digital.

---

### Post by mikechant on 2009-02-19
Just to mention something related: I didn't realize how much 'which cable' matters until I got a new PC last year. It's a Dell 530, which Dell sell a Ubuntu version of, so I expected easy compatability when I installed Ubuntu; I had a 20" Dell Monitor with a native resolution of 1440x900.
The screen came out at 1024x768, looked like crap, and I had no luck trying to configure it with xorg.conf etc. But the mistake was that I'd used the VGA port (which came with a lead already plugged in). When I switched to using the DVI port instead, the correct resolution was detected correctly and automatically.

I guess the lesson is to only use VGA ports as a last resort (e.g. some netbooks only seem to have VGA ports).

---

