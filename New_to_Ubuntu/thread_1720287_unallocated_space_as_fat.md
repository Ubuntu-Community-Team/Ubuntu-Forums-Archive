---
title: "unallocated space as fat ?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-03
i have some unallocated space on my hdd and want to make it fat so as to be able to store media on it (videos,music ,blah) and want to be  able to access it on ubuntu as well as from the windows partition,
should i edit it from disk utility as 
w95 fat 32 (0x0b)
or
w95 fat 32 (LBA)(0x0c) ?

---

### Post by Bucky Ball on 2011-04-03
Don't go for fat. Inefficient and dated. NTFS much better, if you are running just Ubuntu EXT3 or EXT4.

You can boot into Ubuntu, System>Admin>Partition Manager (or Editor depending on your release), unmount the partition you want to change (unless it's free space) and format as desired.

---

### Post by coffeecat on 2011-04-03
Agreed. Use NTFS if you want it accessible in Windows as well. The FAT32 filesystem has a 4GB file size limit which might be problematic if you have large videos to store. You can use Disk Utility to create a partition formatted NTFS.

---

### Post by srs5694 on 2011-04-03
> **Bucky Ball said:**
> Don't go for fat. Inefficient and dated. NTFS much better, if you are running just Ubuntu EXT3 or EXT4.

This may be true under Windows, but I don't believe it's true under Linux, with one exception, which I'll get to shortly. I just ran a quick-and-dirty benchmark: I created a logical volume, put a FAT filesystem on it, and ran a few simple tests. I then overwrote the FAT filesystem with NTFS and ran the same tests. Here are the results (values are times in seconds, as measured with the Linux "time" command):

```

Task                        FAT        NTFS
Extract kernel source       39.914    54.795
Delete kernel source tree   1.13      5.059
Copy kernel source tarball  0.198     1.161

```

As you can see, FAT outperformed NTFS on all three tests, sometimes by a substantial margin.

An important caveat is that this was just a few quick-and-dirty tests; you'd need to do more tests, under better control than I attempted, to get a good understanding of the differences. Also, these tests were performed on empty filesystems; it's entirely possible that NTFS's performance degrades less than FAT's when the filesystems begin to fill up.

Although NTFS is a more sophisticated filesystem, with support for user-accessible features like Windows ownership and ACLs, most of these features are not accessible from Linux. Neither filesystem support *Linux*'s ownership and permissions, for instance. In fact, from a Linux perspective, NTFS has a huge problem in that there's no Linux-native filesystem check tool for NTFS. (There is a program called ntfsfix, but it does only the most minimal checks and then flags the filesystem as needing repair under Windows.) This limitation can be a minor irritant in a dual-boot system, since it can force you to reboot to Windows just to use an NTFS partition under Linux, if it was improperly unmounted. On a computer without Windows installed, it's even worse, but of course the OP has a dual-boot configuration, so it's not all that bad a problem.

The one feature I know of that's likely to be important to users in which NTFS is clearly superior to FAT is NTFS's ability to store files larger than 4 GiB in size. For the stated purpose of storing multimedia files, this could be an issue, depending on the specific files in question. An HD video, or even a long SD video, can easily exceed 4 GiB.

That said, I've written all this from a Linux perspective. Aside from the 4 GiB file-size issue, which applies across platforms, the performance and user feature issues are likely to be different in different OSes. From a Windows perspective, I'd tend to agree that NTFS is superior (although I'm not sure about FAT vs. NTFS performance in Windows). IMHO, then, the questions are how much the partition will be used from Windows vs. from Linux and whether there will be any need to store >4GiB files on the partition.

---

### Post by Bucky Ball on 2011-04-03
All good srs5694, but the main issue is:

"The FAT32 filesystem has a 4GB file size limit ..."

Not good in a world of expanding file sizes ... ;)

---

