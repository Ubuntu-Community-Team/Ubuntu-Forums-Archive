---
title: "Best way to re size my Partition"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2009-08-14
Sorry this may seem like a silly one! 
but is it possible to partition my hard drive which is solely running ubuntu while booted into it using g parted!
i'd like to choose a specific size partition to also try another small OS, its a cloud OS called gOS-3.1... 
I've always had trouble with the manual partitioner when you install ubuntu and don't feel i would be able to partition the size i want without wiping the whole lot and starting a fresh but i don't want to do that... or perhaps is there something i missing here..
Any help would be greatly appreciated,

---

### Post by rbc on 2009-08-14
> but is it possible to partition my hard drive which is solely running ubuntu while booted into it using g parted!
No. The Ubuntu partition is mounted, and you cannot use GParted on a mounted partition. You will have to use the Ubuntu Live CD (or any other distro's CD) or Gparted Live, or whatever partition manager you want.

---

### Post by adempewolff on 2009-08-14
you could also download virtualbox and try out the new os without messing with partitions!

---

### Post by drs305 on 2009-08-14
Back up your important data.

Use the LiveCD, then System, Administration, Partition Editor to open Gparted. Be sure to unmount the swap partition (highlight it, then select Partition, Swapoff).

You can now shrink your ubuntu partition to create additional partitions. If you plan on having more than 3, make sure the 4th is an 'extended' partition and then make additional partitions (logical partitions) within it.

---

### Post by LewRockwell on 2009-08-14
.

Re: Partitioning

Search Terms: Ubuntu Disk Partitioning Tutorials Wiki

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

.

---

