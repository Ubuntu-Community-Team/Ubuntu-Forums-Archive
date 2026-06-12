---
title: "My monitor isn't supported"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by mcse37 on 2009-11-10
My Roswill R912E LED monitor isn't supported by Ubuntu 9.10.  As a result, I can't go any higher than 800X600 resolution.  I understand that xorg.conf is not longer included in this distribution.  What can I do?

Thanks,

Bob

---

### Post by stderr on 2009-11-10
Well, all monitors should be supported per se, although some may require manual entry of the resolution (and sometimes refresh rates etc) - you can still use xorg.conf for this.

It strikes me as being more likely that your graphics card drivers aren't setup properly - have you activated a proprietary driver through System->Administration->Hardware Drivers yet? Then, depending on which card you've got (e.g. nvidia has nvidia-settings) you can normally set such things through the driver's configuration app. Failing that, you can still manually edit xorg.conf.

xorg.conf should be at: /etc/X11/xorg.conf (just take usual precautions: backup before editing, etc)

---

### Post by rhythmiccycle on 2009-11-10
I had this same problem and I just fixed it, now I want to help others, because I know how much it sucks.

if what stderr said doesn't work then I might be able to help.

first of all what resolution do you want to use?

---

### Post by mcse37 on 2009-11-13
1024 x 768 (or higher).

I've also tried using the NVidia driver, but I can't set it to anything higher than 800 x 600.



Thanks

Bob

---

### Post by oldos2er on 2009-11-13
What make/model video card do you have?

---

### Post by mcse37 on 2009-11-14
GeForce FX 5700LE

I'd be willing to create an xorg.conf, but without a template I wouldn't know where to begin.

Thanks,

Bob

---

### Post by oldos2er on 2009-11-14
> **mcse37 said:**
> GeForce FX 5700LE

I'd be willing to create an xorg.conf, but without a template I wouldn't know where to begin.


 Have you checked System, Administration, Hardware Drivers? You should see an option to install proprietary video drivers there.

---

### Post by SpongeBob SquarePants on 2009-11-14
Hi Bob,

I have this problem all the time. The xorg.conf file does exist. It's in /etc.X11. You just need to add a few lines to it. Below are the ones I add for my monitor (a flat screen monitor with a max resolution of 1280x1024). You'll need to tailor the values to fit your own needs. Particularly be careful to not set your max res above what your monitor can handle...same with the refresh rate. If in doubt look up your monitor specs online or in the manual. 

But all I do is replace the monitor/screen values in xorg.conf with the ones below....log out then back in, and it's all sorted.

Back up your xorg first, in case things go tits up.

> Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x1024"
Horizsync 24.0 - 80.0
Vertrefresh 50.0 - 75.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1280 1024
Modes "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

As you say, the problem is related to your monitor not being detected correctly. The nVidia software registers a CRT monitor, not a TFT, and there's no way of changing it...unless you change the xorg manually.

---

### Post by mcse37 on 2009-11-14
Thanks SpongeBob!  Modified my xorg.conf & my monitor is now working correctly!

---

### Post by iissmart on 2009-11-15
> **mcse37 said:**
> Thanks SpongeBob!  Modified my xorg.conf & my monitor is now working correctly!

Did you change any of the values that were quoted above? I'm using a fresh install of 9.10 (with the nvidia drivers enabled) on a Rosewill R912E, added "UseEDID" "FALSE" to my xorg.conf, and now I'm stuck in 800x600 too. How did you get it working?

---

### Post by rhythmiccycle on 2009-11-15
> **iissmart said:**
> Did you change any of the values that were quoted above? I'm using a fresh install of 9.10 (with the nvidia drivers enabled) on a Rosewill R912E, added "UseEDID" "FALSE" to my xorg.conf, and now I'm stuck in 800x600 too. How did you get it working?


I had the same problem, but solved it with xrandr

check out this post
[http://ubuntuforums.org/showthread.php?t=1321224](http://ubuntuforums.org/showthread.php?t=1321224)

---

### Post by leehamer on 2009-11-17
Hi guys, 

Sorry to hijack a current thread but I have been experiencing these issues and I am stumped with how to sort this as I am very new to Ubuntu. I am using 9.10 and I want to try and manually configure my xorg.config file, I know what I need to put in (someone above has a monitor of the same spec so a copy of that info should work. However I dont know where abouts in the xorg.config file I need to put the info. 

Could someone tell me where to put it? My xorg.config file reads as follows:

> 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

I have downloaded the latest drivers for my Nvidia GeForce 5600 FX card and can enable visual effects so I assume that works fine, I am just stuck with a horrible resolution!! 

Any help would be greatly appreciated! cheers

---

### Post by iissmart on 2009-11-18
> **rhythmiccycle said:**
> I had the same problem, but solved it with xrandr

check out this post
[http://ubuntuforums.org/showthread.php?t=1321224](http://ubuntuforums.org/showthread.php?t=1321224)

Tried some of the things that were suggested there, but nothing seems to be taking effect. I'm still in 1280x1024 resolution, but not at 60hz.

---

### Post by mcse37 on 2009-11-19
I copied & pssted the contents of SpongeBob's post into my xorg.conf and changed the Horizsync & Vertrefresh rates to the values supported by the monitor.

---

### Post by SpongeBob SquarePants on 2009-11-20
> **leehamer said:**
> I have downloaded the latest drivers for my Nvidia GeForce 5600 FX card and can enable visual effects so I assume that works fine, I am just stuck with a horrible resolution!! 

Any help would be greatly appreciated! cheers

If the values you intend to copy and paste are for "screen" then simply delete the "screen" entry in your xorg.conf and paste in the new values. If there are values you want to paste in that don't currently exist in your xorg.conf, just add them in the middle somewhere.

Make sure you back up your xorg.conf first (in case something goes wrong) and make sure the values you paste in are supportable by your monitor.

---

