---
title: "Nvidia Fx 5200 problems newbi needing alot of help!?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Kite4_20 on 2009-01-21
Hi I have read alot of post and tried everything, i know how to so i need help now.
I have a compaq:
2.5ghz,1.5gigmem,20hd.
When I installed ubuntu it was a mess with either way cd, text, or windows.
When it tried to boot up it would hang so I learned to get to a terminal, did the apt-get udate and upgrade, after that I could login like a normal boot, that took me three days of about 16hrs a day to figure out. Now I have tried multiple ways to install the nvidia drivers, envyng-no go, hardware driver program to install the restricted drivers, and manual install, tried to edit my xconfig file.

So this is what happens when they are all loaded sometimes i am able to boot into the rescue menu, the dkpg, fsck, then select resume normal boot.
It will let me in and run as if the drivers and xserver is working. Try to reboot to a normal startup, I get the Ubuntu splash screen, the crash different problems, blank screen with blinking courser.  Alt-f1 drop to prompt, but I don't know where to look to find the error log.  This would help me alot in figuring out what I am doing wrong. Any suggestions let me know!

---

### Post by gettinoriginal on 2009-01-21
First, I have some questions.  Did you acquire it or burn it??
When you first tried the disk, did you immediately install, or "try ubuntu without installing".  If you did, did it work??  It sounds to me like you may have a bad Live CD.

---

### Post by Slim Odds on 2009-01-21
I have 2 systems running 8.04 with FX5200 cards.

I've never had any problems. Just selected the proprietary driver from the menu. Compiz is great.

---

### Post by Kite4_20 on 2009-01-21
I burned an iso image, used winsum to check the file system it checked out, also i am on 8.10, no the ubuntu would not load off the cd but i think that is cause I tried it with my nvidia card. I am in ubuntu now but running off the mobo intel chip set.

---

### Post by gettinoriginal on 2009-01-21
Go to System, Administration, Software Sources and make sure the first 4 boxes are checked.  This will allow the installation of restricted (proprietary) drivers such as Nvidia.  :p

---

### Post by Kite4_20 on 2009-01-21
i have done this and downloaded to comp nvidia pakgs 173.xx, but I am currently running of my mobo video out intel chip. This is what happens when I enable the restricted drivers. I enable them then it askes for a reboot, at boot up I go into bios and select pci as my video adapter save changes to cmos then boot, I know there are problems.  Hangs on the boot splash screen and halts the system, when I hit alt-f1 to watch it about two or three seconds into the boot one or to fail can't read it, then alot of red writing. How do I capture that stuff so I can read it and find out what the conflict is?

---

### Post by Slim Odds on 2009-01-21
> **Kite4_20 said:**
> ....I enable them then it askes for a reboot, at boot up I go into bios and select pci as my video adapter save changes to cmos then boot, I know there are problems.  Hangs on the boot splash screen and halts the system, when I hit alt-f1 to watch it about two or three seconds into the boot one or to fail can't read it, then alot of red writing. ....

Is your card PCI?   Both of mine are AGP.

---

### Post by Kite4_20 on 2009-01-21
Mine is a pci nv34 GeForce FX 5200 rev a1

---

### Post by abyssius on 2009-01-21
> **Kite4_20 said:**
> I burned an iso image, used winsum to check the file system it checked out, also i am on 8.10, no the ubuntu would not load off the cd but i think that is cause I tried it with my nvidia card. I am in Ubuntu now but running off the mobo intel chip set.

I had a FX5200 card working fine on 8.04lts, when I upgraded to 8.10 it refused to work reliably. I believe that the problem had something to do with an incompatibility with the restricted drivers and the version of X.Org included in 8.10. I spend an enormous amount of time on this and I have yet to resolve this issue. Eventually, I elected to go back to 8.04lts until an answer can be found.

First, below is an extract from the 8.10 release notes:

> 
Upgrading

Users of Ubuntu 8.04 LTS can upgrade to Ubuntu 8.10 by a convenient automated process. Users of older Ubuntu releases need to upgrade to Ubuntu 8.04 LTS first, and then to 8.10. Complete instructions may be found at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).
nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 

Doing some more research, I discovered that some believe that NVIDIA is aware of the problem, and recommends trying their beta drivers:
[http://nxadm.wordpress.com/2008/10/31/bug-ubuntu-810-and-older-nvidia-video-cards/]("http://nxadm.wordpress.com/2008/10/31/bug-ubuntu-810-and-older-nvidia-video-cards/")

I did try the beta drivers, but I must tell you although I got the machine to work with special effects, etc, I was subjected to random screen freezes where the mouse would move, but everything else was locked up. This made my computer completely unreliable. Finally, I gave up, re-formatted, and went back to 8.04. No more problems. Personally, the differences between 8.04 and 8,10 are so slight, that IMHO it's not worth the effort with a fx5200. I think the choice is buy a newer nvidia card, or wait for the next release in three months.

---

### Post by Kite4_20 on 2009-01-21
So it looks like I should try to revert to 8.4 and try it is it very different? I am going to have to burn a new iso cd and reinstall?? or is there another way?

I don't think that I would be happy with using a card and not being able to play with 3d stuff?

---

### Post by Slim Odds on 2009-01-21
I'm with [abyssius]("http://ubuntuforums.org/member.php?u=483422")  on this one.....

I'm using 8.04 on both of the machines that have the FX5200.

You will have to download 8.04.1 (8.04.2 will be out soon).

---

