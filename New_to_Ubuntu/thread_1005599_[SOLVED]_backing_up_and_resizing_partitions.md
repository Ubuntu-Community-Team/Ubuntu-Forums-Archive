---
title: "[SOLVED] backing up and resizing partitions"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by potatoehead64 on 2008-12-08
Hi folks
My 80gb hard drive is getting into a bit of a mess and I'm running out of space. I have a data partition, partition for Ubuntu and another for MS Windows. 
I've needed to reinstall Ubuntu a couple of time and my current install of Ubuntu Studio needs more space. I have Gparted installed but want to make an iso backup of my hard disk first before fiddling (I'd messed with Gparted before and messed up grub. Thats why I've more than one partition with ubuntu.

1. Whats the best way to create a .iso on a DVD?
2. What is safe to resize in Gparted? 

current view on Gparted is as follows
> 
/dev/sda1 fat32 3.90 GiB 3.11 Gib Used
/dev/sda2 fat32 35.07 GiB 28.31 GiB used boot.lba
/dev/sda4 extended 28.94 lba
     /dev/sda5 ext3 6.93 GiB 4.21 GiB used
     /dev/sda6 linux-swap 368.65 Mib
     /dev/sda7 ntfs 3.07 GiB
     /dev/sda11 ext3 9.61 GiB 7.77 GiB used
     /dev/sda12 linux-swap 486.31 Mib
     /dev/sda8  linux swap 611.82 Mib
     /dev/sda9 ext3 5.58 GiB 2.27 GiB used
     unallocated    282.42 MiB
     /dev/sda10 ext3 2.04 GiB 97.57 MiB used
     unallocated    125.51 MiB
     

sda4, sda11 and sda12 have a keys icon next to the (I assume meaning they cannot be touched because they are mounted????)

sda7 - the ntfs section has a warning triangle icon next to it.

Can anyone help me on this? I really want to get everything tidied up.

---

### Post by cariboo on 2008-12-08
You can create an iso of any disk you want, for instance if you want to create an iso of /dev/sda5. in a terminal type:

```
dd if=/dev/sda5 of=/dev/sda2/backup.iso
```

The above command is an example, where dev/sda5 is duplicated on /dev/sda2 and named backup.iso. the one problem with dd is that it duplicates the partition exactly, including empty space.

Partimage is another program you can use to create an image of your partitions, and it is smart enough not to duplicate the empty space.

DD is installed by default and partimage is available in the repositories.

Jim

---

### Post by potatoehead64 on 2008-12-14
I've no room to create an .iso on any partition. Some of the partition below sda11 are now obsolete and I'd like to delete them. I think I tried this before and it caused GRUB error resulting in me having to reinstall Ubuntu. Thats why I have so many partitions. Is there a safe way to delete the other partitions and resizing sda11?
sda11 is now 100% full and has caused all sorts of problems including stopping firefox working. 
sda1 sda2 and sda3 are (I think) allocated to windows XP and my data drive (which is also full!). 
I do have Gparted on CD rom now. I'm tempted to use it but have no way of backing up. Please help.

---

### Post by nhasian on 2008-12-14
i strongly encourage you to copy any critical data to a USB thumbstick or USB hard disk before using gparted.  you can delete any obsolete partitions from gparted.  just make sure they are not mounted.  Then you can resize the partitions you want to keep and have them take up the free space.  Please remember you cannot use gparted on a mounted filesystem so you should boot off a liveCD to make the changes.

---

### Post by bodhi.zazen on 2008-12-14
Well, first you should manage your partitions from a live CD. You can not resize a partition unless it is unmounted.

For the swap partitions, you can do this from gparted. But you can not unmount the root partition, thus a live CD.

Second, if you wish to make an image of the entire HD you need a place to put it. These images will be quite large.

Personally I use partimage (you can do one partition at at time).

---

### Post by potatoehead64 on 2008-12-15
Well..... I finally got everything tidied up yesterday after saving everything to a flash drive and putting it on another PC I have. It took about half a dozen trips back and forth though. I sorted out the partitions and reinstalled ubuntu afresh. I still don't understand why deleting a partition ends of with "Grub error" though. The hard disk is much tidier now though. Took me all day, but at least it is done. Thanks for all the advice.

---

### Post by gTinker on 2008-12-15
[QUOTE=potatoehead] I still don't understand why deleting a partition ends of with "Grub error" though. [/QUOTE]

Well, you don't give us much to go on to answer this question for you. You didn't mention what partitions you are talking about or what GRUB error you got either.

However, I will tell you one way it could happen. If you delete a partition number smaller than other partition numbers, the partitions are renumbered to make a continuous number sequence, thus GRUB might no longer point to the partition it previously pointed to and a necessary file may not be found. This could be the source of a GRUB error. 

For example. If you have partitions, 5; 6; 7; and you delete 6, then the old 7 becomes the new 6. 

You can have 4:[5;6;7] but you cannot have 4:[5; 7](it will automagically be 4:[5; 6]). If your GRUB is configured to use device nodes, rather than UUIDs or Labels, those renumbered device nodes no longer point to the correct partition.

---

