---
title: "Dual Monitor DVI setup?"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by developmentalmadness on 2011-03-21
I have a Dell Precision M4400 (NVidia m770) with a docking station which has dual DVI ports. If I plug into the VGA port on the docking station or directly into my laptop I can use one of my monitors. But if I'm plugged into the DVI ports on my docking station I can boot, but once Ubuntu loads to the login screen (I get the flashing cursor, then a short bit of text for a split second) my monitors go black. If I undock my laptop the screen refreshes and everything works fine from my laptop. I login, dock my laptop and open the monitor settings and Ubuntu sees my monitors and correctly identifies them (Samsung 19" and Samsung 24"). But even if I try every available resolution I never get anything displayed on my monitors. I tried opening xorg.config but it doesn't exist  in /etc/X11 (or isn't listed when I cd /etc/X11 then ls in the terminal). 

I installed using the Windows installer so I have a dual boot system alongside Win7 x64. I checked and I seem to be running Ubuntu 10.10 (Maverick) x64. 

I'd like to switch over to using Ubuntu from Windows and am just trying to make sure I can get everything setup and working the way I like before I make the jump. So far I've been able to get my other peripherals working on the docking station (eth, mouse, keyboard) and my VPN (Cisco AnyConnect). Any help would be greatly appreciated.

And yes I'm a total noob.

---

### Post by developmentalmadness on 2011-03-22
Ok, so I found my answer here: [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html). Should be required reading for all noobs like me. Anyway, I went to System -> Administration -> Additional Drivers and installed the (recommended) NVidia drivers. After a restart, opening the display preferences console opened up the NVidia console, I changed my settings, clicked "save to x configuration file", then logged out and logged back in to restart x window and now it's working :)

---

