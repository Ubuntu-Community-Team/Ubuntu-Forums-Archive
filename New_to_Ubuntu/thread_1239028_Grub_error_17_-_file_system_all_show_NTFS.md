---
title: "Grub error 17 - file system all show NTFS"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Enigman on 2009-08-13
Hi, noob here.  I have been using Jaunty and Vista in a dual boot on my laptop and today it would not boot.  I received Grub error 17.  I have booted from a live CD (Mint).  

mint@mint ~ $ sudo parted /dev/sda p
Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  143GB  143GB   primary   ntfs         boot 
 3      143GB   240GB  96.7GB  extended                    
 5      143GB   236GB  92.7GB  logical   ntfs              
 6      236GB   240GB  3973MB  logical   ntfs              
 2      240GB   250GB  10.2GB  primary   ntfs 

I also ran Gparted and did Check and Repair.  It returned an error.

I think the issue is that the file systems are all NTFS for some reason.  I believe that /dev/sda2 is the HP_RECOVERY partition.  I don't know which of the other partitions is Vista, Ubuntu, Swap or Home. <sigh>

I hope this can be fixed.  I have no idea what happened.  I really still need Vista.  I need my important saved email and I haven't gotten Ubuntu to allow my laptops sound to work (and it runs quite hot as well).

Thank you very much.

---

### Post by Hospadar on 2009-08-13
It sure looks like all ntfs.  Perhaps in windows you accidentally formatted?  I know when I accidentally double-click my linux partition in windows, windoze tells me "ZOMG this is not formatted?!?! You wants me format it?!?!?"  and I've almost wiped many an install.

If all signs say that everything is ntfs, it may in fact all be ntfs.  I'd say if there was nothing too critical in your linux installation, pop in a livecd and re-do it if you are unable to get at the data.

If you just want to get at vista to back up your important data before you go monkeying with partitions, I'd pop in a vista cd, and do a fixmbr from the recovery console.  

What it seems like probably happened is:
(MBR is the drive's master boot record)

New computer->Vista installed, windows boot loader in MBR->Linux installed, grub goes in MBR, grub can boot windows->Linux partition damaged, grub can't start, can't boot windows->Presumably windows partition is still good, just needs MBR fixed, so either re-install or fix linux or restore windows boot loader to MBR.

---

