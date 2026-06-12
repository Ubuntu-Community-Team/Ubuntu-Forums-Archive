---
title: "Boot: Could not start the X server"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by kux on 2009-11-16
I was running a file operation - transferring files from my USB to an SD disk when the operation froze my machine. I had no choice but restarting the hard way (power button for 5 sec). Now I get this message on startup before I get to the login screen:
[INDENT]Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog dialog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.
[/INDENT]I can get to my GUI in RECOVERY MODE, but this takes a good 5 or 10 min - and I hope is not my only solution. 

I'm running:
EeePC 901
EEEbuntu (with Ubuntu 9.04)
Bios 2.6.30-02063004-generic
Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Graphics: Intel Mobile 945GME Express Integrated Graphics Controller (rev 03)
& Subsystem: ASUSTeK Computer Inc. Device 830f

Also I have no knowledge of terminal commands or how the filesystem works - so if your instructions could be very detailed it would help, thanks!

---

### Post by The Cog on 2009-11-16
In recovery mode, do you get a root ("#") prompt?

If so, try the command **fsck** and see if that helps. It's a filesystem consistency check/repair.

---

### Post by dca on 2009-11-16
Not to add to the injury but your fs may be hosed due to ext4 optimizations to make system run faster on desktops and on SSDs...
 
[http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html](http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html)

---

### Post by blazemore on 2009-11-16
If you can, boot from a LiveCD. (Or if you can, just do this first step on your system) Then open a terminal and type sudo fdisk -l
Post the output here.

---

### Post by philinux on 2009-11-16
> **The Cog said:**
> In recovery mode, do you get a root ("#") prompt?

If so, try the command **fsck** and see if that helps. It's a filesystem consistency check/repair.

+1.

If your root file system is on say /dev/sda1 then you would run

fsck -v /dev/sda1

From the recovery mode command prompt. You'll have to unmount the filesystem first.

---

### Post by blazemore on 2009-11-16
Yes, that's why I asked him to do sudo fdisk -l so we can see which one needs to be checked.

In other news, 1000 beans!

---

### Post by kux on 2009-11-16
blazemore: After running sudo fdisk -l this was my result:

/Disk /dev/sda: 4034 MB, 4034838528 bytes
128 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x58d1ca06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         968     3902944+   7  HPFS/NTFS
/dev/sda2             969         976       32256   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         933     7494291   83  Linux
/dev/sdb2             934         981      385560    5  Extended
/dev/sdb5             934         981      385528+  82  Linux swap / Solaris


philinux: What's the default directory for my root file system? How would I go about 'unmounting' my filesystem?

dca: I've been using this setup for about 4 months now with almost no problems... hope it's not hosed now...

The Cog: I believe I can get to the root prompt.  FSCK is one of the options given in the Recovery Mode boot screen.. I've tried all of those options except for the ones pertaning to GRUB.. with no effect on my normal boot - if you ask I can try to get a list of everything that FSCK tells me... FYI just tried to run FSCK and it tells me: 

WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

So I opted against it...

---

### Post by blazemore on 2009-11-16
Yes, to run fsck you'll have to boot from a LiveCD.
But do what you did, just do if from a LiveCD. And don't run fsck on a mounted filesystem!

---

### Post by The Cog on 2009-11-17
> **dca said:**
> Not to add to the injury but your fs may be hosed due to ext4 optimizations to make system run faster on desktops and on SSDs...
 
[http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html](http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html)

Agreed. In my limited experience, if an ext4 system crashes you have a 50% chance of the filesystem being so badly mangled that a reformat and reinstall is the only option. When GRUB complains "Invalid extent" then you're really up against it.

---

### Post by kux on 2009-11-17
blazemore: Because I have two SD disks that run XP and Ubuntu seperatley, could I mount my 4GB that runs XP and then run FSCK from there?

Also, how do I know that when I run the Live CD (from my FlashDrive) that I won't be also mounting my Ubuntu partition when I run FSCK?

---

### Post by kux on 2009-11-19
I figured out removing an SD card from my SD port enabled a normal boot. 

Why I can't boot with an SD card in the slot is still beyond me. 

I assume that something happened during the file transfer interruption between a USB Flash Drive and my SD card that causes this problem. 

Any known solution?

---

