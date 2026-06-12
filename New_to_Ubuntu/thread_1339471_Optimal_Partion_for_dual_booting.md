---
title: "Optimal Partion for dual booting"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-11-27
Hi,

I just ordered a new Laptop (320GB Hardrive). I want to dual boot Windows and Ubuntu with a shared partition for Data. Which file system format would be ideal for the Data Partition? I heard that ntfs/fat32 is less ideal for  indexing my Ubuntu system. I'll figure out the sizes of the partitions myself, but which file system should I use. Should I use Wubi or is a more manual approach better, I have no problem using a partition Live-CD or the terminal.

Thanks for your answers
Andreas

---

### Post by Marvin666 on 2009-11-27
If windows is reading it too then ntfs is a good choice. When I was running a dual boot, I had 4 partitions. 2 for xubuntu ext3 ans swap, 1 for windows ntfs, and a ntfs partition I kept important files in, and used with both. It never gave me troubles.

---

### Post by coffeecat on 2009-11-27
> **Djalmahal said:**
> Which file system format would be ideal for the Data Partition? I heard that ntfs/fat32 is less ideal for  indexing my Ubuntu system.

Don't bother with FAT32 for an internal partition these days. NTFS read-write is reliable in Ubuntu and you've got Windows to repair the filesystem if the journal gets damaged.

If you come across recommendations to use an ext2/3 Windows driver so that you can use a Linux filesystem for the data partition, be very cautious. There's been a problem for the last year or so in that ext3 filesystems now default to 256-byte inodes whereas the drivers (or one at least) can only cope with 128-byte inodes. And, personally, I wouldn't let these drivers anywhere near my ext4 partitions.

---

### Post by alzie on 2009-11-27
When I was dual booting I had no issues with either NTFS or FAT32 with Ubuntu.  Windows seems to work better with NTFS.

As for choosing between a regular install or WUBI, definitely use NTFS,  FAT32 has a limited virtual hard drive size with WUBI.  I'm not sure if you can access your WUBI install if Windows breaks for some reason.  

I am currently using a WUBI install with no issues but it seems many in the forums feel that a full install is more robust.

I hope this helps

---

### Post by Djalmahal on 2009-11-27
Thanks for your input, looks like I'm going for the manual install with an NTFS Data Partition.

---

