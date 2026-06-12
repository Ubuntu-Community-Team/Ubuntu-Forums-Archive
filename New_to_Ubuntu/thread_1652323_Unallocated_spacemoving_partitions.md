---
title: "Unallocated space/moving partitions"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Inisfad on 2010-12-24
Well, it seems that this is the day for partition questions, but none seem to answer my question.  I have had a dual boot Windows/Ubuntu system for a while.  I set it up as quite a newbie, and have now encountered a problem.  Windows is my first partition, and then I have unallocated space.  After the unallocated space, I have my Ubuntu drive and the swap file.  I now want to enlarge the Ubuntu drive, but have learned that I can only easily enlarge to unallocated space that is to the right of/after the drive in question.  My unallocated space is before my Ubuntu partition.  I copied the Ubuntu partition into the unallocated space.  Now my drive is sda1 (Windows), unallocated space, sda3 (copy of Ubuntu drive), unallocated space, sda4 (original Ubuntu drive), sda5 (swap file).  I have probably done this all wrong, but what do I do now?  Is there some way to get the copy of Ubuntu to become what my computer boots to, so that I can remove the original sda4?  Thanks (and happy holidays!!)

---

### Post by sandyd on 2010-12-24
> **Inisfad said:**
> Well, it seems that this is the day for partition questions, but none seem to answer my question.  I have had a dual boot Windows/Ubuntu system for a while.  I set it up as quite a newbie, and have now encountered a problem.  Windows is my first partition, and then I have unallocated space.  After the unallocated space, I have my Ubuntu drive and the swap file.  I now want to enlarge the Ubuntu drive, but have learned that I can only easily enlarge to unallocated space that is to the right of/after the drive in question.  My unallocated space is before my Ubuntu partition.  I copied the Ubuntu partition into the unallocated space.  Now my drive is sda1 (Windows), unallocated space, sda3 (copy of Ubuntu drive), unallocated space, sda4 (original Ubuntu drive), sda5 (swap file).  I have probably done this all wrong, but what do I do now?  Is there some way to get the copy of Ubuntu to become what my computer boots to, so that I can remove the original sda4?  Thanks (and happy holidays!!)
you need to install grub while chrooted into sda3 and update the /etc/fstab file
post output of
```

sudo fdisk -l
```


happy holidays to you too.

---

### Post by |Eric| on 2010-12-24
i may sound a bit like a plug : pqmagic works wonders 

when you resize move and alter your partition table make shure grub is fine and that fstab needs not to be modified

blkid gives the uuid for the partitions ( this may need to be modified in the fstab)

my usual layout is : 
/dev/sda1 = windows
/dev/sda2 = Linux system
/dev/sda3 = swap
/dev/sda4 = everyting else 
 
you can notice im not using extended partitions ... (kind of an old habit)

edit : 40gb is usualy plenty for most systems .

---

### Post by Inisfad on 2010-12-26
Thanks for the replies.  Here is the output for fdisk -l:      Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x021b021a     Device Boot      Start         End      Blocks   Id  System /dev/sda1            6375        6500     1012095   83  Linux /dev/sda2   *           1        1938    15566953+   7  HPFS/NTFS /dev/sda3           22889       30401    60348172+   5  Extended /dev/sda4            6501       17939    91883767+  83  Linux /dev/sda5           22889       30089    57842001   83  Linux /dev/sda6           30090       30401     2506108+  82  Linux swap / Solaris  Partition table entries are not in disk order    Remember, I am a newbie!!  When I start Gparted, along the graph at the top, it shows my Windows partition first (sda2), then 33gb unallocated (I reduced my Windows partition size), then sda1 (which has one file in it that is locked - I don't know what this is, but it is an ext2 Linux partition), then sda4 (the copy of my Ubuntu partition), then 37gb unallocated, then sda5 (the Linux partition that is being used), then the linux swap file.  I would like to make Linux into one large partition, but don't know how to do this  Thanks!! (and sorry for the way this is scrolling across the page.  I can't get it to go in the colums that I see when I am writing this.  Eck).

---

