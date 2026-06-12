---
title: "Where are my two hard drives?"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by H A NAZIR on 2011-05-25
i install ubuntu11.04 in two drives of 25 g.b each.One drive is used for ext3 journalizing and second is for swap area but the problem is that i cannot view these drives.Both ubuntu and Windows7 display other drives.Please tell me where are these drives?And how to view them?
And also tell me about ext3,ext4 and swap area

---

### Post by Paqman on 2011-05-25
> **H A NAZIR said:**
> 
And also tell me about ext3,ext4 and swap area

EXT3 & 4 are just two versions of the default filesystem for Ubuntu. Your EXT3-formatted drive should be accessible when you open the file manager.

Swap is a type of extra memory that you system can use if it runs low on RAM. Using swap is much, much slower than using RAM, so it should be avoided if possible. You don't need 25GB of swap, normally it doesn't need to be any bigger than the size of your RAM. If you have a modern system with over about 1GB of RAM you will hardly ever use any of your swap space. Usually your swap partition will be a small partition on the same drive as the rest of your system.

Swap is also used when your system hibernates. The contents of your RAM are written into the swap partition, so that they can be restored when you wake the system up.

---

### Post by nemilar on 2011-05-25
You may try these commands to view your disks and partitions:

```
jdeprizi@stardust ~ $ cat /proc/partitions 
major minor  #blocks  name

   8        0  312571224 sda
   8        1    1228800 sda1
   8        2   67108864 sda2
   8        3   10240000 sda3
   8        4          1 sda4
   8        5    7905280 sda5
   8        6  226082816 sda6

jdeprizi@stardust ~ $ sudo fdisk -l /dev/sda
[sudo] password for jdeprizi: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0fc41089

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             154        8508    67108864    7  HPFS/NTFS
/dev/sda3           37639       38914    10240000    7  HPFS/NTFS
/dev/sda4            8508       37639   233989121    5  Extended
/dev/sda5            8508        9493     7905280   82  Linux swap / Solaris
/dev/sda6            9493       37639   226082816   83  Linux

Partition table entries are not in disk order

```

---

### Post by H A NAZIR on 2011-05-25
> **Paqman said:**
> EXT3 & 4 are just two versions of the default filesystem for Ubuntu. Your EXT3-formatted drive should be accessible when you open the file manager.

Swap is a type of extra memory that you system can use if it runs low on RAM. Using swap is much, much slower than using RAM, so it should be avoided if possible. You don't need 25GB of swap, normally it doesn't need to be any bigger than the size of your RAM. If you have a modern system with over about 1GB of RAM you will hardly ever use any of your swap space. Usually your swap partition will be a small partition on the same drive as the rest of your system.

Swap is also used when your system hibernates. The contents of your RAM are written into the swap partition, so that they can be restored when you wake the system up.

I have a 1g.b ddr2 ram and if swap area is not used regularly then is there any way to embed this partition with any other drive?

---

### Post by Paqman on 2011-05-26
> **H A NAZIR said:**
> I have a 1g.b ddr2 ram and if swap area is not used regularly then is there any way to embed this partition with any other drive?

You could, or your could shrink the swap area down so that it takes up much less space on the drive it's currently on, then format the rest of that drive as storage space.

---

### Post by coffeecat on 2011-05-26
@H A NAZIR, when you used the word "drives" in your first post, I think you meant partitions. nemilar suggested a couple of terminal commands which would give us an overview of your setup. So that we can advise best, please open a terminal and post the output of:

```
sudo fdisk -lu
```

---

