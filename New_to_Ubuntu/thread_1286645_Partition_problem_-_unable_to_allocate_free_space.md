---
title: "Partition problem - unable to allocate free space"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-09
I used to have ubuntu + xp + vista. Now i've removed XP and want to give that unallocated space to ubuntu, however i am having trouble doing this. I've put in the livecd, and tried to use gparted, but it won't let me increase ubuntu's size anymore, here is a screenshot: 
[http://img23.imageshack.us/i/screenshotjw.png/](http://img23.imageshack.us/i/screenshotjw.png/)
As you can see it says there is 0 space after the partition sda6 (which is ubuntu)

---

### Post by taavikko on 2009-10-09
Please paste the output of 
```
sudo fdisk -l
```

---

### Post by Falc7 on 2009-10-09
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfec7e353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543040+   7  HPFS/NTFS
/dev/sda2            2434       11019    68967045    5  Extended
/dev/sda5            2434        2737     2441848+  82  Linux swap / Solaris
/dev/sda6            2738       11019    66525133+  83  Linux

```

edit: ooops sorry i've managed to work it out, i need to resize the extended partition before i can size ubuntu's partition

---

### Post by taavikko on 2009-10-09
Seems little bit twisted, since 

The HDD contains total: 14593 cylinders
and the extended section ends in: 11019 cylinders.

You cannot increase the size of an extended partition with an primary partition.

I would create an new fs and mount it somewhere to have the space available.

Maybe someone with more knowledge on partitions will answer to you shortly?

---

### Post by presence1960 on 2009-10-09
you first need to increase the size of sda2 which is an extended partition containing sda6. Once that is accomplished you will be able to resize sda6.

---

