---
title: "Does the amount of ext3 partition affect performance?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Lightsaber™ on 2009-06-02
Hello everyone! I'm new to Ubuntu and to the Linux world. And I'm also new to the idea of *partitioning *your hard drive for another OS (besides Windows - yes I'm a Windows convert!) My question is, does the amount of ext3 filesystem partition affect in any way the performance of Ubuntu on my computer? Performance in terms of how fast Ubuntu accesses files, runs programs such as compiz and 3D games like OpenArena, Eclipse or Netbeans.

---

### Post by lindsay7 on 2009-06-02
I have never seen any info that it does and have never seen it personally.  As long as you have enough space to work with, that is if you make a partition too small you will not be able to save anything.

---

### Post by woedend on 2009-06-03
I've read before that in benchmarks separating /home into its own partition does hinder performance.  But how much?  Negligable.  That is, you will not be able to tell unless you are a numbers freak.  If you are referring to the size of the partition...you probably won't notice much until you come close to filling up the partition and run into "fragmentation" of sorts.

---

### Post by mcduck on 2009-06-03
> **woedend said:**
> I've read before that in benchmarks separating /home into its own partition does hinder performance.  But how much?  Negligable.  That is, you will not be able to tell unless you are a numbers freak.  If you are referring to the size of the partition...you probably won't notice much until you come close to filling up the partition and run into "fragmentation" of sorts.

sure, if it's on a separate partition on the same disk your hard disk will have to seek between the two partitions.

On the other hand if it's on a separate disk, you'd get *better* performance..

Anyway I'm not quite sure what the original poster means with "amount of partition".. Would this be *amount of partitions*, or *size of a partition*?

---

### Post by lovinglinux on 2009-06-03
I don't think having several partitions would affect the performance that much. It actually can increase performance if you choose wisely how you will use those partitions.

This sounds kind of weird, but let me explain.

Hard drives are faster in the beginning of the disk, due to the size of it's radius.

For example, I have two partitions on the same IDE disk. The first one (sda1) scores 59.82 Mb/s while the second (sda2) scores only 37.92 Mb/s. Both are ext4 and used to store personal data. The first one has 44% used space of 66 Gb, while the second has only 10% used space from 7.9 Gb. On the other hand, my first SATA partition (sdb2) scores 73.15 Mb/s while the second (sdb3) scores 70.76 Mb/s. The first one has 27% used space from 19 Gb and the second has 59% used space from 126 Gb.

As you can see, the partition with the worst result (sda2) has only 7.9 Gb and it is the last partition, so the whole partition is next to the end of the disk. The sdb3 has not a huge performance difference from sdb2 because it is a huge partition and it's data occupies just a fraction of the disc. But if sdb3 was mostly occupied with data, then it would experience a considerable performance drop, because you will be inevitably saving data to the end of the disk at some point.

So, if you have a single hard drive, I would recommend creating the swap partition first, then the root partition, followed by the home partition. Swap needs to be as much as fast as it can be if you need it, but it is rarely used if you have enough RAM. So, placing it in the beginning of the disk is the logical decision. Since it's size would be just a couple of Gb or even less, it won't "steal" fast disk space from other partitions. The root partition also needs to be fast, so the system can load programs without lagging. It's size would normally be between 10 Gb and 20 GB, which is not that much. Since the home partition will occupy the rest of the disk, it will probably behave fast most of the time, unless you save too much stuff and leave just a few Gb of free space. Then it will eventually access data from slower parts of the disk. In this scenario, creating an additional partition in the end of the disk for data storage could be a better option and could increase performance.

Let's say your hard drive have 160 Gb and 2Gb are occupied by swap. The root partition has 18 Gb and the rest, which would be 140 Gb, is occupied by home. Let's say that you like to record TV and store several of these recordings. If you have 100 Gb of recorded video, then most of home partition will be always occupied. I don't know how the journaling system allocate disk space, but let's assume it saves files in the first free space it encounters. Then the remaining free space on your home partition, which would be just 25% of the total disk space, would be located at the far end of the disk. In this scenario, it would be better to create an additional partition at the end of the disk to store all those videos. This way, you would guarantee that the remaining free disk space on your home partition would be located closer to the beginning of the disk (faster) and closer to the root partition (smaller seeking area). So whenever you need to save new data into the home partition, it will write faster than if you had a big home partition with all those videos stored. I also would recommend using the last partition for storage, but not for temporary data. For example, the TV recorder would probably need to write a lot of data in the disk and they are usually CPU intensive, so you should record the TV in the smaller home partition and then move the recording to the storing partition at the end of the disk.

So performance would ultimately depend on where you need to write/read data to/from, which is related to partition location, size, amount of allocated space, amount of free space and how do you use them.

If you will continue to use dual-boot, then I would recommend this order:

1) Windows C:\
2) Linux swap
3) Linux root
4) Relatively small Linux home
5) Larger storage NTFS partition (can be used to store large files from both OSs)

*UKeywords: 649167 2009 june partition allocation size location position performance*

---

