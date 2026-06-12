---
title: "URGENT!!! Low disk space problem"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by ashhab2010 on 2011-07-18
i have just 12 mb disk space remaining!!!!!!!!
initially i had alloted 10 gb disk space to ubuntu but i seem to have run out of it
is there any way to increase the space without reinstalling ubuntu all over again:(
plz help

---

### Post by CaptainMark on 2011-07-18
yes theres always a way, post the output of this command back here so we can see what your current formatting looks like for advice ```
sudo fdisk -l
```you should make sure youve already got or download a new livecd as well, your more then likely gonna need it

---

### Post by Blasphemist on 2011-07-18
More than half of the space you are using is your data files, not ubuntu and programs. Let's start with basics. Have you emptied the trash? Have you deleted any files that you know aren't needed? 

There is a program named computer janitor that can clean up packages but I be careful with it. You don't want to get rid of something you do want. I'd just stay away from it. Use GParted and make a screen shot from it. Post it back here and I'll look to see if I see anything like redundent swaps or something that could help get you more space.

---

### Post by ashhab2010 on 2011-07-18
> **CaptainMark said:**
> ```
sudo fdisk -l
```

here is the output

ashhab@Ashhab:~$ sudo fdisk -l

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f113f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7011    56307825    f  W95 Ext'd (LBA)
/dev/sda2   *        7012        9733    21864465    7  HPFS/NTFS
/dev/sda5               2        4463    35840983+   7  HPFS/NTFS
/dev/sda6            4464        7011    20466778+   7  HPFS/NTFS

---

### Post by Elfy on 2011-07-18
As you only have ntfs partitions it would appear that you are using wubi - that is installed inside windows. 

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

I've also changed the prefix to wubi so people looking know that this is not a normal ubuntu. 

Personally if you feel happy with ubuntu after trying it in windows it might be time to look at installing it to it's own partition.

---

### Post by ashhab2010 on 2011-07-18
> **Blasphemist said:**
> More than half of the space you are using is your data files, not ubuntu and programs. Let's start with basics. Have you emptied the trash? Have you deleted any files that you know aren't needed? 

There is a program named computer janitor that can clean up packages but I be careful with it. You don't want to get rid of something you do want. I'd just stay away from it. Use GParted and make a screen shot from it. Post it back here and I'll look to see if I see anything like redundent swaps or something that could help get you more space.

yeah the waste bin is empty and all useless files are deleted....

---

### Post by CaptainMark on 2011-07-18
ah okay wubi installs are a tad different and ive never used one so im out of this one but the advice from forestpiskie is sound, if your happy with ubuntu after trying it, then its a good option to consider installing it on its own partition,

---

### Post by Blasphemist on 2011-07-18
As mentioned above, with all ntfs we'd expect this to be a wubi installation. Is that right? That also makes sense given that all of your partitions have free space, about 21GB between them. 

This will help you resize the space available to ubuntu.
[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

This will help you get started if you want to migrate to a normal installation from wubi. [https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by jmszr on 2011-07-18
ashhab2010,

This will help if you decide to migrate Wubi to it's own partition: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) .

Also, try running "sudo apt-get clean" in the terminal, it may free up some space in / .

Hope that helps.

---

