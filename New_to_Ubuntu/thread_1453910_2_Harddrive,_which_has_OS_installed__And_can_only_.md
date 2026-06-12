---
title: "2 Harddrive, which has OS installed?  And can only see one?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Sepiraph on 2010-04-13
Hi all,

  First post! :)  Ok so I finally decided to venture into Ubuntu as my main OS for a computer computer.  I was able to get it working and all, however I have 2 harddrive and I am a bit unsure which HD I installed the OS file into.  If I go to GParted I can see both HD but in Computer, I have only see 1 HD (the one that I want to use as a secondary drive).  I did some quick googling but didn't really find the answers... Please help!

---

### Post by nitstorm on 2010-04-13
```
sudo fdisk -l
```
If you have only Ubuntu on your computer, then the partition with the * has your Ubuntu partition on it & hence the drive with the partition has ur Ubuntu on it...

---

### Post by Sepiraph on 2010-04-14
Thanks for the quick reply, well I did the command and it shows that both HDs have one partition with the * in it!  The reason was being when I was installng the new system, the older HD (160GB) already have Ubuntu installed and I also installed Ubuntu in the newer HD.  What should I do now?


> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120475   967715406   83  Linux
/dev/sda2          120476      121601     9044595    5  Extended
/dev/sda5          120476      121601     9044563+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43c4e8b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1221     9807651   83  Linux
/dev/sdb2            1222       19457   146480670    5  Extended
/dev/sdb5            1222        1828     4875696   82  Linux swap / Solaris
/dev/sdb6            1829       19457   141604911   83  Linux

---

### Post by Sepiraph on 2010-04-14
Ok so actually digging further, I went to GParted and unflagged "mount" on the 2nd HD.  And I notice that in "Computer", it actually showed my 1st HD as Filesystem while if I click on the 2nd HD it is trying to mount it.  So I guess what I need to do is to erase and repartition the 2nd HD.

---

### Post by readycarpenter on 2010-04-14
so you have 2 hard drives
1TB, and a 160GB

it appears you have linux on both drives, did you install twice or do you have 2 linux installed?

---

### Post by Sepiraph on 2010-04-15
Yea I had 2 copies of Linux, one from a previous install.  But anyway I already resolved my issue... right now it is able to connect to a Cisco 2950 and network w/ Vista. :D

---

### Post by readycarpenter on 2010-04-15
you should really post how you resolved your problem, so this forum actually can help someone else with a similar problem, then set as "solved"

cheers

---

### Post by Sepiraph on 2010-04-17
> **readycarpenter said:**
> you should really post how you resolved your problem, so this forum actually can help someone else with a similar problem, then set as "solved"

cheers

Well I didn't really "resolved" my problem... 

It's more of a "I thought I had a problem but I really didn't because I was so new to Ubuntu"

But anyway in Gparted, it will show the mount point and the one listed with "/" is it.

---

