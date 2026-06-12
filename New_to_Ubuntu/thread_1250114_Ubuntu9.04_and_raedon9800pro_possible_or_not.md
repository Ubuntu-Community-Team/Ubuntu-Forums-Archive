---
title: "Ubuntu9.04 and raedon9800pro possible or not?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by gizmopower on 2009-08-26
Hello all! 
First, sorry if I am posting in the wrong section!

This is my first post and I want to point out that I am a comlpete noob to linux. :confused:
I have innstalled Ubuntu 9.04 on one of my desktops and like it a lot, a great os.
I´m looking around and trying to learn about it, specially the terminal window and it´s commands. I have only done a little Telnet with dreambox.

So to my question...

Can I, or can I not get my ATI Raedon 9800pro working with Ubuntu9.04
I tried with the driver: "ati-driver-installer-9-3-x86.x86_64.run" from amd homepage
My system is 32bit.

I have found a lot of postings about this, but many are outdated or confusing.
Like the tutorial with Ubuntu 8.10, it will not work in same way with 9.04 because of changes with kernel...?
Also I saw a list of what is needed to install the driver:

> 
Before attempting to install the ATI Proprietary Linux driver, the following software
must be installed:
• POSIX Shared Memory (/dev/shm) support is required for 3D apps
• glibc version 2.2 or 2.3
• Linux kernel 2.6 or higher
• XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
> 
The following packages must be installed in order for the Catalyst™ Linux
driver to install and work properly:
• XFree86-Mesa-libGL
• libstdc++
• libgcc
• XFree86-libs
• fontconfig
• freetype
• zlib
• gcc
Are theese packages alleredy in the Ubuntu 9.04 release or do I have to install them?


Hoping for some answers.
Tanx!

GizmoPower

---

### Post by 3rdalbum on 2009-08-26
The current ATI Catalyst driver does not support the Radeon 9800, and the last driver that supported the 9800 does not work on Ubuntu 9.04.

You have three options:

1. Use the open-source ATI driver on Ubuntu 9.04 (this driver is active by default). Pros: Requires the least amount of work and no expense. Cons: You might not have 3D support (depends on the card), if you do have 3D support it won't be especially fast.

2. Install Ubuntu 8.10 and use the old driver. Pros: You have moderately-good 3D support (the ATI driver doesn't have very good performance). Cons: You're stuck with old software, and no upgrade path, and you won't system updates after April next year. And 3D performance won't be *that* great, because ATI's driver is not very good.

3. Buy a new graphics card. If you have a PCI-E slot in your computer, you can install any new graphics card. If you don't have PCI-E, then you will have an AGP slot and you will have to hunt around for the Powercolour ATI cards with AGP, or an older Nvidia from the 6xxx or 7xxx series. Pros: You have an upgrade path and you may see better performance. Cons: You have to spend money, and the earlier Nvidias with AGP sometimes require a bit of xorg.conf hacking from what I hear.

Okay, so it's up to you, but Ubuntu is completely usable on a Radeon 9800, even without the proprietary driver. Unless you don't have 3D acceleration and you need 3D for what you want to do with your computer, then I'd recommend just sticking with the open-source driver on your current card.

---

### Post by 3rdalbum on 2009-08-26
For anyone else who might be interested, Ubuntu comes with everything on that "required" list, except gcc and kernel headers (the latter is not on that list, but is still required). You can get both these things by installing the "build-essential" and "linux-headers-generic" packages from Synaptic.

---

### Post by gizmopower on 2009-08-26
Tanx for answering! :)

If I revert to the Xorg intel driver 2.4 and install the latest working driver, wich is "ati-driver-installer-9-3-x86.x86_64.run"
Would it work?

I´ve read that someone solved it that way. 

And it still says in the Ubuntu documentation:
> 
**Accelerated 3D support (r300, r400 and r500 series)**

 All these cards and derivatives have good 3D acceleration support 

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
[COLOR=Blue]9800 / R350 or R360 based cards[/COLOR]
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
Xpress 200 / RS480 IGP
Xpress 200 / RS482 IGP for Intel
Xpress 200M / RS482 IGP
Xpress 1100 / RS482 IGP
Xpress 1150 / RS485 IGP
Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

Tanx!
Gizmopower

---

### Post by Mark Phelps on 2009-08-26
> **gizmopower said:**
> Tanx for answering! :)

If I revert to the Xorg intel driver 2.4 and install the latest working driver, wich is "ati-driver-installer-9-3-x86.x86_64.run"
Would it work?

I´ve read that someone solved it that way. 

And it still says in the Ubuntu documentation:

Tanx!
Gizmopower
Yes ... it could work, but the posts from folks who have tried that indicate that they then have other problems, notably, kernel-related problems.

Just hope that if you're going to start messing around with your XServer, you at least do a backup first.

---

### Post by embiggened.badger on 2009-08-26
Good luck with this issue, **Gizmo**. When I first installed Ubuntu less than a week ago, my system was still built around an ATI Radeon X1950 Pro chipset. ATI is somewhat notorious for failing to provide the comprehensive level of support for Open Source software (i.e. Linux in general) for which their chief competitor, nVidia, is now well-known.

On that note: If you decide to go looking for an alternative graphics card, I can recommend any card based within nVidia's GeForce 9xxx series for its ease of installation and use. I picked up an nVidia GeForce 9400 GT last night, and all I had to do was plug the darn thing into my PCI Express slot. Voila - instantly compatible solution.

---

### Post by gizmopower on 2009-08-26
Ok i did it! reverted the Xorg intel driver to "2.4" Wohoo!
I have run glxgear and got: 5712 frames in 5.0 seconds = 1142.288 FPS
How does that sound? Bad?

Question:
Should I now install.. the "ati-driver-installer-9-3-x86.x86_64.run"  ?
The version now is: 8.54.3

Tanx!
Gizmopower

---

### Post by gizmopower on 2009-08-27
> **embiggened.badger said:**
> Good luck with this issue, **Gizmo**. When I first installed Ubuntu less than a week ago, my system was still built around an ATI Radeon X1950 Pro chipset. ATI is somewhat notorious for failing to provide the comprehensive level of support for Open Source software (i.e. Linux in general) for which their chief competitor, nVidia, is now well-known.

On that note: If you decide to go looking for an alternative graphics card, I can recommend any card based within nVidia's GeForce 9xxx series for its ease of installation and use. I picked up an nVidia GeForce 9400 GT last night, and all I had to do was plug the darn thing into my PCI Express slot. Voila - instantly compatible solution.

Tanx for the info! :D

I do have two Nvidia: 9600gt and 7600gt but they are in use in my Other two pc´s
But I´m nerly there I think, just need to go a step back again!


Q:
I updated the driver to 9.3 and now Ubuntu reboots when running glxgears
Does anybody know how I could go back to the previous driver: 8.54.3


Tanx!
GizmoPower.

---

### Post by Mark Phelps on 2009-08-27
> **gizmopower said:**
> I updated the driver to 9.3 and now Ubuntu reboots when running glxgears
Does anybody know how I could go back to the previous driver: 8.54.3

You would have to remove the current drivers and reinstall the older drivers from an ATI download.

I was hoping that you would succeed, but as I had already mentioned, others who have tried the same thing have also failed.

---

### Post by gizmopower on 2009-08-28
> **Mark Phelps said:**
> You would have to remove the current drivers and reinstall the older drivers from an ATI download.

I was hoping that you would succeed, but as I had already mentioned, others who have tried the same thing have also failed.


Well it looks like I have succeed after all! :D
I dl Nexuiz and it runs quite ok!

That was reverting to the Xorg intel driver 2.4 and install the latest working driver, wich is "ati-driver-installer-9-3-x86.x86_64.run"

I will se  if I can get som fps from the game, but I dont know what I should be aming at with my poor card!

What do you think?
And how can I see the frames in game?

Tanx again for support! :D

GizmoPower

---

### Post by 3rdalbum on 2009-08-28
I can't understand why you downgraded an Intel graphics driver. I thought you had an ATI Radeon 9800, not Intel graphics.

---

### Post by gizmopower on 2009-08-28
Good question.
I don´t either..
I just read that making old ATI (Like mine raedon9800) work with Ubuntu9.04 one solution was reverting the Xorg intel driver to "2.4"..
Been googling the net for a couple of days to find solutions.
I have only had Ubuntu for three days now and never touched Linux except some file transfer and telnet with Dreambox!

I have confirmed that it workes cus now i was able to install 9.3 drivers and enter Catalyst to performe changes. 3D games is a fact, it runs..
Before the downgrade it was impossible to install anything!


GizmoPower

Edit: Could some please provide me the ati driver 8.54.3 that came priinstalled in Ubuntu 8.10?

---

### Post by Mark Phelps on 2009-08-28
Congratulations!!

You may be the first person who has been able to make this work.  You should think about adding a tutorial to that subforum.  I'm sure LOTS of folks would like to know how to do what you did so they can get back to using restriced ATI drivers.

The link below is to ATI legacy drivers:  

[http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx")

---

### Post by gizmopower on 2009-08-28
I found a tutorial a bit different from others on the net!
I will post in tut. sub.

Tank you for youre support!!

---

