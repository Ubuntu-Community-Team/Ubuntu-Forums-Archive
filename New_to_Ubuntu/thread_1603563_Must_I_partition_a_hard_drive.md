---
title: "Must I partition a hard drive?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by paker on 2010-10-22
Is partitioning basically dividing the space to 2 or more sections? If I want to use the entire space, do I still have to partition the HD? Partition of 1?

The HD is an external usb device, 2 TB, for not-so-important video and audio files. I don't need to divide the space.

Thanks.

---

### Post by macem29 on 2010-10-22
if the external drive is for storage only then no, it does not need to be partitioned, it will need to be
formatted in a way that the OS can use it however, but most are usable out of the box with ubuntu

---

### Post by srs5694 on 2010-10-22
It's possible, but not generally advisable, to use a disk as a "raw" device without partitioning it. Partitioning a disk, even a disk that has just one filesystem, gives it a format that's expected. This might be important in some situations. For instance, I doubt very much if a non-Linux OS installer would recognize an ext2/3/4 filesystem on a raw disk; but such an installer is much more likely to recognize that a disk has been partitioned and allocated entirely to Linux. This could make the difference between successfully installing such an OS and having it accidentally wipe out your Linux data files.

Furthermore, partitioning the disk now, even into just one partition, means that you'll be able to shrink that partition to make room for a second in the future, should the need arise. If you don't partition now, such a future change will be much harder, although not impossible.

Partitioning consumes very little disk space. In theory, it could consume as little as one sector (512 bytes) of the hard disk, although in practice it's likely to take more than that -- perhaps slightly over 1 MiB with modern partitioning standards. Given modern disk sizes, that's very little space to give up to get a more flexible and (at least in theory) better supported system.

---

### Post by paker on 2010-10-24
Thanks for the explanation. Now I see I can go either way, but partitioning seems to lose little for potential gains in the future. I will partition the HD.

---

