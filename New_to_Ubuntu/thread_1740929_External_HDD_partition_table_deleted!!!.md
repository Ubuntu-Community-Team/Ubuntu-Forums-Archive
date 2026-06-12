---
title: "External HDD partition table deleted!!!"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Gondrano on 2011-04-27
Help!


First time I use GParted!

Yesterday I made a very silly thing, wanted to repartitioning via   GParted my 320giga ntfs data external hard disk (full more than half) to ext4, but I end up in a mess. I thought would be possible to substitute the ntfs with a extended file-system but indeed I only created a new partition of the same size. I shut the os down and then I restart it where was no partition table.

I attach pictures to better explain where I am now. 

In /dev I found a sdb sdb1 sdb5 reconducting to the HDD, but in GParted its space is unallocated. It does not compare in fstab.

I hope the data is still untouched! Now I wonder how to have access to it for eventually copy it in a new hard disk and then recover all back to the right partitioned first one. 

Thanks for any suggestion

---

### Post by srs5694 on 2011-04-27
First, your /etc/fstab file is fine; the "nodev" item you've highlighted on the /proc filesystem entry is perfectly normal and is unrelated to your problem.

The problem is that your /dev/sdb partition table is completely messed up:


[list]
[*]It uses a type-0x85 extended partition type. This is legal, but is very unusual. It's conceivable, though, that this unusual extended partition type confused some utility somewhere along the way, resulting in the more serious problems....
[*]The extended partition covers sectors 63-488,392,064, but the one logical partition it contains covers sectors 218,129,572-1,920,119,981. This is larger than the extended partition and it's also larger than the disk (488,397,168 sectors).
[*]The logical partition's boot flag is marked as "?". That probably indicates corruption of this data byte, which has only two legal values.
[*]The logical partition's type is listed as 0x72, or "unknown." According to [this page of MBR type codes,](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html) 0x72 is "V7/x86, a port of UNIX Version 7 to the PC." This is highly unusual. It might be legitimate, but it might be another sign of data corruption.
[*]There's nothing defined on the disk prior to the clearly mis-sized /dev/sda5. Again, this is legal, but it's suspicious.
[/list]


These problems are so severe that my only suggestion is to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to try to recover your true partitions on the disk. Alternatively, if you have no data on the disk (which you might not, if you created a fresh filesystem on it, as you seem to be saying), you could just create fresh partitions in GParted.

---

### Post by Gondrano on 2011-04-28
I said wrong, my corrupt HDD is only 250 gb.

I have tried to make an image and save it on a new 1 t HDD but it fails. 
The 1 t has two partitions one ext4 and the other ntfs. I tried to save an image on one of the two partitions listed in the testdisk GUI. Via testdisk I followed this path /media/prima. It replay there is no enough space.
I wander how to save a copy of all before recover it. 

What the command type displayed in the testdisk GUI is for?

---

### Post by Gondrano on 2011-04-28
Thank you Srs5494

Hi followed your advice and I had the ntfs partition table back using testdisk! :D

I do not succeed in make an iso but however I saw that test disk found easily again the partition, so I went head, thought it would rewrite the entire disk sector by sector, but indeed it rewrite just the partition table. Fiuu!

ps I must reformatting the 1 tera HDD, any suggestion for the file system? Maybe ext4 to avoid fragmentation, 2 partitions, but I guess one must be ntfs or?. And I wanted to do the same with the little one except all ext4.

Can you please explain me briefly pro and con of ext4? I mean which kind of file will be unwritable on it?
[COLOR=#000000]
[/COLOR]

---

### Post by srs5694 on 2011-04-28
*Any* filesystem can be used to store *any* type of file (graphics, music, plain text, etc.). The main caveat has to do with file metadata, such as ownership and permissions, which are usually lost when storing data on a non-native filesystem.

The most important differences aren't in the types of files that can be recorded on the filesystem but what OSes can read and/or write it. Windows supports only FAT, NTFS, ISO-9660, and UDF out of the box (the last two of those are for optical discs). There are ext2/3/4 drivers for Windows, but the ext4 support is very new, and based on comments I've read, even the ext2/3 support doesn't seem that great; however, I've never used these drivers myself, so I can't comment on them from personal experience.

For Linux-only use, I recommend you use a Linux-native filesystem on removable disks. Currently, ext3fs is probably best for compatibility, with ext4fs not far behind. ReiserFS, XFS, and JFS are all options, too, but they're less well-supported outside of Linux, in case that should become an issue in the future. (A couple of exceptions are noted below.)

For cross-platform use, suitable filesystems include:


[list]
[*]**FAT** -- Supported by just about everything, but it can be slow and it has a 4 GiB file-size limit that can be a problem with big backup files and multimedia files.
[*]**NTFS** -- Useful mainly with Windows, but there's NTFS support in some other OSes. Linux support is slow compared to most filesystems (even FAT), but this usually isn't a big problem.
[*]**HFS and HFS+** -- These are used by Mac OS (HFS+ requires Mac OS X), and so are good for Linux/Mac data exchange. Linux's HFS+ support is read-only by default if a journal is used, so you should use the option to create HFS+ *without* a journal if you want to use it as a two-way data-exchange volume.
[*]**JFS** -- IBM's AIX and OS/2 both support JFS (in fact, IBM wrote it and it was later ported to Linux).
[*]**XFS** -- SGI created XFS for its IRIX OS and later donated it to Linux, so XFS is good for Linux/IRIX cross-platform use.
[*]**UFS** -- This is the native filesystem for FreeBSD and several other Unix-like OSes, so you can use it for cross-platform exchange with them. Linux's read/write support has been classified as "experimental" for years, though, so you might want to use FAT instead, or check on the BSD's support for a Linux filesystem.
[/list]


There are also several more obscure filesystems available for more obscure OSes, such as BeOS, QNX, and OS/2. FAT is often a better choice for them, though, since FAT support is usually quite good in both Linux and the other OS, whereas Linux's support for the other OS's native filesystem is often a bit limited. Details vary depending on the filesystem, though.

---

### Post by Gondrano on 2011-05-05
Thanks  for your explanation, 

I have formatted the 1tera HDD (mainly for my father photos stockage) in two ntfs partitions. I must say that I tried to make 2 ext4 partitions but every time the result was two partitions with a mixture of ext4,ext3 and some 24giga for each one unreachable (presumably ext3). 

Possibilities could be two: 1. the HDD WD ELEMENTS SE is not compatible with GNU/Linux or 2. I corrupted some sectors trying to copy an image of the entire 250 (~130giga) disk before recover it with testdisk, but every time I tried to make an image it said error after a couple of minutes.

For the little personal Hdd I feel better format it in ext4, so the interior space will be better organized. (no fragmentation, sector optimization...)

---

### Post by srs5694 on 2011-05-05
It's impossible to have a single filesystem that's a "mixture of ext4,ext3." Ext4fs is the latest generation of the filesystem line that began with the extended filesystem (extfs; now extinct), then became the second extended filesystem (ext2fs), then ext3fs, and now ext4fs. It's possible that some older utilities would identify an ext4 filesystem as being an ext3 filesystem; or there could even be a buggy program that misidentifies ext3fs as ext4fs. It's also possible to manually tweak filesystem features to turn off some of the advanced ext4fs features, producing something that's somewhat in-between the two; but that would still be an ext4 filesystem, just with some features disabled. Since you don't say why you thought you had a mixture of ext3fs and ext4fs, I can't do more than point out that this is impossible; you'll need to be more specific if you want to know the true meaning of whatever led you to this conclusion.

The issue of 24 GB being "unreachable" could relate to any of several factors:


[list]
[*]Measurement units -- Gigabytes (GB; 10^9 bytes) vs. gibibytes (GiB; 2^30 bytes), and similarly for other units. By and large, people don't understand the difference, and some tools incorrectly report GiB as GB. Hard disk sizes are usually measured in power-of-10 units, so a 1.00 TB hard disk is actually 0.909 TiB (or 931 GiB). There's no lost space here, any more than there's lost distance when converting a measurement of, say, 100 yards to 91.4 meters.
[*]Reserved space -- The entire ext2/3/4fs family reserves 5% of available disk space for use by root, by default. Thus, on that 1TB/931GiB drive, 50GB/47GiB will be reserved for root. Some utilities remove this space from "available space" estimates, but others don't, which can lead to confusion.
[*]Filesystem overhead -- All filesystems reserve some space for their own use. Usually the quantities are quite small. The journal file is probably the biggest such consumer of space on journaled filesystems. I don't know offhand how big it would be on a 1 TB filesystem, but it could be big enough to be noticed.
[/list]


Since you say you created two partitions, each of which was missing 24 "giga," I'm guessing that most of that was in the 5% reserved space. (5% of 500 GB is 25 GB, or 23.3 GiB.) This space can be "unreserved" by using the tune2fs utility and its -m option, or at filesystem creation if you use mke2fs and some of its advanced options, such as -m.

You can't physically damage sectors on a hard disk just by copying data to them, unless the drive is in the process of failing. You can, of course, overwrite data in sectors, which can damage files or filesystems. Beyond that, I can't comment on your problems recovering data with testdisk, since you haven't been very clear about what happened. Posting *exact* descriptions of what you did and *exact* error messages is critical in diagnosing such problems; reports such as "it said error after a couple of minutes" are pretty unhelpful.

---

### Post by Gondrano on 2011-05-07
Thanks to be so precise and to reserve time and energies to fill my ignorance.
Sorry if I did not reported the exact words of testdisk when its said that there was a failure in copying the image. I also was really stupid because every time I have tried to do it I always created a new log file. So the last one is just for recovering the disk (without create an image on another hdd).

Once I recover the 250 GB I tried to create two partitions and I think it is how you wrote (2 option: reserved space) . As a newbie I found it quite strange. Every day I learn something new.

ps when I right clicked with the mouse on each partition icon, it just showed me two colored (blue and yellow) areas. The small one of 24GB. And as file-system it was ext4,ext3.

pss I always make a mess with measurements units!

---

### Post by Gondrano on 2011-05-07
Ups, forgot to upload the log file! :)

---

