---
title: "Need help partitioning"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-08
Hi everyone,
I want to install Ubuntu on my laptop. I already have Windows XP and Vista installed on it but I don't want to remove them. The hard-disk size is 320GB. Now, I want to create a partition using Paragon Partition Manager using Vista. I will create a 50GB partiton (That's enough right? :-k). Which file system format should I use? NTFS, FAT32, Linux Ext 2, Linux Ext3 or Linux Swap2.

---

### Post by OldTimeTech on 2008-12-08
The live CD will partion the disk for you when you go to install Ubuntu and not delete either XP or Vista.

---

### Post by Locke_99GS on 2008-12-08
As mentioned, the partitioner on the LiveCD can do all of that for you during the install, but it can be done ahead of time if you'd like. 

Generically, you'd use ext3 for your linux partition. If you intend to use the hibernate feature, you want your swap partition (think page file) to be at least as large as the RAM you have installed.

---

### Post by geirha on 2008-12-08
If you want to use that windows partitioner, that's ok too, but just leave the 50GB unpartitioned. The ubuntu installer should give you the option of using the available space on the drive, and create the partitions it needs for you.

---

### Post by looi76 on 2008-12-09
> **geirha said:**
> If you want to use that windows partitioner, that's ok too, but just leave the 50GB unpartitioned. The ubuntu installer should give you the option of using the available space on the drive, and create the partitions it needs for you.

I can't resize the Vista Drive. Its size is 236GB and I want to make it 186GB so, that 50GB remains for Ubuntu. I have tried to resize the drive on Vista using Paragon Partition Manager 9.0 but I keep getting an error donno why! So, can I partition the drive using Ubuntu LiveCD and if I can do it, can someone please explain?

---

### Post by bumanie on 2008-12-09
You would be best using vista's in-built partitioner. It can shrink as well as expand partitions. But before you try any shrinking, it is best to defrag at least twice. Right click on my computer - choose manage and then choose manage storage devices. Right click on the partition you want to shrink. Choose shrink and shrink to whatever size you want. You can tehn install ubuntu to the unallocated space by choosing manual at the partitioning stage and format the space to ext3.

---

### Post by mknarr on 2008-12-09
Hay hope this helps
How to triple boot xp vista and ubuntu

Part 1  [http://ca.youtube.com/watch?v=M3t8Js_STEs](http://ca.youtube.com/watch?v=M3t8Js_STEs)
Part 2  [http://ca.youtube.com/watch?v=IiQi7cFV4Qk](http://ca.youtube.com/watch?v=IiQi7cFV4Qk)
Part 3  [http://ca.youtube.com/watch?v=PEadYq63jjE](http://ca.youtube.com/watch?v=PEadYq63jjE)
Part 4  [http://ca.youtube.com/watch?v=Bu-52xgQJR0](http://ca.youtube.com/watch?v=Bu-52xgQJR0)

I didn't actually try the guide on youtube but good luck with it it should be fairly easy.

Recognition goes to reponzo01 for creating the videos

---

### Post by hyper_ch on 2008-12-09
Just shrink the according harddisk/partition and leave the space unpartitioned that you want to use for ubuntu. No need to "pre-setup" the linux partitions.

---

### Post by RomanIvanov on 2008-12-09
if shrinking will not help and you run into the problem with error from partitioner that this partition is mounted and could not be changed please use this (UNetbootin+Gparted Life CD):
[https://bugs.launchpad.net/unetbootin/+bug/297568](https://bugs.launchpad.net/unetbootin/+bug/297568)

---

### Post by lkraemer on 2008-12-09
When I got my new Compaq CQ50-139NR, which had Vista on a 250 Gig Drive,
I just booted the Ubuntu 8.10 LiveCD, and went straight to Gparted, and
shrank the original Vista partition to 100 Gig.  I then moved the Compaq
Recovery Partition right behind the Vista partition (10 Gig)  Since I had never
set up or ran the Vista initial install everything went great.  Then, with a
100 Gig Vista partition and the ~148 Gig remaining I Installed Ubuntu.
Then once Ubuntu was installed, I rebooted into Vista, and it had to recover
from the change in partition sizes and then Vista was happy.  So I booted back
into Ubuntu, and started adding my software.
I probably should just have BLOWN away the Vista partition along with the
Recovery Partition and installed Ubuntu, but I wanted to make sure Ubuntu would work.

Just be sure to Defrag like the previous posts say.  And only Ubuntu 8.10 or later will
shrink/move the Vista partitions.  I tried with Ubuntu 8.04 and it didn't work for shrinking/moving.

Oh, There is a FOUR Primary Partition Limit on any one Physical hard Drive.  So, if you have Vista, and a Recovery Partition
that makes two, which leaves Ubuntu as EXT3, and linux-swap as a Swap Partition.  Linux-swap should be twice your RAM size.
Total of Four Primary Partitions MAXIMUM.

I thought I had a tutorial bookmarked but didn't find it.  Maybe someone else has a better one bookmarked.
Tutorial:
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Good luck.

lk

---

### Post by hyper_ch on 2008-12-09
or use logical partitions instead...

---

### Post by mikechant on 2008-12-09
Re the posts above above primary and logical partitions, it's highly recommended *not* to have four primary partitions since it gives you no flexibility. If you have two or three windows-related primary partitions I would recommend making all the remaning space into an extended partition; this can then contain up to 16 logical partitions (I believe you *can* have more than 16 but I think Linux will only recognise the first 16).

Personally, as I have plenty of disc space, I have the following disc partitions:

```

sda1: Windows (FAT16 boot related)
sda2: Windows (NTFS Recovery partition)
sda3: Windows (NTFS main Vista partition)
sda4: Extended partition containing the following logical partitions 
sda5: root partition 1 (Ubuntu 7.10, currently in use)
sda6: root partition 2 (Ubuntu 8.10, being tested)
sda7: root partition 3 (spare for testing other Linux distros)
sda8: /home 1          (Current home directory)
sda9: /home 2          (temporary copy of home 1 for use when testing new releases without screwing up home 1)
sda10: swap            (used by all releases)
sda11: data            (music, videos etc.)
followed by unallocated space, typically for expanding the data partition
followed by any test/temprorary partitions at the end of the disc
```
This means that hopefully I won't have to shuffle my partitions about too much in future, which can be a pain and very slow.
All my root and home partitions are 20Gb, which is quite generous and allows for just about anything, apart from music, video, photos etc. which I store on the data partition (150Gb with room for further expansion).
The swap partition is 2Gb, same as my RAM size.

---

