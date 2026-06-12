---
title: "ATI 6950 Black Screen"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by sujitn on 2011-01-18
Hi, i just finished building my PC and installed Ubuntu 10.04 all well and good. However when i installed the ATI 6950 driver the PC restarted. Got upto the ubuntu splash screen then the screen just turns black. Any ideas on what to do? I did hit ctrl + alt + f1. but nothing happened. Also does anyone know if the 6950 drivers are supported by ubuntu? Thanks =]

---

### Post by sujitn on 2011-01-20
Bump

---

### Post by Linux000 on 2011-01-20
Have you tried booting into recovery mode?(At Grub, there should be a Recovery option) If so, what were the last couple error messages it gave?

---

### Post by Mark Phelps on 2011-01-21
Last time I checked the AMD site, they had no 6xxx drivers for Linux.  The latest they had was for the 5x series.  So, if you forced the installation of incompatible drivers, that would explain why you're getting no display.

---

### Post by khelben1979 on 2011-01-21
I suggest you configure your X server to use the open source Radeon driver instead, until there's a official driver available.

---

### Post by sujitn on 2011-01-22
Yep thanks i guess ur right. Can't do much until AMD launch the drivers for linux. Thanks every1 for ur help =]

---

### Post by ste_bran on 2011-01-25
Sorry for being a noob, but I didn't quite understand the answer above. I too have a newly built comp with an AMD (Ati) 6950 video card. I would like to install ubuntu 10.10 x64 as the only operating system.

Since AMD still has no linux drivers, should I install Win 7 instead and install ubuntu later when drivers appear, or do I have an option to install using an X server (whatever that is) as khelben mentions? If so, would I be able to upgrade/downgrade/change to regular ubuntu when the drivers are out, or are we talking some sort of reinstall?

---

### Post by mastablasta on 2011-01-25
Ubuntu will automaticly install with the opensource drivers. performance might (will) not be as good as with the proprietary drivers. however the system should be fully operational and functional ( i use opensource ones on an old ATI card for which ATI dropped support). 
 
later when ATI issues LinuX drivers for this series card you can simply install them through the Hardware drivers menu. at the moment the ones found there won't support your card (it seems).

---

### Post by ste_bran on 2011-02-10
Linux drivers now available at AMD:
 [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Havent tried them yet.

---

### Post by Ifrit24 on 2011-07-31
I have the same problem, upgraded to my 6950 and now I get that black screen after the ubuntu loading screen.  I tried installing the new driver but either I am not doing that correct or it is not solving my problem.  

To install the driver so far I have tried a couple things.  I have the driver on an external HD that I mount and can run from recovery mode.  I have tried doing the standard install (#1: Install driver 8.872 on X.org 6.9 or later 64 bit) but that didn't solve my problem, so I tried doing the #2 option: Generate Distribution Specific Driver Package.  From there I picked the ubuntu option but I don't know where to save it?  I have tried just /, /lib, and /lib/modules but none of those worked.  

Any advice? 
Thanks in advance!

---

### Post by BrightEyesDavid on 2011-08-01
In case it's useful, [I ended up installing directly from the driver without creating a .deb package]("http://askubuntu.com/questions/50771/installing-catalyst-11-6-for-an-ati-hd-6970").

```
sh ati-driver-installer-11-6-x86.x86_64.run
```

---

### Post by kaldor on 2011-08-01
The 6000 series drivers should be fairly well supported by now.

---

### Post by Ifrit24 on 2011-08-01
so I tried using just sh ati.... and that didn't work, but now instead of getting a black screen im just stuck at ubuntu loading screen.  
Then i tried following [these]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") instructions to install but that didn't help either.  Any ideas?  

Thanks!

---

