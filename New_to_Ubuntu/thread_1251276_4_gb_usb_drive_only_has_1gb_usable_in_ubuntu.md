---
title: "4 gb usb drive only has 1gb usable in ubuntu"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by jherskow on 2009-08-27
the title pretty mcuh says it all. its called 4.1 gb drive on the GUI. but it only shows 0.1gb of free space when it should have 3.1 (0.9 is used)

the screenshot says it all.

help?

---

### Post by nikhilbhardwaj on 2009-08-27
what do you get when you type
```
df -h /media/disk
du -h /media/disk

```
replace /media/disk with the path where your usb is mounted

---

### Post by Liolikas on 2009-08-27
```

sudo fdisk -l

```
may show interesting things too.

---

### Post by mike555 on 2009-08-27
try viewing hidden files , you might find a trash can with stuff in it ..........

---

### Post by cusinmex on 2009-08-27
> **mike555 said:**
> try viewing hidden files , you might find a trash can with stuff in it ..........

yeah.. there might be a recycle or trash folder with all
hidden files..

---

### Post by credobyte on 2009-08-27
```
sudo rm -r /media/disk/.Trash-1000

```

If it doesn't help, fire up gparted and check if there's really a 4gb partition inside your USB.

---

### Post by jherskow on 2009-09-01
> josh@JoshBook:~$ sudo fdisk -l
[sudo] password for josh: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1647b2fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 4110 MB, 4110230016 bytes
127 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      268293      517055   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(268292, 78, 21)

hat was from the sudo- fdisk

no hiddin trash cans...
t

---

### Post by halitech on 2009-09-01
looks like it only has 1 partition on it and its 1gig in size. what does Partition editor show?

---

### Post by drinkpepsi on 2009-09-01
Did you buy that drive off of ebay? I've heard they sell alot of phony drives on there. Do you have a pc running windows to see what it shows there?

---

### Post by egalvan on 2009-09-01
> **jherskow said:**
> 

Disk /dev/sdb: **4,110 MB, --- 4,110,230,016 bytes**
127 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x8ef631df
[COLOR="Red"]
This doesn't look like a partition table
Probably you selected the wrong device.
[/color]
Device Boot Start End Blocks Id System
/dev/sdb1 ? 268293 517055 979374166 66 Unknown
[COLOR="Red"][COLOR="Red"]Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(734, 123, 14) logical=(268292, 78, 21) 
[/COLOR][/COLOR]


The **bold** section seems to support the 4gig claim.

The red sections show problems with the file system.

If this has no data you need to recover, I would fully erase the drive and re-format it.

As a test, use gparted to view the drive, and post a screenshot if at all possible.

---

### Post by LewRockwell on 2009-09-01
> **egalvan said:**
> the **bold** section seems to support the 4gig claim.

The red sections show problems with the file system.

If this has no data you need to recover, i would fully erase the drive and re-format it.

As a test, use gparted to view the drive, and post a screenshot if at all possible.

+ 1

.

---

