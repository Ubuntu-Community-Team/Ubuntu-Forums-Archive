---
title: "Ubuntu Installation Problem &quot;unusable&quot; disk space"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by RMckelvie89 on 2011-03-04
hey there, I am a newcomer to the Linux OS and I have run into a problem when trying to install version 10.10 and allocating a suitable partition. 

I wish to run this alongside Windows 7 so I can try out something new and I decided  to choose "Specify Partitions Manually" and reduce the data size to 200GB  so that I can run Win 7 alongside ubuntu. 

When I created the new partition, I come across the message, 

[B]"No root file system is defined.
Please correct this from the partitioning menu.[/B]"

I wish to know what this means and how I can change the unusable partition to actual free space. Please note that I do not speak fluent jargon and if you go on about "mounting drive" and such, you will no doubt lose me.

---

### Post by sikander3786 on 2011-03-04
Welcome to Ubuntu and the forums :-)

You need to define mount point for your '/' partition and also for Swap. This page will help you I believe.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Once you read that page, you'll definitely have some queries and they'll be easy to answer later :-)

---

### Post by RMckelvie89 on 2011-03-04
I am still confused and i know nothing about partitioning and the contents of that site is still a bit foreign to me.

I have no free space at the moment because the entire disk is dedicated to Windows 7 and I don't want to delete any partitions because I don't know what they do and I'm afraid I might muck up my entire system.

Just to add clarification, I decided to use the disk manager in order to shrink the size of the volume of the C drive and it is still unusable according to the installer.

---

### Post by sikander3786 on 2011-03-04
Ok. No problem. From the booted Ubuntu Live CD, please go to System > Administration > GParted and post a screen-shot. You can find the screen-shot app under Applications > Accessories > Take Screen-shot.

And from Applications > Accessories > Terminal, post the complete output of this command.

```
sudo fdisk -lu
```

---

### Post by RMckelvie89 on 2011-03-04
Here is my output. 

> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07e503a8

   Device Boot             Start                     End                   Blocks           Id                      System
/dev/sda1   *                2048                  409599             203776        7                      HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2                    409600            391034599    195312500     7               HPFS/NTFS
/dev/sda3                 460171264      488183807     14006272       7                 HPFS/NTFS
/dev/sda4                 488183808    488395119       105656           c                     W95 FAT32 (LBA)



---

### Post by sikander3786 on 2011-03-04
There are already 4 primary partitions which is the limit. You need to delete one of your existing partition and create and extended one with 2 new logical partitions (at least). One for '/' and the other for Swap.

Which one of those partitions is use-less for you?

---

