---
title: "How to backup a 500gb disk with WINDOWS7 using LINUX?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by honeybear on 2011-08-20
Hi,

I would like to backup my whole harddisk /dev/sda (which has 3 partitions) into a single image file. However partimage does NOT support WINDOWS 7 : [http://www.partimage.org/Supported-Filesystems](http://www.partimage.org/Supported-Filesystems)

I mount a 2TB disk free (using SAMBA) to store this image of the /dev/sda. However which program can make it relatively fast, this whole harddisk backup?

Any solutions brought by Linux? 

Any help is welcome ... 
Regards

---

### Post by b2zeldafreak on 2011-08-20
[Clonezilla]("http://clonezilla.org/")

Personally I use the Live CD and backed up to an external hard drive. I think you can also use it from within Linux to clone partitions that aren't currently mounted.

---

### Post by honeybear on 2011-08-20
> **b2zeldafreak said:**
> [Clonezilla]("http://clonezilla.org/")

Personally I use the Live CD and backed up to an external hard drive. I think you can also use it from within Linux to clone partitions that aren't currently mounted.

man, clonezilla, seems like it cannot clone a whole harddisk !

[http://www.sevenforums.com/backup-restore/18971-clonezilla-open-source-image-backup.html](http://www.sevenforums.com/backup-restore/18971-clonezilla-open-source-image-backup.html)

:( :(

---

### Post by honeybear on 2011-08-20
Got it !!

It is now wiht clonezilla making the backup of hte whole disk even all partitions. Sounds fine.


It is much faster than partimage !! wow

---

### Post by MDguy on 2011-08-20
Clonezilla can clone an entire hard disk; when you boot into the Clonezilla LiveCD there will be a screen that lets you choose whether you want to clone a single partition or whether you want to clone the entire disk.

---

### Post by honeybear on 2011-08-20
> **MDguy said:**
> Clonezilla can clone an entire hard disk; when you boot into the Clonezilla LiveCD there will be a screen that lets you choose whether you want to clone a single partition or whether you want to clone the entire disk.

it works super.

However to mount the NFS is bit tricky, and I have to do it manually because it did not work (I typed everthg correctly)

Done !! ;) thank you clonezilla !

---

### Post by beew on 2011-08-20
Just wondering, is it true that clonezilla clones the whole partition rather than just the part that is actually used (so to clone a partition of 20G the destination has to be at least 20G even if only 5Gs have data) It seems that partimage can clone only the parts that have data but it apparently doesn't support ext4, if true that makes it pretty useless for Linux.

I am wondering if there is any tool which both supports ext4 and clones only the parts with data instead of whole partitions.

---

### Post by honeybear on 2011-08-20
> **beew said:**
> Just wondering, is it true that clonezilla clones the whole partition rather than just the part that is actually used (so to clone a partition of 20G the destination has to be at least 20G even if only 5Gs have data) It seems that partimage can clone only the parts that have data but it apparently doesn't support ext4, if true that makes it pretty useless for Linux.

I am wondering if there is any tool which both supports ext4 and clones only the parts with data instead of whole partitions.

1-I tried partimage
was long
got ok
but you have not hte whole disk. so it is worth?


2-did also clonezilla. was faster + I could clone the whole disk !



3- dd : take 2 days... more accurate but too long

---

### Post by Mark Phelps on 2011-08-21
Imaging a Cloning are different functions.

Imaging only copies off the used data on the partition; it does not CLONE the partition.

Cloning, by definition, produces a sector-by-sector copy of the original drive.

If you just want to backup a partition, use Imaging not Cloning.

Also, if you want to be able to image and restore Windows 7 partitions, why not just use the FREE version of Macrium Reflect?  That works great.

---

