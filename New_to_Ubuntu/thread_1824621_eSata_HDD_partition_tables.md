---
title: "eSata HDD partition tables ?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by neil_1 on 2011-08-14
I have just bought a new internal HDD and want to use it externally by esata,
how to i go about making a partition table for it ?
it is only recognized in gparted and fdisk

edit:
i want it to have an ntfs filesystem 
how do i do this?

---

### Post by neil_1 on 2011-08-15
anyone knows?

---

### Post by aeiah on 2011-08-15
use gparted to create an ntfs partition?

---

### Post by jmore9 on 2011-08-15
donload and make yourself a copy of gparted live and boot into it.  Works like a charm with NTFS and linux parts.

---

### Post by neil_1 on 2011-08-17
> **aeiah said:**
> use gparted to create an ntfs partition?
yes but before that it asks which type of partition tables the hdd needs ?
msdos and some other choises. should i chose msdos ?
> **jmore9 said:**
> donload and make yourself a copy of gparted live and boot into it.  Works like a charm with NTFS and linux parts.
sorry what ?:S

---

### Post by westie457 on 2011-08-17
Hi.

There are a few factors to be taken into consideration about which partition table to use.

1 The size of the HDD. Up to 1TB the MS-DOS partition table is sufficient. Over 1TB it should be a GPT- type partition table.

2 The number of partitions that are likely to be used on the HDD. 
   The MS-DOS table allows a maximum of 4 primary partitions (any of which may be an extended partition. An extended partition can contain (in theory) up to 128 logical partitions.
   The GPT table allows more than 4 Primary partitions which can have the same characteristics mentioned above.

3 Personal choice. You can have either of the above but not both at the same time.

4 Gparted works best with a MS-DOS partition it can work with a GPT table.

5 A GPT-table needs different tools to be able be set up correctly.

---

### Post by srs5694 on 2011-08-18
> **westie457 said:**
> 1 The size of the HDD. Up to 1TB the MS-DOS partition table is sufficient. Over 1TB it should be a GPT- type partition table.

Actually, the Master Boot Record (MBR; aka "msdos" and various other names) partition table is perfectly adequate for disks up to 2^32 sectors, which works out to 2 TiB (2 tebibytes), not 1 TB (1 terabyte), assuming 512-byte sectors. Since 2 TiB = ~2.2 TB, as a practical matter, this means that MBR is fine for all disks on the market today except for some 3 TB models. MBR is even adequate on some external 3 TB models, some of which use 4096-byte sectors, which raises MBR's limit to 16 TiB.

For some reason the Ubuntu installer switches from MBR to GPT when given a completely blank disk that's between 1 TB and 2 TB (I don't know the exact cutoff value). I don't know why the developers chose this value rather than MBR's true limit of 2 TiB.

> 2 The number of partitions that are likely to be used on the HDD. 
   The MS-DOS table allows a maximum of 4 primary partitions (any of which may be an extended partition. An extended partition can contain (in theory) up to 128 logical partitions.

The theoretical limit on logical partitions is about half the number of sectors on the disk, which works out to about 2 billion on a 2TB disk (assuming 512-byte sectors). Practical and OS-specific limits are lower, but I've created disks with over 128 logical partitions, just as a "proof of concept." IIRC, Ubuntu's got a limit of 16 partitions, but that's an Ubuntu-specific limit.

> The GPT table allows more than 4 Primary partitions which can have the same characteristics mentioned above.

The only "characteristic" you specified for primary partitions is that one can be an extended partition. The concepts of extended and logical partitions are unique to MBR disks; GPT disks don't use these hacks. In their absence, the word "primary" in "primary partition" becomes meaningless, so although GPT partitions are analogous to MBR primary partitions in certain ways, GPT partitions are simply "partitions." GPT supports up to 128 partitions by default, but this value can be raised should the need arise, given suitable partitioning tools.

---

### Post by neil_1 on 2011-08-21
Thanks westie457 :D
my HDD is up and running now :)
Thanks for the explanation srs5694 :)

---

