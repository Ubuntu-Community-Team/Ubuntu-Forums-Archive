---
title: "RAID and Ubuntu"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Superdarion on 2010-04-30
Hi. I'm trying install Ubuntu 10.04 64bits on a desktop (a Dell studio xps 8100) but I've failed miserably.

The problem is the RAID, it seems, and it's something I know very very little about. So far, I can load up the liveCD and use anything. Ubuntu can see and mount the 1.2tb HD.

The problem is during installation. In the partition part, gparted doesn't detect that the one partition has win7 in it (thus I don't even get the "install side by side" option) and I can't seem to resize the partitions manually. And the thing is that they aren't seen by gparted as sda or sdb, but rather as /dev/mapper/lsw_ciagccecj_ARRAYX, with X some number.

Now, I've been reading around the forums and they talk about soft/hardware raid and fakeraid. I just have no idea of what that is!

So my question is how do I set up a partition to install linux without wiping win7?

In case it's of any help, I include fdisk -l  and   dmraid -s -s.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       19452   105049035    5  Extended
/dev/sda5            6375        9413    24410736   83  Linux
/dev/sda6            9414        9535      979933+  82  Linux swap / Solaris
/dev/sda7            9536       19452    79658271   83  Linux

```

```
ubuntu@ubuntu:~$ sudo dmraid -s -s
*** Group superset isw_ciagccecj
--> Active Subset
name : isw_ciagccecj_ARRAY0
size : 2500518400
stride : 256
type : stripe
status : ok
subsets: 0
devs : 2
spares : 0

```

---

### Post by P4man on 2010-04-30
Im confused since your fdisk output doesnt even show an sdb (but does show linux partitions) ?

Do you have 2 disks? Are they raided in the bios? If so, you have a fakeraid. A livecd doesnt mount that, doesnt see it. fakeraid really is a "windows raid driver in bios" and is only meant to allow windows to boot from a software raid.

i do think the alternate cd recognizes fakeraids and proposes to you to apply  the same settings as the fakeraid for a linux software raid, but im not sure it will detect windows partitions or be able to mount them.

Unless someone else gives you better advice, I would suggest not to even try to install ubuntu on fakeraid that has windows on it. Either add a drive for ubuntu, or remove the fakeraid and instead use windows dynamic disk raid to create a more secure and better performing raid (compared to fakeraid, which really is not a good idea). The only problem is  that windows can not boot itself from dynamic disks (which is the only reason  we even have fakeraids) so you cant use that for the OS itself, only for data partitions.

---

### Post by Superdarion on 2010-04-30
Oh, I'm sorry. Seems I didn't paste all of it. Here it goes again:

```
buntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

Device Boot Start End Blocks Id System
/dev/sda1 1 11 88326 de Dell Utility
/dev/sda2 * 12 1266 10078208 7 HPFS/NTFS
/dev/sda3 1266 155650 1240090624 7 HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

---

### Post by P4man on 2010-04-30
Meanwhile I read that ubuntu 10.04 now does recognize fake raids, but its absolutely not clear to me if its safe to install on it if windows is installed on it. Im going to stand by my previous advice unless someone with more experience can chime in.

---

### Post by psusi on 2010-04-30
Indeed, 9.10 supported fake raids well.  Unfortunately, there was a late regression in 10.04 that broke the ability to install to them.  You can probably work around this by manually setting up the partitions first, then telling the installer to use the existing partitions.

Run gparted from a terminal with:

sudo gparted /dev/mapper/isw_ciagccecj_ARRAY0

You should be able to partition the disk that way, then start the installer.

For reference, the bug is here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050)

Click "this affects me too".

---

### Post by Superdarion on 2010-04-30
Thanks you very much for your help!

Now I only have one more question. How do I know if what I have is fakeraid or hardware raid? P4man mentioned the bios; if I find mention to raid in the bios, then it's fakeraid?

---

### Post by P4man on 2010-04-30
the fact linux sees 2 drives proves its a fake raid (if its a raid at all) and not a hardware raid. Hardware raid is invisible to the OS and seen as just 1 drive (if thats how its configured). Its extremely unlikely you'd have a hardware raid and not know about it, these things tend to cost a fair bit of money (and for good reason) and you wont find it integrated on any desktop motherboard that Im aware off. Its almost always a separate card (unless on some workstation/server boards, and even there its generally a card).

---

### Post by Superdarion on 2010-04-30
Ubuntu auto-mounts it as 1 big drive, actually. It is only in fdisk that I can see 2 separate drives.


All I know really is that Dell offers either one 500gb HD or two 500g in raid0 and the price increase for the 2-drive version only accounts for the extra drive itself. I guess that means it's fakeraid?

---

### Post by P4man on 2010-04-30
> **Superdarion said:**
> Ubuntu auto-mounts it as 1 big drive, actually. It is only in fdisk that I can see 2 separate drives.

It would mount it as one drive if it were a hardware raid (configured as raid 0), but fdisk wouldnt see 2 drives, not even the brand and type or correct size of the individual drives. It would just see a raid volume (without extra management software). 

> All I know really is that Dell offers either one 500gb HD or two 500g in raid0 and the price increase for the 2-drive version only accounts for the extra drive itself. I guess that means it's fakeraid?

\
its a dell desktop. You bet its a fakeraid :)
but find out in the bios. im guessing you will find some intel matrix raid controller settings. Thats intel's fake raid.

---

### Post by Superdarion on 2010-04-30
Thank you very much, guys!

I'll let you know how the partitioning (using that link provided) and installation went as soon as I get it done!

---

### Post by Deihmos on 2010-04-30
> **psusi said:**
> Indeed, 9.10 supported fake raids well.  Unfortunately, there was a late regression in 10.04 that broke the ability to install to them.  You can probably work around this by manually setting up the partitions first, then telling the installer to use the existing partitions.

Run gparted from a terminal with:

sudo gparted /dev/mapper/isw_ciagccecj_ARRAY0

You should be able to partition the disk that way, then start the installer.

For reference, the bug is here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050)

Click "this affects me too".

Raid 0 worked perfect for me in 9.10 but not the same with this new build. Gparted does not show any raid disks but shows them as individual disk. If I boot with the 9.10 live cd Gparted does see the raid disk as one. When installing I was able to chose which partition to install grub too but it does not work with 10.04.

---

