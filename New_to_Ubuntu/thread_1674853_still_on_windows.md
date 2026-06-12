---
title: "still on windows"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Paul Fletcher on 2011-01-24
At the moment i am still on windows but i am eager to get on ubuntu and i just want to ask a few questions.  i have two hard drives disk c and disk d. i have moved the things i want to keep to drive d so if i put ubuntu on drive c would this affect anything on drive d. also could i transfer the items back onto ubuntu.

---

### Post by CharlesA on 2011-01-24
If everything is on the "D" drive, and you install Ubuntu on the "C" drive you will still have access to your files.

Just keep in mind that there is no such thing as drive "C" or "D" on Linux. It might be listed as something like sda1 or sdb1.

---

### Post by James_Lochhead on 2011-01-24
> **Paul Fletcher said:**
> I have two hard drives disk C and disk D. 

The letters C and D are actually references to partitions rather than the hard drives themselves. A partition is a "logical storage unit" ([http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)) inside a hard drive. A good analogy: if hard drives are pies, a partition would be a slice of pie. It should be noted thought that sometimes the "slice" can be the size of the whole pie (which it is in your case).

It's useful (although not necessary) to have a basic knowledge of partitioning as a Linux user.

> **Paul Fletcher said:**
> If I put Ubuntu on drive c would this affect anything on drive d.

It shouldn't. One of the great things about partitions is that if you're not using one the data is reasonably safe from problems with the others.

It's always a good idea to back data up though, even if it's only  in case of human error.

> **Paul Fletcher said:**
> Also could I transfer the items back onto Ubuntu.

Yes. This is very easy. Ubuntu can read both NTFS and FAT32 (the types of filesystems used with Windows) by default. The process is much the same as when you moved your data your C drive to your D drive.

---

### Post by The Cog on 2011-01-24
You cannot put Linux on an NTFS or FAT partition - you have to put it on a Linux-compatible filesystem - the default these days is ext4. So if you are referring to partitions rather than drives, then you will probably have to re-format one of them.

In order to give an accurate picture of what is really on the drives, please can you use a live Ubuntu CD and capture and post the output of the command ```
sudo fdisk -l
```That last letter is a lower-case L.

---

