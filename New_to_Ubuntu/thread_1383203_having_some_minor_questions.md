---
title: "having some minor questions"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-01-16
im installing windows and ubuntu well dual booting them   and  this guide that i was reading said to install windows first and then ubuntu  


but i have this question when i wipe it the partions will still be in ext3 format and  windows wont go off of that  so is there anyway to just get it back to ntfs format

---

### Post by JKyleOKC on 2010-01-17
If you do a full wipe of the drive, the partitions will all go away. Then when you install Windows, its installer will format the whole drive as NTFS. After installing Windows, use its defragmenter to correct any fragmentation introduced by the install process and its temporary files, then install Ubuntu and tell it to use the largest free space. It will detect that space, shrink the Windows partition, and create its own partitions then format them as ext3 or ext4 (depending on the version you install). If you follow this sequence, it's almost entirely automatic!

---

### Post by kenuf on 2010-01-17
I'd do the following:

1.   Install Windows, and defrag
2.   Boot to the Ubuntu Live CD
3.   When it loads go to System> Administration> GParted
4.   Right click on the partition and click 'Resize/Move'
5.   Shrink the partition to make space for Ubuntu and apply the changes in gparted
6.   Double click on the install Ubuntu icon
7.   Proceed with the install on the newly created unallocated space.

---

### Post by lidex on 2010-01-17
It would save you a headache if you partitioned the drive first and then told windows to use the partition you set aside for it. That would eliminate having to resize windows, which is problematic at best for the uninitiated. Here is a good resource - scroll down to the "Windows partitions" section. 
[http://ubuntuguide.org/wiki/Multiple_OS_Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation")

---

