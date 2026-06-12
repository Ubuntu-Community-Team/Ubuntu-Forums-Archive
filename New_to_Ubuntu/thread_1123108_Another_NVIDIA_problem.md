---
title: "Another NVIDIA problem"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Lben on 2009-04-11
Hey guys.  I have been searching for the solution to my problem, and have found many people ask similar questions, but none that helps me.  I am new to Linux so please be patient.

I have downloaded the correct drivers for my onboard NIVIDA card (6 series).  I followed the directions on the page which asked my to run the following.

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86-180.44-pkg1.run

I do this and follow a few simple steps and everything seems to go smoothly.  It even has a step that configures my xconfig file for me.  I restart the xserver and everything appears to be working great.  That is unless I restart my system.  Upon restarting my resolution is back at 800x600 and opening the NVIDIA x server settings file displays an error stating that "it does not appear I am using the NVIDIA x drivers".  If I reinstall the driver all is well again until I reboot.  Any ideas would be greatly appreciated. 

Not sure if it matters, but I am running Ubuntu on a 4 gig USB drive.

---

### Post by labinnsw on 2009-04-11
Go to: System >> Administration >> Hardware Drivers
Is the driver enabled? If not enable it.

---

### Post by Lben on 2009-04-11
I went to "Hardware Drivers" and Activated the recommend driver.  It said it was downloading and installing. When complete, it asked me to restart the computer.  I did so and it loaded again in 800x600.  I checked to see if the driver was showing active, but it says  "a different version of this driver is in use".  Still cant change the resolution.

---

### Post by sandyd on 2009-04-11
uh oh, he now has 2 nvidia drivers installed at once....


thats not good.....

in the "Device" section of xorg.conf, change 
the part where it says 
```

Driver "nvidia"

```
to
```

Driver "nv"

```

thats all i can say.

---

### Post by labinnsw on 2009-04-11
Also make sure that only one of those drivers is enabled, the recommended one.
After that you should be able to change the resolution at: System >> Preferences >> Screen Resolution

---

### Post by JoshuaRL on 2009-04-11
Is it a persistent USB drive install?  If not, you may have a USB drive version of a LiveCD.

---

### Post by Lben on 2009-04-11
This is what I have in my xorg file....


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

This is after a restart, I have not checked to see if it is different if I install the driver and not restart.

As far as checking that only 1 driver is enabled under "hardware drivers".  My list has two drivers listed.  Neither is showing as being active (even after I click to activate it and restart), but the recommend says a "different version of this driver is in use". 

This should be a persistent install.  When booting I boot to the option that says something like run in persistent mode.  I also and able to make and keep changes like wallpaper and screensavers.

---

### Post by Lben on 2009-04-11
I have found that when I install the driver and everything is working correctly, much more info is added to the xorg file.  After restart, it goes back to the short file I posted above.  So it seems the problem is that the xorg file is not being saved on restart.  Anyone know why this would be happening?

---

### Post by unutbu on 2009-04-12
I believe that if you want to successfully install the nvidia driver from a NVIDIA-Linux-*.run file, you must first remove certain Ubuntu packages related to nvidia (see [http://ubuntuforums.org/showthread.php?t=52924](http://ubuntuforums.org/showthread.php?t=52924)). 

Conversely, if you want to successfully install the nvidia driver using Ubuntu packages (nvidia-180-modaliases, nvidia-common, and nvidia-glx-180), then I believe you should clear the system of any files installed by the NVIDIA-Linux-*.run file first.

I've been searching around for instructions on how to do that. 
The closest I have come is from here:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt)
which says the command to use is 
```

sudo nvidia-installer --uninstall
```
I'm not even sure if you'll have an nvidia-installer program on your machine, however, since that web page is quite old (circa 2004). Perhaps it is worth a try anyway. After you do that, be sure to remove and then reinstall the nvidia-180-modaliases, nvidia-common, and nvidia-glx-180 Ubuntu packages.

---

### Post by Lben on 2009-04-12
I can edit xorg with sudo gedit, restart xserver and everything works fine.  If I restart the computer, xorg goes back to the stock file.  I have even tried changing the owner of xorg to my username and still the files changes back to the stock file and owner goes back to root after restarting.  I can't cant seem to save any changes to this file.  Can anyone help?

---

### Post by JoshuaRL on 2009-04-12
> **Lben said:**
> I can edit xorg with sudo gedit, restart xserver and everything works fine.  If I restart the computer, xorg goes back to the stock file.  I have even tried changing the owner of xorg to my username and still the files changes back to the stock file and owner goes back to root after restarting.  I can't cant seem to save any changes to this file.  Can anyone help?

You really don't want to change the permissions of xorg.conf to anything other than root.  As you have seen, modifying it can have a big impact on your computer's usability.  So its best to just leave it as it is.

Have you tried the suggestions by unutbu?  That seems to be the way to go.

---

