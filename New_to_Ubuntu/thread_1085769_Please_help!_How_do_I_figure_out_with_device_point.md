---
title: "Please help! How do I figure out with device points to which drive"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by seepage87 on 2009-03-03
I've got 7 HDs in my computer, 6 in a RAID6.  One of those drives (/dev/sdb1) has issues and I need to send it back to Seagate to get a new one.  Except I have no idea which physical drive is sdb.  How can I figure this out?

It might be worth noting that the device allocations seem to change if I add or remove drives.  I think my drive that's not on the array used to be sda and now it's sdg.

I'm sure there's an easy way to have it display which port it's connected to or something, but I have no idea and I think I may have irreparably destroyed my array trying to fix this, so I'd like it to not happen again.

Thanks in advance.

---

### Post by Het Irv on 2009-03-03
I can't think of way to list the physical port in Ubuntu (I am not saying the option doesn't exist, I just don't know it).  How are you getting the notification that the drive is bad?  One way to find the offending drive might be trial and error, removing the drives one at a time, but I wouldn't want to do that... too much like work.

Drive are usually numbered in their physical order, so I am gonna take a guess and say that the first Drive in RAID (slot 0 or whatever) is the one you are looking for.  Of course if RAID doesn't follow the usual pattern then I am out of Ideas.

---

### Post by Coreigh on 2009-03-03
First question do you have seven disks, or seven partitions?
In a terminal print the disk and partition listing with the following command:
```
sudo fdisk -l
```
and copy and post the results back here that will spell out how many disks and partitions you actually have.

Assuming for a moment that you in fact have seven disks they are ordered alphabetically. Disk #1 is /dev/sda, disk #2 is /dev/sdb etc. Disk #1 is 'the first disk on the primary controller.' For example if you have your primary boot disk on the built-in controller on the mother board (and the CD-ROM on the secondary) and any other disks on an add-in card (not build in to the mobo) sda is the boot hard drive and sdb is the CD-ROM. If the you have a second hard disk that is slave to the boot disk then the slave disk will be sdb and the CD-ROM is sdc. So starting at the primary controller with the first disk you have sda, then the next disk found becomes sdb. The "next disk" may be on the primary, the secondary, or way out on the add-on card, where ever it is the "next disk" gets the "next letter."

The controllers will be labeled as primary (0), secondary (1), and so on (3), (4) etc. The master disk is disk 0 the slave is disk 1 on each controller. So all you have to do is identify the controller order and count your way out to sdb (the second disk in the system).

This can get more complicated when the controller support more than two disks and SCSI is slightly different but you can still get there.

Going back to the "sudo fdisk -l" to list your partitions you should still do that so you can identify if you will lose more than that one (sdb1). If the disk only has the one partition then you're good to go, but if there is an sdb2 and sdb3 or more you will mant to identify those mount points and back up that data.

---

### Post by seepage87 on 2009-03-03
I in fact have 7 disks and my system is booting off of sdg for some reason (I may have set it to do so in my bios a while back, I don't remember).  I actually got a good answer from the linux user group at my alma mater, who suggested:

```
smartctl -d ata -a /dev/sdb | grep Serial
```

which I hear will return the serial number of sdb.  I think glancing at the serial numbers and checking if they match is little enough work for me.

---

