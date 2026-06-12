---
title: "Dual boot problems"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-03
I just installed Ubuntu last night. It boots directly into Ubuntu and doesn't give me an option for XP as I assumed it would.  I had some issue last night with the install. It quit while partitioning. I removed the CD, so it would boot into XP after it realized there was no CD in the tray.  It would only give me an error about no CD in the tray. I changed the boot order to go to the HD 1st, but still no luck with XP.  Any help is always appreciated.

---

### Post by DGortze380 on 2009-03-03
> **js@lloyd said:**
> I just installed Ubuntu last night. It boots directly into Ubuntu and doesn't give me an option for XP as I assumed it would.  I had some issue last night with the install. It quit while partitioning. I removed the CD, so it would boot into XP after it realized there was no CD in the tray.  It would only give me an error about no CD in the tray. I changed the boot order to go to the HD 1st, but still no luck with XP.  Any help is always appreciated.

boot the live cd and post the output of 

fdisk -l

sounds like you've deleted the partitions, thus, there is nothing bootable on your HDD.

---

### Post by js@lloyd on 2009-03-03
Usage: fdisk [-l] [-b SSZ] [-u] device 
E.g.: fdisk /dev/hda  (for the first IDE disk) 
  or: fdisk /dev/sdc  (for the third SCSI disk) 
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive) 
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices) 
  ... 
ubuntu@ubuntu:~$ fdisk -l 
Cannot open /dev/sda 
ubuntu@ubuntu:~$

---

### Post by DGortze380 on 2009-03-03
interesting...

was there anything important on the drive??

My suggestion at this point is that the formatting and partitioning failed. I would reformat, repartition, and reinstall.

If you need to attempt to recovery anything off the drive, there are a number of open source tools to help you attempt to do that.

---

### Post by Michael.Godawski on 2009-03-03
hi,

it should be

```
sudo fdisk -l
```
Try again and post the output.

---

### Post by js@lloyd on 2009-03-03
To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xeb5feb5f 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda2   *           1       14593   117218241    f  W95 Ext'd (LBA) 
/dev/sda5            5743       14593    71095626    7  HPFS/NTFS 
/dev/sda6               1         249     1999998   82  Linux swap / Solaris 
/dev/sda7             250        5742    44122491   83  Linux 
 
Partition table entries are not in disk order 
ubuntu@ubuntu:~$

---

### Post by DGortze380 on 2009-03-03
ok. so your windows partition still exists. You should even be able to access it from the live cd.

Looks like you're potentially having issues with grub.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by js@lloyd on 2009-03-03
i took a look at the link. being so new, this might be a little more than i can handle.  there are a few different versions on how to fix it.  any suggestions on the easiest route for a beginner with very limited knowledge?

---

### Post by DGortze380 on 2009-03-03
> **js@lloyd said:**
> i took a look at the link. being so new, this might be a little more than i can handle.  there are a few different versions on how to fix it.  any suggestions on the easiest route for a beginner with very limited knowledge?

ok, the first thing I would do, is ensure that you have all important data backed up. You should be able to access your windows files with the ubuntu live cd. Use and external drive, or writeable cds/dvds to back up ALL important data.

The 'simplest' way to try and fix the problem is to reinstall. If you want a dual boot, do not partition the whole disk, choose your existing ext3 and swap partitions during the installation.

This is not the most elegant solution, and many people here look down upon the 'reinstall' line of advice, but it is the simplest solution if you data is backed up.

---

### Post by js@lloyd on 2009-03-03
do you mean to reinstall windows too? i have no info on ubuntu to back up, as I haven't had much of a chance to use it. xp is pretty fresh too, so there's nothing on there that i care about losing. however, i only know how to work within the windows enviornment to do a fresh install, and I can't access it now.

---

### Post by DGortze380 on 2009-03-03
> **js@lloyd said:**
> do you mean to reinstall windows too? i have no info on ubuntu to back up, as I haven't had much of a chance to use it. xp is pretty fresh too, so there's nothing on there that i care about losing. however, i only know how to work within the windows enviornment to do a fresh install, and I can't access it now.

nope, if you reinstall Ubuntu, it will do a fresh install of GRUB to your MBR.

You shouldn't have to touch your current windows install.

---

### Post by Ptero-4 on 2009-03-03
> **js@lloyd said:**
> To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xeb5feb5f 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda2   *           1       14593   117218241    f  W95 Ext'd (LBA) 
/dev/sda5            5743       14593    71095626    7  HPFS/NTFS 
/dev/sda6               1         249     1999998   82  Linux swap / Solaris 
/dev/sda7             250        5742    44122491   83  Linux 
 
Partition table entries are not in disk order 
ubuntu@ubuntu:~$

I dunno if it's just me, but from that readout it seems like your windows partition got somehow stuck inside the extended partition (i.e: it became a logical partition). The problem with this is that unlike linux, windows is very picky about which type of partition it's put on and won't load (it won't even install on) from a logical partition. Basically you'll need to either make that partition become a primary partition (which obviously it was to begin with) or move the data off it, delete it, resize the extended partition, make a new primary partition and reinstall windows (you can try resizing the "windows" partition, resize the extended partition, copy the logical partition to the unpartitioned space delete the original copy of that partition, resize the extended one all the way back and resize the newly made windows partition all the way to it's former size. But gparted probably can't copy a logical partition to space outside the extended one (I never tried doing that) an even if it can, the chances that windows will boot, run and still validate WGA/activation properly are pretty low).

---

