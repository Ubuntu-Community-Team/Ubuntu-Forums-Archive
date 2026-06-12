---
title: "Partition for mp3"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by dlion64 on 2009-04-19
I want to dual boot Windows and Ubuntu. Can i make a partition for my music to where windows and ubuntu will both read it. And if so what format should I make it? Would Fat 32 work or is that a bad idea?

---

### Post by halitech on 2009-04-19
Linux can read anything MS puts out but MS can't read Linux partitions without third party software. If it will be files under 4gig then Fat32 would be fine. If you think you might put something over 4gig on it, got NTFS.

---

### Post by Paqman on 2009-04-19
> **dlion64 said:**
> Would Fat 32 work or is that a bad idea?

It would work, but FAT32 suffers from heavy fragmentation. If you're not changing the data on that partition much then that wouldn't be a problem at all.

NTFS is a good option if you want a partition that both systems can use, that is more durable than FAT32.

If you decide to use NTFS, install the package ntfs-config. It'll get that partition mounted without having to hack into your /etc/fstab manually.

---

