---
title: "Hard Drive Misallignment upon install"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by CounterVulture on 2011-03-23
Hello

My apologies if this post should be in the hardware or installation forums. I wasn't sure, so I followed the forum guide's advice and posted it here.

I'm relatively new to ubuntu and have been learning it gradually over the past year or so. Recently I had to have my hard drive replaced due to my previous hard drive's malfunctioning. The repair place that diagnosed and replaced the drive replaced it with a Western Digial hard drive with 4k sectors and this seems to have caused some problems with my Ubuntu installation.

Before installing ubuntu I installed a copy of windows for certain applications, then followed up by installing ubuntu. Upon installation Ubuntu created for itself an extended container partition in the space that wasn't allocated for windows. In that container it installed the main filesystem in one partition and swap space in another.

I ended up having the same problem that it seems many people with these 4k sector drives seem to have where ubuntu's install created misalligned partitions. However, the disk utility says that only the container partition is misalligned (by 1024 bytes). The main filesystem and swap partition don't seem to have any misallignment problem.

My question is, does the misallignment of the container partition still affect system performance even though the individual partitions it contains are aligned? Since I just performed a fresh install I'd like to fix this problem before starting any serious work on this system. 

Any input and information is appreciated, thanks!

---

### Post by deconstrained on 2011-03-23
I found this quite informative when I was setting up RAID w/striping, which requires careful partition alignment for performance:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by oldfred on 2011-03-24
You can ignore the extended.

See post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by CounterVulture on 2011-03-24
Okay, thanks for all the information.

---

### Post by CounterVulture on 2011-03-24
Also, could somebody explain why it is that the extended container partition can be ignored in the first place? Why does the container partition alignment not affect performance but the filesystem partition alignment does?

---

### Post by srs5694 on 2011-03-24
Alignment is an issue in filesystem (and probably swap space) performance because most filesystems are built up from data structures that are 4 KiB in size -- precisely the same size as the physical sectors in Advanced Format drives. When a write is made of one of thes 4 KiB data structures on a misaligned partition, the drive must read two physical sectors, modify parts of both of them, and then write both sectors back. This takes extra time compared to simply writing the 4 KiB sector that corresponds to the data structure on a properly aligned partition.

Note that alignment is relative to the filesystem, which is placed on a primary or logical partition. Extended partitions don't contain filesystems directly. The only data structures unique to extended partitions are the [Extended Boot Records (EBRs),](http://en.wikipedia.org/wiki/Extended_boot_record) which are 512-byte data structures that tell the OS where an extended partition resides. These data structures are read when the computer boots and seldom written, so there's little that can be done to either enhance or degrade performance by improving their read/write speed. Furthermore, because they're 512 bytes in size, no matter how the extended partition is aligned, writing an EBR will entail a read-modify-write operation. In sum, extended partition placement is irrelevant for Advanced Format performance; only primary and logical partition alignment matters.

---

### Post by jtarin on 2011-03-24
Very well said srs5694!!!

---

### Post by CounterVulture on 2011-03-24
Thanks, srs! That's exactly what I was looking for, and very well explained, too.

---

