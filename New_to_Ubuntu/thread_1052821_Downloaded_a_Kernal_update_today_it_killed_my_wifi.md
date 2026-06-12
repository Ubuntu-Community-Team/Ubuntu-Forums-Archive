---
title: "Downloaded a Kernal update today it killed my wifi."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-28
LOL Please help!


I downloaded the Kernal update today that the system said I needed and after I did this my laptops WiFi no longer worked!

I'm extremely heartbroken because I worked my butt off to find a solution to get it to work in the first place...

I have an Atheros ar242x internal wifi card,  Needless to say I just sat there speechless and stunned after this happened first thing in the morning.. it took me days to find a fix that worked for this...

Could someone please explain to me what happened when the update took effect that caused this?

Do I need to try and re-install the mad-wifi fix that got it working in the first place?  I am using Intrepid 8.10.........

I'm still in shock over this........especailly as hard as I worked to get it running.

---

### Post by 3rdalbum on 2009-01-28
Short answer: Yes. For various reasons, the kernel's binary interface keeps changing for almost every new kernel version. For every third-party driver you compile, you are actually compiling it for that specific kernel version that you are running. When you update the kernel, it cannot use the old driver - you must recompile the driver to match your kernel.

If you were using drivers that are present in Ubuntu's repositories, then you wouldn't have this problem as Canonical always recompiles Ubuntu's drivers to match the updated kernels, and pushes them out as updates at the same time.

Stinks, yeah; but it's done for some good reasons, and you don't always have to recompile your modules again. You only need to recompile when there's an "ABI bump". Which is pretty often, granted, but last time I installed a new kernel it didn't bump the ABI and my good wireless driver continues to work.

Surely the procedure for installing the new driver wasn't really that tough? I expect much of the groundwork (installing build libraries and kernel headers, downloading the driver's source code) is already done.

-----------
EDIT: AR242x, you say? Did you try the "ath5k" driver that's available in the "linux-backports-modules-generic" package? Install that package and type "sudo modprobe ath5k", or in the file "/etc/modules", add the word "ath5k" to the bottom of the file and reboot.

---

### Post by cptrohn on 2009-01-28
> **3rdalbum said:**
> Short answer: Yes. For various reasons, the kernel's binary interface keeps changing for almost every new kernel version. For every third-party driver you compile, you are actually compiling it for that specific kernel version that you are running. When you update the kernel, it cannot use the old driver - you must recompile the driver to match your kernel.

If you were using drivers that are present in Ubuntu's repositories, then you wouldn't have this problem as Canonical always recompiles Ubuntu's drivers to match the updated kernels, and pushes them out as updates at the same time.

Stinks, yeah; but it's done for some good reasons, and you don't always have to recompile your modules again. You only need to recompile when there's an "ABI bump". Which is pretty often, granted, but last time I installed a new kernel it didn't bump the ABI and my good wireless driver continues to work.

Surely the procedure for installing the new driver wasn't really that tough? I expect much of the groundwork (installing build libraries and kernel headers, downloading the driver's source code) is already done.

-----------
EDIT: AR242x, you say? Did you try the "ath5k" driver that's available in the "linux-backports-modules-generic" package? Install that package and type "sudo modprobe ath5k", or in the file "/etc/modules", add the word "ath5k" to the bottom of the file and reboot.

LOL Yes it was actually pretty tough for me anyway(completely new to anything Linux and how it all works).. I beleive the package you stated was the one that I installed before, Thank you for the answer though... I will run it all again..

---

### Post by 3rdalbum on 2009-01-28
> **cptrohn said:**
> LOL Yes it was actually pretty tough for me anyway(completely new to anything Linux and how it all works).. I beleive the package you stated was the one that I installed before, Thank you for the answer though... I will run it all again..

The new kernel may have just wiped out your /etc/modules file - see if "ath5k" is in there. If not, add it and you should get your access back.

---

