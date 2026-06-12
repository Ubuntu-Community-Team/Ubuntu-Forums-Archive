---
title: "dual boot problem"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by denizente on 2011-04-25
Hi. I installed Ubuntu from the CD but first had to adjust partitions using GParted to give dual boot with Windows. So far so good, everything working on both OSs - but I wanted to get rid of Windows partition completely & tried to use GParted to to this - but don't seem to have succeeded.

I have since found that a couple of applications I use only run on Windows anyway (I've never had much luck with Wine...), and want to revert to dual boot if possible. 

So:  I want to make it a dual boot machine again, but can't see in GParted how to do this (don't even know if it's possible).  I can get Windows to start with various errors (mainly concerning the D drive), and no applications apprearing.

The details from GParted are:

/dev/hdb   is split into /dev/hdb5 (ext3) ; /dev/hdb6  (linux-swap)  &  unallocated

/dev/sda    is split into:

/dev/sda/3 (also split dev/sda5 (ext3) and /dev/sda6 (linux swap)
/dev/sda1 (NTFS) HDD
unallocated
/dev/sda2 (NTFS) DATA
unallocated




Does this make sense to anyone? I appreciate it's not 100% Ubuntu-related & that I may get sent endless links instead of an answer, but it made sense to try this forum rather than any Windows-related forum. Hope someone can help,

Many Thanks

---

### Post by oldfred on 2011-04-25
If your sda1 is formated to NTFS, is large enough and has the boot flag, window should just install to that partition. Do you still have boot flag on sda1? Grub does not use boot flag, but windows has to have it to directly boot, make repairs, or install.

Windows will install its boot loader into the MBR. You need the Ubuntu liveCD to reinstall grub or more likely now grub2. Make sure you know which version of grub you have as the instructions are different and trying to install the wrong one makes it worse.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by denizente on 2011-04-25
Thx for quick response. Yes, SDA1 has the boot flag. It has 29GB available, 22GB of which has been used. Does that mean there's enough space for windows to reinstall itself?

NB Will reinstalling Windows wipe Ubuntu off my machine or will it stay as dual boot when I reinstall Windows?

Cheers

TC

---

### Post by oldfred on 2011-04-25
Windows does not see the Ubuntu partitions.It should not delete Ubuntu, but sometimes it writes partition table wrong and repairs have to be made.

You will have to reinstall the grub bootloader as posted above.

---

