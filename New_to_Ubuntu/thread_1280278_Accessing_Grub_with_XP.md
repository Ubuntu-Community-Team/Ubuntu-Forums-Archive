---
title: "Accessing Grub with XP"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by noxinvictus on 2009-10-01
I apologize if this is already covered but I am accessing this through my cell phone's browser which makes moving around for answers a bit tedious. And here is why:
 
In a moment of sheer genius, i decided to put XP back on my PC after a couple of years of being Ubuntu exclusive. I did so because there are a few older games and apps that dont Wine so well that I did miss playing. I formatted the petition on my computer that previously stored an older Kubuntu which I seldom accessed and put the installation of Win on it, rebooted and...yeah, Grub is gone and thus is my access to Ubuntu (9.04). It goes straight to XP.  
Could someone tell me the method of retrieving my data to access my better side?
 
Thanks.

---

### Post by rbc on 2009-10-01
Have you thought about SuperGrubDisk, to restore grub

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

---

### Post by Bradtek on 2009-10-01
How to restore Grub from a live Ubuntu cd
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by noxinvictus on 2009-10-01
> **rbc said:**
> Have you thought about SuperGrubDisk, to restore grub

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) 

 Thank you. It did return Grub to the MRB where I could effectively boot it- and easily I might add... But now XP, although there, wont boot due to some errors! Ultimately no loss, but no original plans to fruition either. Thanks.

---

### Post by LewRockwell on 2009-10-02
> **noxinvictus said:**
> put XP back on my PC after a couple of years of being Ubuntu exclusive. I did so because there are a few older games and apps that dont Wine so well that I did miss playing. I formatted the petition on my computer that previously stored an older Kubuntu which I seldom accessed and put the installation of Win on it, rebooted and...yeah, Grub is gone and thus is my access to Ubuntu (9.04). It goes straight to XP.  
Could someone tell me the method of retrieving my data to access my better side?

If you used an OEM recovery/re-install/reset-to-factory-fresh disk(s) to put XP back on your machine then it probably formatted the entire hard drive

This is the hazard of using/buying pre-installed windows and/or using these disks in an attempt to fix/recover/re-install/etc.

.

---

### Post by LewRockwell on 2009-10-02
> **noxinvictus said:**
> It did return Grub to the MRB where I could effectively boot it- and easily I might add... But now XP, although there, won't boot due to some errors!

can grub find the /boot/grub/menu.lst file?

(if it cannot then you may have fallen victim to your OEM windows re-install, as per the above post)

.

---

### Post by noxinvictus on 2009-10-02
> **LewRockwell said:**
> can grub find the /boot/grub/menu.lst file?

(if it cannot then you may have fallen victim to your OEM windows re-install, as per the above post)

.

Nope, thankfully no such event.  I would've been quite devastated had that occurred.  GRUB was successfully restored and I could access Ubuntu with no problems whatsoever; everything is where it should be.  However, in restoring GRUB to the MRB, the WinXP from the menu will not boot.  I've tried a couple of restores of the Win partition since then and while it will boot after restart (and GRUB's disappearance), when I restore GRUB once more- Win then ceases to function.

In a nutshell, Ubuntu and WinXP just won't co-exist on my PC!

The Super Grub Restore application even has options to restore Windows to the MRB and fix it, just as with GRUB, but still I get boot errors and no XP in the outcome.  It seems as if it's one way or the other.  Clearly, if any choice exists, it wont be for messy, but it would be nice to have it as a secondary partition to play aforesaid games- but that's only of minor importance.

It might be an issue with the application itself, too.  I'm on XP end right now (3rd restore) and I'll attempt the other method of restoring GRUB as mentioned a few posts up...

Thanks for all the help, folks.

---

### Post by Johnny_Lifeson on 2009-10-02
Usually if Windoze is installed after GNU/LINUX , it seems to take everything over, nasty stuff. But if you install Windoze first then GNU/LINUX , they seem to play nice togather.

GRUB gets killed off as well, Sad...   :(

---

### Post by noxinvictus on 2009-10-02
> **Johnny_Lifeson said:**
> Usually if Windoze is installed after GNU/LINUX , it seems to take everything over, nasty stuff. But if you install Windoze first then GNU/LINUX , they seem to play nice togather.

GRUB gets killed off as well, Sad...   :(


Indeed.  Like many others first experience, mine was with Windows first and Ubuntu later- and I never had any problems with XP installed first and Linux added as a later partition.

So, I return on my fourth XP recovery.  Same end result when restoring GRUB through Live CD.  It restored it as with the application, but XP ever vigilantly fails in booting.

Here's the excuse when I try to load it:

> 

For REALTEK RTL8139(x)/8130/810x PCI Fast Ethernet Controller v2.16 (041224)
PXE-E61:  Media Test Failure, Check Cable
PXE-MDF:  Exiting PXE ROM
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER



I scratch my head in the relevancy of my nic card and the inability of Windows to boot, but its the same story each time I try to load it *after* restoring GRUB.  It works fine after a restore- no such issues with anything.  It kinda reminds me of the childish action of "Well, I'm not going to be your friend if you're friends with him!"  Bah!

---

### Post by Mercury_Alpha on 2009-10-02
Is this NIC integrated into the motherboard? If so, I recommend temporarily disabling it in your motherboard's BIOS. If it's a discrete card, remove it from the computer and see if that clears the error.

---

### Post by LewRockwell on 2009-10-02
looks like your BIOS is attempting to boot via the network

you should check your BIOS settings to make sure your boot order is the way you want it

we always set machines to boot from the optical drive first, USB devices second, and internal hard drive third

most people do not need the network boot option enabled and if yours in enabled you should unselect it

while you're at it make sure you are running the latest BIOS version for your machine

.

---

