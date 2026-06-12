---
title: "fdisk issue"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by coolmego on 2011-04-08
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6092    48929792   83  Linux
/dev/sda2   *        6092       13417    58838016    7  HPFS/NTFS
/dev/sda3           13417       26165   102400000    f  W95 Ext'd (LBA)
/dev/sda4           26165       38914   102400000    7  HPFS/NTFS
/dev/sda5           13417       26165   102398976    7  HPFS/NTFS
 What is the meaning of System part of /dev/sda3 and if looked closely it can be seen that they have the same start value but have different blocks..How can two partitions have the same start block..????

---

### Post by coolmego on 2011-04-08
I mean /dev/sda3 and /dev/sda5 have the same start no but have different block numbers..

---

### Post by Rubi1200 on 2011-04-08
Which fdisk command did you run; with the -l switch?

Run this and then post the output:

```
sudo fdisk -lu
```

---

### Post by srs5694 on 2011-04-08
Don't bother with Rubi1200's command; it's necessary to diagnose certain problems, but you haven't reported any such problem.

The original Master Boot Record (MBR) partition table can hold just four partitions. That soon became inadequate, so an extension/hack to MBR soon came into being: One of the four primary partitions became an *extended* partition, into which an arbitrary number of *logical* partitions could be placed. Your /dev/sda3 is an extended partition. Linux's fdisk identifies it as a "W95 Ext'd (LBA)" because it's a specific type of extended partition that was first used by Windows 95.

Because /dev/sda3 is an extended partitition, all your logical partitions (in your case, just /dev/sda5) must reside entirely within it. This appears to be the case for you, although your fdisk output is precise only to cylinder values, not to the sector, as you seem to believe. Rubi1200's command would show sector-precise values, and that would probably show /dev/sda5 starting at least one or two sectors after the start of /dev/sda3. Unless you're experiencing a disk problem, there's no need to bother posting this output, though. (If you *are* experiencing a problem, please describe the symptoms.)

---

