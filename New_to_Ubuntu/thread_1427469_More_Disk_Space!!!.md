---
title: "More Disk Space!!!"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Rey117 on 2010-03-11
I have a question..Can you allocate or partition more disk space for Ubuntu? I'm currently running Ubuntu 9.10.

---

### Post by lotharmat on 2010-03-11
That would depend on how the HD is configured.

Please can you post the results of 

```
sudo fdisk -l
```

That is a lowercase L not a 1 btw!

---

### Post by Rey117 on 2010-03-11
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f6bbd80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       31075   248070144    7  HPFS/NTFS
/dev/sda3           31076       38913    62958735    5  Extended
/dev/sda5           31076       38587    60340108+  83  Linux
/dev/sda6           38588       38913     2618563+  82  Linux swap / Solaris

---

### Post by audiomick on 2010-03-11
What is on sda2? Is that a windows installation? If so, which windows is it?

---

### Post by Rey117 on 2010-03-11
Sda2 is my Windows Vista Home Premium 64 Bit

---

### Post by philinux on 2010-03-11
> **Rey117 said:**
> Sda2 is my Windows Vista Home Premium 64 Bit

What does this show.

```
df -h
```

The safe way is to use vista disk tools to shrink your windows partition to make more space on your hard drive. Then use the livecd and gparted to increase your ubuntu partition.

As always backup backup backup, moving/resizing can go wrong. And clean up windows of fluff and defrag windows twice first.

---

### Post by audiomick on 2010-03-11
Ok. I have seen recommendations here that you should use windows tools to re-size Vista and Win7 partitions. I think Vista comes with a partitioning tool.
You need to clean out anything superfluous in the windows install.
De-frag the windows partition at least once, better twice.
Shrink the windows partition (I think it is around 250GB at the moment) using the windows tool such that the free space is after the windows partition, i.e. adjacent to sda3, the extended partition.
Start windows a couple of times, and let it do any disk checking it wants to do.

Boot into the Ubuntu Live Cd and start gparted
system> administration> gparted.
Expand sda3, the extended partition into the empty space created by shrinking the windows partition.
Expand sda5 into the free space that is now inside the extended partition.

edit: philinux beat me again...;) He's right, I forgot to say backup anything important before you start.

---

### Post by Rey117 on 2010-03-11
I will do this later tonight because I'm dorm right now and heading for class so when I get back after class I will do this. Thanks I didn't think I would get a response this fast!!! Thanks!!!

---

