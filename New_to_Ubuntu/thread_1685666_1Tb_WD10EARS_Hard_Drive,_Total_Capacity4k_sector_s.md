---
title: "1Tb WD10EARS Hard Drive, Total Capacity/4k sector size questions."
date: 2011-02-11
forum: New to Ubuntu
---

### Post by schlidel on 2011-02-11
I have a 1Tb Western Digital WD10EARS (which is a 4k sector drive) but Ubuntu 10.10 shows only 911.GB total capacity (in Disk Usage Analyzer), is this correct? Windows 7 showed 930Gb capacity, I believe.

I swear I checked it a minute ago and it said 860GB available so that's when it got real bad and I decided to open this thread.

I can live with 911Gb total capacity, but if this number fluctuates I'll become concerned.

Is this normal? Also, how do I check that this drive is being utilized correctly with the 4k sector size technology?

Thanks!

---

### Post by ajgreeny on 2011-02-11
1.  Manufacturers seem always to work on sizes in 1000 base, ie a megabyte is 1000 Kb, a GB is 1000 MB etc etc so the difference on a huge drive supposedly of a TB or above is pretty large, which could account for the first difference you see.

2.  The ext# file systems reserve a 5% slice of the drive as unavailable to allow for the journaling and fsck file checks, so a drive appears used by that 5% even when there is nothing on it, perhaps accounting for the second difference.

Keep looking at the size detected over a longer time period and I suspect it will remain the same.  If not, I can't imagine what is going on, or why it keeps changing.

---

### Post by mcduck on 2011-02-11
Actually the 5% isn't reserved for journaling & fsck, it's reserved for the system & root user, to prevent normal users from filling the drive up to the point where Linux can't create the files it needs when booting.

(if you check the available disk space as root, you'll see it reporting larger amount than you see as a normal user.)

The reserved amount can be changed, 5% of a 1TB drive is quite a lot and way more than the system would actually ever need to be able to boot, but in the end you might not want to. While Ext filesystems aren't nearly as vulnerable to fragmentation as FAT & NTFS are, it still does happen, and the performance will start dropping quickly when the drive gets too full. So you'd never actually want to fill the drive even up to the 95%, not to mention going beyond that.

But the part about hard drive manufacturers using 1000 as multiplier is correct. Computers on the other hand actually use 1024 as a multiplier for kilos, megas etc, since they operate on binary mathematics, not base-10 like us humans do. So the way how different programs and tools report sizes (nad the usage of GB vs GiB as unit name, for example) can vary a bit, and in the end you'll often just have to calculate it yourself to see what's actually happening.

edit:

A Hard drive manufacturer counts 1TB drive to be 1000GB, or 1000000 MB, 1000000000 KB, or 1000000000000 bytes.
On the other hand, calculated the same way the computer uses the space (and how, for example, RAM works), things are bit different:
1000000000000B = 976562500 kiB = 953674 MiB = 931 GiB = 0,9 TiB

---

### Post by schlidel on 2011-02-11
I found where I was getting that 860Gb number from.

In System Monitor it lists:

 total - 911.1Gb
 free - 904.8Gb
 Available - 858.5Gb

This last number is unacceptable, especially since Windows sees 930Gb as usable.

---

### Post by coffeecat on 2011-02-11
I have a WD 10EADS 1TB drive which is probably the same size as yours. The output of fdisk shows this to be 1000204886016 bytes which is a little over 1TB. In Gib (gibibytes - 1GiB = 1024 x 1024 x 1024 bytes), the size is 931.5, so Windows is reporting GiB, not GB.

Disc Usage Analyser is badly named - it analyses filesystems, not disks, which can be a different matter. I guess the 860 is the 930 less the journalling that others mention, less your swap partition and less anything else you might have on the disc. Disk usage Analyzer is telling you about your system's filesystem, not the physical drive. If you have just one root partition, no home partition and no other partition mounted, then it's telling you about your root partition only, which is smaller than the physical drive.

System Monitor  shows the partitions, not the total drive, so you will get similar figures. Use Disk utility or Gparted or terminal commands such as fdisk to look at the whole drive.

---

### Post by mcduck on 2011-02-11
> **schlidel said:**
> I found where I was getting that 860Gb number from.

In System Monitor it lists:

 total - 911.1Gb
 free - 904.8Gb
 Available - 858.5Gb

This last number is unacceptable, especially since Windows sees 930Gb as usable.

And what is the value for used space (meaning the OS, installed programs + all your personal files). Also read the above posts about difference in how the space is calculated, and the 5% of space reserved for system & root user.

The value seems correct, assuming you got those readings as a normal user.

---

### Post by mcduck on 2011-02-11
> **coffeecat said:**
> 
Disc Usage Analyser is badly named - it analyses filesystems, not disks, which can be a different matter.

Depends on how you look at it. ;)

It doesn't actually analyze filesystems either, it analyzes the *disk usage of files*. As in how much space the files take, and how much that is compared to total amount of used space & the space used by the parent directory.

---

### Post by coffeecat on 2011-02-11
> **mcduck said:**
> Depends on how you look at it. ;)

It doesn't actually analyze filesystems either, it analyzes the *disk usage of files*. As in how much space the files take, and how much that is compared to total amount of used space & the space used by the parent directory.

Fair point, I was oversimplifying. :) But it says, "Total Filesystem capacity" and then gives a figure which can be misleading if you don't know what it's talking about. The important thing is that  the OP is getting muddled between partitions, filesystems and discs.

---

### Post by srs5694 on 2011-02-11
Others have provided good comments. I'd just like to add that none of this has anything to do with the specific model hard disk you've got or the fact that it's an Advanced Format drive; those details are buried several layers deep in the abstractions between the 1s and 0s on the disk platter and the files you see and manipulate with your file manager.

One more point....

> Also, how do I check that this drive is being utilized correctly with the 4k sector size technology?

You should check that all your primary and logical partitions begin on 8-sector boundaries. You can do this by typing "sudo parted /dev/sda unit s print". Change /dev/sda to /dev/sdb or whatever's appropriate. The result will resemble the following:

```
$ **sudo parted /dev/sda unit s print**
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start     End          Size         File system  Name                  Flags
 1      40s       439s         400s                      BIOS boot partition   bios_grub
 2      440s      410039s      409600s      fat16        EFI System            boot
 3      410040s   819639s      409600s      ext2         Linux /boot (unused)
 4      819640s   1229239s     409600s      ext2         Linux /boot (unused)
 5      1229240s  1953525134s  1952295895s               Linux LVM             lvm

```

Examine the values under the "Start" column. (You can ignore any extended partitions; you're only interested in primary and logical partitions.) If they're all multiples of 8, you're set. This example is fine, since all the Start values are multiples of 8.

If you find that any partitions do *not* begin on 8-sector boundaries, you can either delete and re-create the partition(s) (obviously easiest if you've not yet stored lots of files on it) or use GParted or some other tool to move/resize the partition to an appropriate boundary. Bad alignment will result in degraded performance, particularly when writing large numbers of small files. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic a few months ago.

---

### Post by extremis11 on 2011-10-20
So, if i get it right the extended partition doesn't have to be aligned, right? But it wouldn't hurt if it is, just to make disk utility stop complaining about it. Also, if i moved the boot partition at the start of disk or resized it and reinstalled Ubuntu would that make the disk unbootable?


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x677f9038

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   314983913   157286133    7  HPFS/NTFS/exFAT
/dev/sda3       314984446  1434222591   559619073    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1434222592  1465149167    15463288   12  Compaq diagnostics
/dev/sda5      1373403136  1434222591    30409728    7  HPFS/NTFS/exFAT
/dev/sda6       314984448   323373055     4194304   82  Linux swap / Solaris
/dev/sda7       323375104   637947903   157286400   83  Linux

Partition table entries are not in disk order

---

### Post by coffeecat on 2011-10-20
> **extremis11 said:**
> But it wouldn't hurt if it is, just to make disk utility stop complaining about it. Also, if i moved the boot partition at the start of disk or resized it and reinstalled Ubuntu would that make the disk unbootable?

If you mean sda1, that looks as though it's your Windows 7 boot partition, assuming your have Windows 7. If you remove/move that you will make Windows unbootable.

I suggest you start your own support thread with a suitable title.

---

### Post by nothingspecial on 2011-10-20
This thread is old.

Closed

---

