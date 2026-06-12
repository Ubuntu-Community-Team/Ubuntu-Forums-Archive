---
title: "Jaunty ATI Drivers Open Source 3D Acceleration"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Promaster91 on 2009-04-27
Hi. I just upgraded to Jaunty and I am having problems with my video drivers. I can no longer use the flgrx driver because of the Xorg update. I am currently using the open source driver but I am having very little success with the 3D acceleration. It lags considerably. I was wondering if anybody was successful with 3D acceleration with a Radeon ATI card. If you could please explain what you did and/or post your xorg.conf file that would be greatly appreciated. Thanks :).

Here is my Xorg.conf file, I am using a Radeon X1200 with the xf86-video-ati driver and EXA acceleration.

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X1200"
        Driver          "radeon"
	Option          "DRI"            "on"
        Option          "AccelMethod"    "EXA"  
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection

```

---

### Post by PeonDevelopments on 2009-05-04
I have this issue too. No 3D acceleration in Jaunty.
I used the 86x_64 bit ati 9.4 catalyst driver; my card is the ATI Radeon 3870.
The 1920x1200 resolution is detected fine.

---

### Post by Christopher on 2009-05-04
Im using the ATI 9800 pro 128mb card & i did a fresh install and then went to use Envy to install my drivers and i got a frozen screen on reboot with alot of funky colors lol. I then did another fresh re-install of Ubuntu 9.04 - Jaunty Jackalope and all is fine. Do we just wait for a new updated driver from ati ?:confused:


I noticed the drivers offered for download in Envy are 8.2 and here  [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)  they are 9.3, anyone using 9.3 on Jaunty Jackalope that has a radeon card ?

---

### Post by CrystalShadow on 2009-05-04
This sounds a lot like what I've been dealing with on my laptop with an X1400 chip.

I've been trying to avoid re-installing the whole thing, but I guess that'd be the quickest solution.
How unfortunate.

---

### Post by ii Candor ii on 2009-05-04
> **CrystalShadow said:**
> This sounds a lot like what I've been dealing with on my laptop with an X1400 chip.

I've been trying to avoid re-installing the whole thing, but I guess that'd be the quickest solution.
How unfortunate.

Same here. I'm trying to save the installation because I have a project saved in the XP virtual machine I installed on it. Looks like no dice for me though.

---

### Post by Muffinabus on 2009-05-04
I am using the open source drivers on Jaunty and have had no problems with 3D acceleration using my X1950GT.  I can run Compiz perfectly.  However, it worked out of the box, I didn't do *anything* extra, so I doubt I'll be much help.

My xorg.conf is pretty much empty:

```
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
```

> **Christopher said:**
> Im using the ATI 9800 pro 128mb card & i did a fresh install and then went to use Envy to install my drivers and i got a frozen screen on reboot with alot of funky colors lol. I then did another fresh re-install of Ubuntu 9.04 - Jaunty Jackalope and all is fine. Do we just wait for a new updated driver from ati ?:confused:


I noticed the drivers offered for download in Envy are 8.2 and here  [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)  they are 9.3, anyone using 9.3 on Jaunty Jackalope that has a radeon card ?

You cant.  The proprietary drivers for the new 'legacy' cards will not work in Jaunty.

---

### Post by Will It Blend? on 2009-05-09
I am having a very similar problem. I have an (old) Radeon X300 card running on my dimension 8400, and the new X server does not like it. I've tried installing the fglrx drivers, but that doesn't go over well. I log out, and the screen goes black (permanently), so I turn off the computer. Reboot, and as soon as X Windows is up (for lack of a better word), I'm greeted by a coleidescope of colors.

I quickly uninstalled those. I think many people are suffering from this problem. I've mediated the lack of 3d acceration somewhat by using fluxbox, but the effects are still noticable. My  xorg.conf file is pretty much default:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by anewguy on 2009-05-09
> **Promaster91 said:**
> Hi. I just upgraded to Jaunty and I am having problems with my video drivers. I can no longer use the flgrx driver because of the Xorg update. I am currently using the open source driver but I am having very little success with the 3D acceleration. It lags considerably. I was wondering if anybody was successful with 3D acceleration with a Radeon ATI card. If you could please explain what you did and/or post your xorg.conf file that would be greatly appreciated. Thanks :).

Here is my Xorg.conf file, I am using a Radeon X1200 with the xf86-video-ati driver and EXA acceleration.

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X1200"
        Driver          "radeon"
	Option          "DRI"            "on"
        Option          "AccelMethod"    "EXA"  
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection

```

Please excuse me for asking a dumb question, but everyone has to learn somehow, right?  I noticed that you have "ATI Technologies, Inc. Radeon X1200" as the Identifier for your adapter, yet in the screen section you identify the Device as "Configured Video Device".  I thought xorg matched the ID's to build the screen, so are you sure you are using the ATI device?

Thanks,
Dave :)

---

### Post by jemlinus on 2009-05-10
Please set the driver section as "ati" nothing else.

Also anewguy is right.

---

