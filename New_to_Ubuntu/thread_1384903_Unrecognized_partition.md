---
title: "Unrecognized partition"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by SwiftySwerve on 2010-01-18
Hey folks,
 
I am as new as it gets, so here goes...
 
I am currently running XP and I would like to set up a dual boot. My C drive is a single partition 80GB NTFS drive. I was hoping to leave it that way. I have a second hard drive of 250GB which is partitioned into 2. One 80GB NTFS (E drive) which the XP Disk Management utility tells me is a Primary partition and one 170 GB NTFS (F drive) which seems to be an Extended partition with a logical drive.
 
After booting from the Ubuntu disk (version 9.04) I selected English for the language, US for the keyboard, EST for the time zone and then was presented with only two options for creating the Ubuntu partition: either the C drive or the F drive. I spent a few hours clearing the E drive hoping to use it as the Ubuntu boot drive but the Partitioning facility doesn't seem to see it.
 
Any ideas? I should be able to put Ubuntu anywhere shouldn't I? Any help would be greatly appreciated.

---

### Post by sandyd on 2010-01-18
> **SwiftySwerve said:**
> Hey folks,
 
I am as new as it gets, so here goes...
 
I am currently running XP and I would like to set up a dual boot. My C drive is a single partition 80GB NTFS drive. I was hoping to leave it that way. I have a second hard drive of 250GB which is partitioned into 2. One 80GB NTFS (E drive) which the XP Disk Management utility tells me is a Primary partition and one 170 GB NTFS (F drive) which seems to be an Extended partition with a logical drive.
 
After booting from the Ubuntu disk (version 9.04) I selected English for the language, US for the keyboard, EST for the time zone and then was presented with only two options for creating the Ubuntu partition: either the C drive or the F drive. I spent a few hours clearing the E drive hoping to use it as the Ubuntu boot drive but the Partitioning facility doesn't seem to see it.
 
Any ideas? I should be able to put Ubuntu anywhere shouldn't I? Any help would be greatly appreciated.
delete the E drive and leave it as free space, then when ubuntu asks for partitioning, select "use largest block of free space"

---

### Post by warfacegod on 2010-01-18
> **carlee said:**
> delete the E drive and leave it as free space, then when ubuntu asks for partitioning, select "use largest block of free space"

If his 170GB partition has 100 GB free wouldn't choosing "Use largest block..." put it in that partition instead?

---

### Post by bodhi.zazen on 2010-01-18
> **carlee said:**
> delete the E drive and leave it as free space, then when ubuntu asks for partitioning, select "use largest block of free space"

see 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

At step 8 , use the "Manual partitioning" option.

you will need to know which partition you want to install into, in Linux terminology.

[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)

---

### Post by SwiftySwerve on 2010-01-18
Thanks for responding, however, this is just my problem.  In step 8 in the attached link, my E drive is not presented as an option only the C and F drives.  Why might it not show up in the list?

---

### Post by sandyd on 2010-01-19
> **SwiftySwerve said:**
> Thanks for responding, however, this is just my problem.  In step 8 in the attached link, my E drive is not presented as an option only the C and F drives.  Why might it not show up in the list?
Open up a terminal (Applications -> Accessories -> Terminal)

Type in
```

sudo gparted

```
wait while it scans your disk, and see if the parition shows up,
You can right click on the parittion and do anything you want to it.
p.s. hint: if you have multiple hard disks, the hard disk chooser is in the top right of gparted.

p.p.s.
sorry about being highly-unnewbie friendly for the use of the terminal. i have nooo idea where gparted is in the gnome menu is since i use KDE.

---

### Post by warfacegod on 2010-01-19
> **carlee said:**
> Open up a terminal (Applications -> Accessories -> Terminal)

Type in
```

sudo gparted

```
wait while it scans your disk, and see if the parition shows up,
You can right click on the parittion and do anything you want to it.
p.s. hint: if you have multiple hard disks, the hard disk chooser is in the top right of gparted.

p.p.s.
sorry about being highly-unnewbie friendly for the use of the terminal. i have nooo idea where gparted is in the gnome menu is since i use KDE.


System > Admin.> Gparted

---

### Post by sandyd on 2010-01-19
> **warfacegod said:**
> System > Admin.> Gparted
thanks!

---

### Post by SwiftySwerve on 2010-01-19
gparted seems to recognize the partition.  I will try again and if it does not show up I guess I will format it from Ubuntu as an ext3 and see what happens.

---

### Post by sandyd on 2010-01-19
> **SwiftySwerve said:**
> gparted seems to recognize the partition.  I will try again and if it does not show up I guess I will format it from Ubuntu as an ext3 and see what happens.
if it doesn't show up, just right click on the partition and delete it. (assuming that you have no needed files on it).
then when installing, use the option "use largest block of free space"

---

### Post by sandyd on 2010-01-19
> **warfacegod said:**
> If his 170GB partition has 100 GB free wouldn't choosing "Use largest block..." put it in that partition instead?
it gives the larges unparititoned block of space

---

### Post by warfacegod on 2010-01-19
> **carlee said:**
> it gives the larges unparititoned block of space

Thanks.

I've never used the auto-magic options in an install before.

---

### Post by SwiftySwerve on 2010-01-19
Well it looks like the problem was between the chair and the keyboard.  I will try to specify the partitions manually.  Should I be using ext3?

---

### Post by warfacegod on 2010-01-19
> **SwiftySwerve said:**
> Well it looks like the problem was between the chair and the keyboard.  I will try to specify the partitions manually.  Should I be using ext3?

I use ext4 on all of my drives (6 total) and have had no issues. I've noticed a performance improvement in ext4 over ext3.

---

### Post by SwiftySwerve on 2010-01-19
Thanks Carlee.  I finally got it working.

---

