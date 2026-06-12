---
title: "blank screen on bootup, no login"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by zepl on 2009-08-05
Was trying to change my ATI driver, to fix my blender problems
Followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_Open_Source_Edge_Drivers"), 
The good nes is it worked, had a resolution of 800/600, so I did the last part, 

To switch to the radeonhd driver, add this to /etc/X11/xorg.conf : 
Section "Device"
	Driver		"radeonhd"
EndSection

logged out and my screen went blank, rebooted, nothing, recovery mode, auto repair grraphics's? did nothing. Not sure what to try.

---

### Post by fooman on 2009-08-05
in recovery mode....did you try the "xfix" option?

---

### Post by zepl on 2009-08-05
Yes, thats the option Imeant by "auto repair grraphics's"
I also found another solution, Using the hotkey for the terminal, and type 
sudo dpkg-reconfigure xserver-xorg
sudo reboot
I used CtrlAltF2 for the hotkey, not sure if that was right, nothing happened though

---

### Post by pastalavista on 2009-08-05
The only way I could ever restore my system when that happened, (and I've done it several times) is to basically reinstall xserver by booting in recovery mode, open a root terminal with networking and type ```
sudo apt-get update
``` to make sure networking works... and then ```
sudo apt-get purge xserver-xorg
``` and finally```
sudo apt-get install xserver-xorg
```

The only way I could get my 3D graphics working is following this post

[http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/]("http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/")
but it made my laptop run very hot.

---

### Post by zepl on 2009-08-05
Unfortunately the above solution didn't work, but could i use it to go backwards? osmeting like
sudo apt-get purge xserver-xorg-video-radeonhd
or by uninstalling the xserver-xorg are you uninstalling that to?

---

### Post by pastalavista on 2009-08-05
The post I mentioned with the solution changes your software sources to the 8.10 Intrepid repositories. You need to downgrade Xorg to a previous version from the Intrepid repos, lock the version in synaptic and allow for the use of the ATI driver 'fglrx'. Then revert back to the Jaunty repos.

It's all a bunch of overcomplicated crap now that ATI is co-operating. I'm counting on the kernel to be upgraded eventually. It already has a good bit, but it's not perfect yet.

---

### Post by zepl on 2009-08-05
i sort of understood that, but im still stuckim thinking i should just reinstall now

---

### Post by pastalavista on 2009-08-05
> **zepl said:**
> i sort of understood that, but im still stuckim thinking i should just reinstall now

Probably a good idea, but if you want your graphics to work properly, install 8.10 Intrepid Ibex.

---

