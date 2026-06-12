---
title: "Possibility of restoring previous grub2 bootloader?"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by elnehi on 2010-09-27
Ok, I'm a newcomer to Ubuntu, even though I'm a rather experienced computer user. I had a nice working edition of Ubuntu 10.04 Netbook remix (installed from a flash drive) running on an 8GB SD card on my HP Mini. I decided to try out the beta of 10.10, so I installed 10.04 to a separate 4GB SD card and upgraded within the OS, which of course overwrote my previous grub2 bootloader. I am just wondering if there is a way to go back & restore the grub2 bootloader for the 8GB SD install of 10.04, since I know of no other way to access it at this point. I do have a USB SD card reader that I could use to access the 10.04 install on the 8GB card while 10.10 is running on the 4GB card, if need be. By the way, I'm running a dual-boot with Windows 7 Pro on the 16GB internal SSD ('nuff said). Thanks for any help you can provide!

---

### Post by The Cog on 2010-09-27
If you can get back too the previous 10.04 (hopefully, the 10.10 bootloader gives it as an option) then you can just run **sudo grub-install /dev/sda** or whatever drive you want to reinstall the old grub to. Then **sudo update-grub** to get the old bootloader to offer the 10.10 boot as an option.

If you can't directly boot 10.04, you can use the alternate install CD and choose to rescue a broken system. Then specify your 10.04 root as the root to rescue, and install grub as above.

---

### Post by elnehi on 2010-09-27
I cannot access the previous 10.04 install from the bootloader because I swapped out the SD cards (using the same internal card reader) to reinstall 10.04 on the 4GB card, which overwrote my old bootloader with a new one.  When I try to boot using the 8GB card (with the old 10.04 install), it goes to a screen with:
 
error: no such device: 93df4002-6b7a-4582-9a42-62c183c5c38f
grub rescue>
 
It will not take any commands there that I try to type in.  
 
Also, I am not sure if by "alternate install CD" you mean the media I used to install Ubuntu.  As I stated, I used an image installed to a flash drive.  As far as I can see, it does not give the option to rescue a broken system.  It gives options to Run from the drive or Install to a Hard Drive, things like that.  It has an Advanced Options with what looks to be a sub-menu, but there are no options listed in the sub-menu section.  Perhaps there is a way to rescue from within the OS running from the flash drive?  I am uncertain.

---

### Post by The Cog on 2010-09-27
When you installed Ubuntu, you booted from a USB stick, right? This USB stick was created from a CD image - the Desktop installer CD. Well, as well as the Desktop installer CD, there is an "alternate" installer CD. If you can make a bootable USB stick from that, it will give you the option to repair a broken system, at which point you can specify your 8G SD as the root filesystem and then run grub-install. 

What I am describing is really the section "Recovery Using the Ubuntu Alternate/Install CD" from this document:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
which also describes how to reinstall the bootloader from the normal desktop installer CD. Yes I know you are using USB strik instead, but I think the steps are the same once you have managed to make the bootable USB stick from the CD image.

---

### Post by elnehi on 2010-09-28
Okay, I got the Alternate Install image put on the USB drive and selected the option to Repair a broken system.  It goes to the following line:
 
[      1.006461]  [<c0104007>] kernel_thread_helper+0x7/0x10
 
It then hangs while the caps lock light blinks on & off (that's a new one).  Any suggestions?
 
By the way, on the link you gave for the instructions, it says to type "rescue" at "boot:" to attempt to fix the problem.  I tried that route, but it never came up with a "boot:" prompt.

---

