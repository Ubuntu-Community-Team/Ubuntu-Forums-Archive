---
title: "Problem partitioning with Gparted"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-19
Hi there! I was attempting repartitioning my hard drive with gparted from live cd. I created a new partition table and made 4primary partitions. One ntfs for win, one ext3 for ubuntu, a swap and a "data"(fat32) partition to be used by both win and ubuntu, all primary partitions.

When applying repartiotioning I get an error with creating mt last partition, which, afterwords, is black framed and called "unknown" by Gparted.

I tried moving the partitions round, to see if the last partition would have been created if it was larger or smaller or of a different file system but no luck. It's just the last one it does not like..doesnt matter if fat32/ext3, larger or smaller.

Any clue? Please...I'm stuck with install:(

---

### Post by geirha on 2009-03-19
A harddrive can have a maximum of four partitions. Four primary partitions that is. If you need more than four partitions, you need to make one of the primary partitions into an extended partition. Inside the extended partition you can have lots of logical partitions.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Moop on 2009-03-19
Ubuntu can read and write to ntfs partitions so you don't really need a fat32 partition. 

Try making your swap a logical partition so you're not maxed out on primary partitions.

---

### Post by webwiller on 2009-03-19
I have created four partitions. Not 5, just 4. But I get error when GParted attempts to create the 4th partition. So this isnt the prob I guess...am I wrong?

---

### Post by webwiller on 2009-03-19
I have no clue about how, but rebooting GParted was able to format the 4th partition too. SOLVED.

TY ANYWAY:)

---

