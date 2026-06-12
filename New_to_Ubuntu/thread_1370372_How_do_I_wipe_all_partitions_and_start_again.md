---
title: "How do I wipe all partitions and start again?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-02
Hi All

I have set up a dual boot that seems to be working fine, but there is a stubborn Windows Vista Loader that will not go away no matter what I do with GParted.

(My dual boot is Windows 7 and ubuntu 910 - vista came pre-installed).

If i re-install windows and allow it to take the entire disk - and then later on shrink the partition, will that work?

Thanks!

---

### Post by ikt on 2010-01-02
> **listerdl said:**
> If i re-install windows and allow it to take the entire disk - and then later on shrink the partition


Yeah that should be fine, a guide for the whole process can be found here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Bartender on 2010-01-02
Creating a partition for Windows out of the space that you want it to use up is a more elegant solution.  

Wipe the drive clean with a GParted LiveCD.  Then create a primary partition, formatted as NTFS.  Make it half the drive, or a third of the drive, or whatever size you want to use to keep Windows in its corral.  Then create an extended partition out of the rest of the drive.  Leave the space inside the extended unallocated, or create one or more logical partitions formatted as ext4, whatever. 

When you toss the Windows installer disc in and boot from it, it'll see the NTFS partition.  You should be able to install to just that partition.

---

