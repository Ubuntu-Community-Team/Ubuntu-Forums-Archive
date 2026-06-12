---
title: "Need help with partitioning space"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Elfon on 2011-03-03
Here is the scenario:
I had XP, which was getting to laggy so I uninstalled it. Instead I've installed ubuntu 10.10, making separate partitions for / (600 mb); /boot (20 gb); /home(rest of space); Gparted showed that i already had the swap area.(some 200 mb)
I might be cursed, because Ubuntu was too slow and laggy as well. Things were disappearing from the  top panel and overall weird thing were happening. Besides I missed some of my video games.
So I decided I would uninstall ubuntu, install XP again, but after that install ubuntu one more time and have a dual boot.
XP setup showed me what partitions i had - there were 4 of them as mentioned before. So i've installed Xp on the partition which was originally for /boot and was 20 gb, formatting it as well. Everything works fine, but my computer shows me only one local disc where the windows is installed which is only 20 gigs. I though i would be able to access other partitions which were / and /home (which had a lot of files on it) or at least show me that they exist. 
So i've decided to install ubuntu and make dual boot. However, in the ubuntu setup, in the manual partition option, it shows me that my entire hard drive (500 gb) is free space. But if i separate it one more time it will format those partitions first. And i don't want to lose any of my files and have a trouble installing windows one more time. Gparted shows the same and wants to format the hard drive before making partitions.

So, is there a way i can install ubuntu, and leave xp, as well as not losing any of my data which i want to store in /home partition?
Sorry for a lot of text, but i wanted to describe the situation in details.  
Thank you

---

### Post by srs5694 on 2011-03-03
> **Elfon said:**
> Here is the scenario:
I had XP, which was getting to laggy so I uninstalled it. Instead I've installed ubuntu 10.10, making separate partitions for / (600 mb); /boot (20 gb); /home(rest of space); Gparted showed that i already had the swap area.(some 200 mb)
I might be cursed, because Ubuntu was too slow and laggy as well. Things were disappearing from the  top panel and overall weird thing were happening.

It could be your computer is just too old for modern software; or maybe there's something wrong with it (flaky RAM, perhaps). There are diagnostic tools you can run to help locate such problems -- but that's a matter for another thread, should you want to pursue it. For now, you've got a more immediate problem....

> So I decided I would uninstall ubuntu, install XP again, but after that install ubuntu one more time and have a dual boot.
XP setup showed me what partitions i had - there were 4 of them as mentioned before. So i've installed Xp on the partition which was originally for /boot and was 20 gb, formatting it as well. Everything works fine, but my computer shows me only one local disc where the windows is installed which is only 20 gigs. I though i would be able to access other partitions which were / and /home (which had a lot of files on it) or at least show me that they exist.

Windows can't read Linux filesystems by default, so they won't appear in the "My Computer" window. You should see them in the Windows disk partitioning tool, but IIRC, they'll be identified as "unknown filesystem" or some such, and you won't be able to read them.

There are ext2fs/ext3fs drivers for Windows, such as [this package.](http://www.fs-driver.org/) (There may be others, too; try a Web search if you want to locate more.) I have little experience with such tools, so I can't say how well they work. If you just need to copy a few files off, something like this should work OK. Alternatively, you could boot from a CD- or DVD-based Linux distribution and copy the files onto a USB flash drive or the like.

> So i've decided to install ubuntu and make dual boot. However, in the ubuntu setup, in the manual partition option, it shows me that my entire hard drive (500 gb) is free space.

There are several problems that can cause libparted-based tools (including the Ubuntu installer's partitioning system and GParted) to do this. One is a mis-sized extended partition, as described [here.](http://www.rodsbooks.com/missing-parts/index.html) Given what you've described, though, I suspect that the Windows partitioner has re-assigned a logical partition to be primary without adjusting the extended partition's size. (This is a known bug in the Windows installer.) The solution might be logically similar, but some of the details will differ.

In any event, I recommend you boot a Linux live CD, open a Terminal window, and type the following command:

```

sudo fdisk -lu

```

Note that's a lowercase letter "L" in "-lu", not a digit "1". Post the output here, either as a screen shot or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings (which preserves formatting, thus making the post more legible). This command won't solve the problem, but it will show us the state of your partition table, which will enable us to give you better advice.

---

### Post by louiech21 on 2011-03-03
All I can suggest installing XP, then boot into XP and insert your Ubuntu disc and use Wubi.  Wubi is the Windows installer for Ubuntu which you can find on your Ubuntu disc.

Your other alternative is to boot from your live CD and use Gparted to create your hard drive partitions.  Personally the Wubi route is probably the easiest.

---

### Post by srs5694 on 2011-03-03
I strongly recommend against installing via WUBI at this point. The disk's partition table is almost certainly corrupted at this point, and installing via WUBI will not fix that problem. Thus, the problem will persist, and given the other issues, some disk space will remain inaccessible.

Post the fdisk output, as I recommended in my first post; that will enable those of us who understand these issues to offer advice for how to fix the problem.

---

### Post by kn0w-b1nary on 2011-03-03
[QUOTE=srs5694;10517181]I strongly recommend against installing via WUBI at this point. The disk's partition table is almost certainly corrupted at this point, and installing via WUBI will not fix that problem. Thus, the problem will persist, and given the other issues, some disk space will remain inaccessible.[QUOTE]

+1.

---

### Post by louiech21 on 2011-03-03
> **srs5694 said:**
> I strongly recommend against installing via WUBI at this point. The disk's partition table is almost certainly corrupted at this point, and installing via WUBI will not fix that problem. Thus, the problem will persist, and given the other issues, some disk space will remain inaccessible.

Post the fdisk output, as I recommended in my first post; that will enable those of us who understand these issues to offer advice for how to fix the problem.

This is very good advice, the partition table should be fixed before installing anything.  Would you recommend using gparted to wipe the hard drive and remove all the partitions to start fresh?

---

### Post by Joe of loath on 2011-03-03
I assume you mixed up /boot and /? 600mb is too little for /, and 20gb wayyy too big for /boot ;) Generally I run a 200mb /boot partition.

---

### Post by jbiggs12 on 2011-03-03
> **Joe of loath said:**
> I assume you mixed up /boot and /? 600mb is too little for /, and 20gb wayyy too big for /boot ;) Generally I run a 200mb /boot partition.
This. Your system would probably be really laggy if you were to only designate that much space for your root partition.

---

### Post by Elfon on 2011-03-03
> **srs5694 said:**
> It could be your computer is just too old for modern software; or maybe there's something wrong with it (flaky RAM, perhaps).

Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
RAM 3023 MiB
VGA Radeon HD 3410
I don't think hardware is a problem here.

This is what id get by enetering  sudo fdisk -lu command 
```
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43166654    21583296    7  HPFS/NTFS
/dev/sda2        43175934   976771071   466797569    5  Extended
/dev/sda3       976586752   976771071       92160   82  Linux swap / Solaris
/dev/sda5        43175936   976586751   466705408   83  Linux

Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18b54d69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7822079     3911008+   b  W95 FAT32
ubuntu@ubuntu:~$ 

```

> This. Your system would probably be really laggy if you were to only designate that much space for your root partition.
I don't remember how much space i designated precisely, but somehow i have a feeling that what i said is correct. i messed up. This is probably the cause of lags. won't do that major mistake again.

---

### Post by srs5694 on 2011-03-03
> **louiech21 said:**
> This is very good advice, the partition table should be fixed before installing anything.  Would you recommend using gparted to wipe the hard drive and remove all the partitions to start fresh?

The OP clearly stated there are files on some of the partitions that s/he wants to recover. Thus, wiping everything and starting from scratch is not an option.

Given the fdisk data I asked for, it will probably be possible to suggest a method of recovering that will not involve wiping everything and re-installing.

---

