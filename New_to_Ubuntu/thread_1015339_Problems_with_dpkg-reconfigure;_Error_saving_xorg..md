---
title: "Problems with dpkg-reconfigure; Error saving xorg.conf"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by chickenpatty878 on 2008-12-18
My screen resoulution has been stuck at 640x480, so when I try and run dpkg-reconfigure..., these are my results.
> gerald-desktop:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081218175534
The questions it asks are just about my keyboard, not the monitor / video settings. Am I doing all of this correctly? And I'm running on a default xorg.conf file, so Im guessing i have to fill all of the info in myself? This is what it looks like now 
> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Im just trying to find a way to set my resolution to 1280x960, since there are no other choices than 640x480 in System > Preferences > Screen res. Thanks in advance, i have been looking around for 2+ weeks now and have found nothing to help. I do know that my monitor is a Dell M991, not to sure about the video card.

---

### Post by oldos2er on 2008-12-18
Can you post the output of "lshw"?

---

### Post by taurus on 2008-12-18
If you are not sure what graphic card do you have, run this command from a terminal to find out.

```
lspci | grep VGA
```
It's probably one of those Intel integrated graphic controllers.

---

### Post by handydan918 on 2008-12-18
> **chickenpatty878 said:**
> My screen resoulution has been stuck at 640x480, so when I try and run dpkg-reconfigure..., these are my results.

The questions it asks are just about my keyboard, not the monitor / video settings. Am I doing all of this correctly? And I'm running on a default xorg.conf file, so Im guessing i have to fill all of the info in myself? This is what it looks like now 


Im just trying to find a way to set my resolution to 1280x960, since there are no other choices than 640x480 in System > Preferences > Screen res. Thanks in advance, i have been looking around for 2+ weeks now and have found nothing to help. I do know that my monitor is a Dell M991, not to sure about the video card.
Try logging in to a console and issuing ```
sudo xfix
```

---

### Post by chickenpatty878 on 2008-12-18
> **handydan918 said:**
> Try logging in to a console and issuing ```
sudo xfix
```

@handydan, I ran recovery mode then xfix, and get the same message
```
xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081218175534
```
and that was all. Im having troubles with saving over this file for some reason.


After running 'lspci | grep VGA', i get ```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```
How much of this do I need in xorg.conf?

---

### Post by chickenpatty878 on 2008-12-22
Any ideas on how i use this information to build a new xorg.conf?

---

### Post by chickenpatty878 on 2009-01-02
Hmmm, a week and i still haven't figured this one out. Any more ideas or would a fresh install be a good bet?

---

