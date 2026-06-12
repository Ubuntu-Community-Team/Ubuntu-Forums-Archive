---
title: "New Hard Disk- which partition table type best for me"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by eshant_engineer on 2010-04-25
I have new 500GB Samsung Hard Disk with me, now I am confused in selecting new partition table type. I am going to install Ubuntu, Windows, Solaris in future, making it primary hard disk. Please suggest me suitable partition table type for creating new...which will be good in all aspect..

Thank You in advance..

[COLOR="Red"]Edit:[/COLOR]
option available are: msdos, aix, dvz, loop, sun, bsd, etc

---

### Post by cuberts on 2010-04-25
> **eshant_engineer said:**
> I have new 500GB Samsung Hard Disk with me, now I am confused in selecting new partition table type. I am going to install Ubuntu, Windows, Solaris in future, making it primary hard disk. Please suggest me suitable partition table type for creating new...which will be good in all aspect..

Thank You in advance..3 systems?
well it depends which one you want to take up the most space.
Ubuntu is usually the fastest, therefore I think you could let it take up 180 GB, Solaris is better than windows so mabye around 170, and windows 150 GB

Thats what I would do , so I hope this helped

---

### Post by eshant_engineer on 2010-04-25
Sorry..I confused u too :), I have cleared it in post

---

### Post by sisco311 on 2010-04-25
Use the standard msdos partition table. It's fully compatible and supported by Linux, Windows & Solaris.

---

### Post by TMKCodes on 2010-04-25
Do you mean partition filesystems?

NTFS for Windows
Ext4 for Linux
ZFS for Solaris

---

### Post by eshant_engineer on 2010-04-25
No..rather partition table for partitioning Hard Drive

---

### Post by srs5694 on 2010-04-25
On a BIOS-based computer, Windows can only boot from a Master Boot Record (MBR) partition table, which GNU Parted and GParted refer to as "msdos". Solaris and Linux are also happy with MBR disks on such systems, so as a practical matter, MBR is your only real choice.

In theory, you could use a GUID Partition Table (GPT) setup for a Linux/Windows dual-boot, but then you'd need to either create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) or jump through some weird hoops using [UEFI DUET](http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/e/project/ef/efidevkit/DuetRelNotes.txt) to make Windows think it's using an EFI-based system. I don't know how Solaris would react to either configuration.

If your computer happens to use EFI or UEFI firmware rather than a BIOS, you may need to use GPT, but I don't know offhand how Solaris interacts with such systems. I think I heard that Windows *must* boot from GPT on such systems, but I'm not positive of that. (I know that Windows *can* boot from GPT on EFI/UEFI-based systems.)

On an MBR disk, Windows must boot from a primary partition. (There are reportedly some awkward workarounds, but AFAIK they all involve at least one primary partition, even if Windows isn't technically installed to that partition.) Likewise for Solaris; it uses a primary partition that it then carves up using its own unique subpartitions, which are conceptually similar to logical partitions. Linux is happy on either primary or logical partitions. Thus, you'll need at least two primary partitions. Since MBR limits you to four primary partitions (or three primary partitions and one extended partition, which can then hold an arbitrary number of logical partitions), you should be careful not to use too many primary partitions if you install Linux before either Windows or Solaris.

---

### Post by eshant_engineer on 2010-04-26
Thanks for your valuable post...

---

