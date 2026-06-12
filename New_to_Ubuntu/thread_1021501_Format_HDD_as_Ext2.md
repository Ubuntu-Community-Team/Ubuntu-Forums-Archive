---
title: "Format HDD as Ext2"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2008-12-25
How do I format a harddisk as ext2 format?

Thanks for any help.

---

### Post by nhasian on 2008-12-25
you can use gparted in the System->Administration->Partition Editor.  if its not there you can install it with:

```
sudo apt-get install gparted
```

---

### Post by jimmy the saint on 2008-12-25
Just use gparted.  Make sure that you are formatting the correct disk.  You will need to create a new partition, which can be the whole drive.  I repeat: MAKE SURE YOU FORMAT THE CORRECT DRIVE!  It is advisable to make a good backup before doing anything to the partitions just to be safe.  Good Luck!

---

### Post by 73ckn797 on 2008-12-25
> **arnold.pietersen said:**
> How do I format a harddisk as ext2 format?

Thanks for any help.
If you have the Live CD, boot from it. Go to System/Administration/Partition Editor. From there you can designate the format type of the selected drive. If you have Partition Editor installed and are wanting to format another drive in the system, the procedure will be the same.

---

### Post by taurus on 2008-12-25
And of course, you need to unmount the drive first if it's already mounted before you can do anything with gparted.

---

### Post by billgoldberg on 2008-12-25
And make really sure you want to use ext2, it isn't a journaling file system!

---

### Post by arnold.pietersen on 2008-12-27
Hi Everyone

Thanks for the advice.  I will certainly try it with another HDD.

The problem stems from the fact that I was upgrading to 8.10 from 7.04.  The external HDD which I wanted to use for the backup came up as read-only and was thus locked.  Having tried various options, I thought I'll format the hard disk as ext2. At one stage I took out the USB cable of the HDD without unmounting. I plugged it in again and the read-only was gone and I could back up to the HDD.

Thanks once again.

---

### Post by -kg- on 2008-12-27
First read the information at:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I personally would format the drive as ext3, which is a journalling version of the ext(x) format.

> And of course, you need to unmount the drive first if it's already mounted before you can do anything with gparted. 

Exactly.  You won't be able to do any operations on the partition without unmounting it...you'll basically be presented with a couple of options from the menu (not the one you will want), including the "Unmount" option.

---

