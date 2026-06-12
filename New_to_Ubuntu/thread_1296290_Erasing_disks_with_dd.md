---
title: "Erasing disks with dd"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Boris-- on 2009-10-20
Hello,

I'd just like to know how to do this and how long does it take (I have a 300 gig SATA drive and a normal 120gig drive). The reason is not being able to install any windows after formatting my win7 drive. Ubuntu works fine but I need XP for work.

Thank you for your time!

---

### Post by petersohn on 2009-10-20
You want to erase the full disk? You probably won't need that. If you want a "clean" disk, boot from a live CD, run gparted and delete all partitions. It will be done pretty fast, and you don't need to null out all data for that.

EDIT: Well, if you have your Ubuntu on different drive than the Windows, then you don't need the live CD.

---

### Post by prshah on 2009-10-20
> **Boris-- said:**
> 
I'd just like to know how to do this and how long does it take (I have a 300 gig SATA drive and a normal 120gig drive).

You can just erase the MBR+partition table, and the whole disk will _appear_ blank; it will take about half-a-second. 

If you want to erase the entire disk, the exact time will vary; but you can take a (rough) estimate of 1.7Gb/min.

To erase just MBR+partition table```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1
```

To erase (zero out) everything```
sudo dd if=/dev/zero of=/dev/sdX bs=64M conv=noerror [color=red]oflag=direct[/color]
```

Notes:[indent]-In both cases, replace /dev/sdX with the actual drive device of the drive you want to erase. Note DRIVE, not partition, so please don't use eg, /dev/sdX9.
-This is a highly risky procedure, so you do this at your own risk. One misspelling or misplacement will vanish your data instantly.
-In the second command, the part in red can be omitted to gain some speed
-In the second command, you can play around with the "bs" parameter; some people report better results with 16M, some with 32M and yet some with 64K... go figure.
-At your own risk only. (Repeated to stress importance).
[/indent]

---

### Post by LewRockwell on 2009-10-20
Parted Magic LiveCD Utilities Disk has a nice erase disk function!

check it out!

[http://partedmagic.com/](http://partedmagic.com/)

.

---

### Post by Boris-- on 2009-10-20
Thank you for your replies, alot!

The problem is really that I can't install wins xp (need for work) on this computer after formating win7 partiton. I know this doesn't belong to this forum but I am trying to fix my computer for a week now with no success.

Here is the problem:

I have used dd to erase my disk, and ubuntu to make a ntfs partition on it. I have tried three different windows xp CDs (one original and 2 backups) and none detect my partition before setup (unknown partition (raw)) or something like that. I didn't go through with making a new one but when I make a new partition in the setup i usually get "error loading os".

Also I can't make a new partiton in setup on my SATA 300gig disk (I have 2 disks, 300 - master and 120 gig -slave). I can only install wins on the 120g IDE disk.

Since I'm not really the most knowledgeable guy in computer history I hope that this makes sense. 

Thanks for your time and have a nice day!

Thank you again for your time!

---

### Post by Daveski on 2009-10-20
Does XP say that it cannot detect a mass storage device? If so, then the old 'kernel' used for XP insall cannot talk to your disk controller without a driver (the old 'Press F6' during setup).

---

### Post by SkyNet2029 on 2009-10-21
Part of the problem may actually be in the physical layout of your hard rive arrangement. Xp needs to be installed to a Master drive, not slave drive. You can get around this limitation by disconnecting your Master and leaving the slave connected as if it were the primary drive. Install xp and it should boot from there.
As to the (RAW) on your disk in partitiioning: If the disk is labeled as RAW it means that no filesystem is in place on the disk. You will need to use the XP disc to format the (RAW) to NTFS for it to be recognized by the install disc.

---

### Post by DGortze380 on 2009-10-21
In addition to previous suggestions...

Windows must be installed to the first primary partition.

Also, you may want to try creating a FAT32 partition instead of NTFS. My my experience XP detects FAT32 more often than NTFS. You can then use the XP installer to reformat to NTFS before installing.

---

### Post by Boris-- on 2009-10-21
I will try to unplug SATA drive / make FAT partition. I will report back to let you know how it went.

Thanks for your help, without you guys I'd be lost or at least paying alot to a computer repair service :)

Have a nice day!

---

