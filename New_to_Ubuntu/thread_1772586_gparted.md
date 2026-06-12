---
title: "gparted"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-05-31
I opened Gparted from USB drive.

unallocated.
sda1.
sda2.
sda3.
sda4.
what is unalocated one for?

---

### Post by scradock on 2011-05-31
> **Matrix01 said:**
> I opened Gparted from USB drive.

unallocated.
sda1.
sda2.
sda3.
sda4.
what is unalocated one for?

"Allocated" space has been marked as part of a partition, such as sda1.

The "unallocated" space has for some reason been left un-marked, and probably un-formatted too. If there's a lot of it, think about how it might be recovered. If it's only a small part of the disk (1% or less), forget about it.

I have an elderly HD with 250MB unallocated at the beginning, ever since I started losing partition tables (which are stored at the beginning of a partition). I simply told gparted to start the first partition 250MB into the disk surface, thus avoiding putting anything useful on that part of the disk.

---

### Post by Matrix01 on 2011-05-31
HP mini has 150 GB of hard drive space, 
and unallocated one has 1 MiB.
so...it seems to be insignificant.

---

### Post by srs5694 on 2011-05-31
> **scradock said:**
> I have an elderly HD with 250MB unallocated at the beginning, ever since I started losing partition tables (which are stored at the beginning of a partition).

It's unclear precisely what you mean by this comment about "partition tables [being] stored at the beginning of a partition," but I suspect you might be misunderstanding something. Even if you're not, there are some changes in the works, so in the interests of improving peoples' understanding....

In the common Master Boot Record (MBR) partitioning scheme, the *primary* partitions (including the *extended* partition, if the disk has one) are defined in the first sector (usually 512 bytes) of the hard disk. The first partition has traditionally begun on sector 63, although this value can vary, and today it's more likely to be sector 2048 (1 MiB from the start of the disk). Thus, leaving 250 MiB of unallocated space won't help protect the primary partitions; given the way computers make mistakes, a computational error would be as likely to accidentally write data 250 MiB early as 1 MiB early.

The MBR scheme also supports *logical* partitions, which are stored inside the extended partition. Logical partitions (and their extended-partition carrier) were invented as a workaround to the MBR 4-partition limit. These partitions are defined differently; the first sector of the extended partition contains a data structure called the Extended Boot Record (EBR), which defines the first logical partition in the extended partition. The EBR also includes a pointer to the next EBR, which defines a partition and a pointer, and so on until the last logical partition's EBR, which defines just the partition and has no pointer. Normally, the EBR appears a few sectors before the partition it defines -- but not *in* the partition itself. That first EBR, though, does appear at the start of the extended partition, and all the rest are of course contained within it, although not at its start. If you lose an EBR, you'll lose the partition it defines and all subsequent logical partitions. Thus, accidentally writing to an extended partition could be a very damaging thing to do. Adding unallocated space between the start of the disk and the first partition, or even between the start of an extended partition and the first logical partition it contains, would be unlikely to improve reliability.

All of this is changing, though. MBR has a size limit that works out to 2 TiB with 512-byte sectors (or proportionally larger with larger sector sizes). Its replacement is known as the GUID Partition Table (GPT), and it uses an entirely different structure. GPT includes a *protective MBR* (which is basically just designed to alert GPT-unaware utilities to the fact that the disk is in use), a sector with a set of GPT metadata, and then several sectors in which partitions are defined (up to 128 by default, although this value can be changed). The GPT metadata and partition definitions are duplicated at the end of the disk. This arrangement provides some security in case of an accidental overwrite of either the main or backup partition data. In theory, a buggy partitioning program could write partitions that overlap with the GPT data, but such damage would likely be quickly detected, particularly if data were written to the affected sectors, since GPT also includes CRCs of the GPT data, enabling OSes and utilities to detect damaged GPT data structures.

Thus, in theory GPT is less susceptible to damage than is MBR. In practice, time will tell. It's certainly easy enough to damage a GPT disk through inappropriate use of a partitioning tool or because of a buggy partitioning tool. (The same is true of MBR, of course.)

For either partition type, you can back up your partition data so that if something trashes the partition table, you can easily recover. For MBR, you can use sfdisk for this:

```

sudo sfdisk -d /dev/sda > sda.txt

```

This command saves the partition definitions (for primary, extended, and logical partitions) in sda.txt. You can then save it to a removable disk and, if your partitions are damaged, restore them:

```

sudo sfdisk -f /dev/sda < sda.txt

```

For GPT, you can use [url=http://www.rodsbooks.com/gdisk/]GPT fdisk (gdisk and sgdisk):

```

sudo sgdisk -b sda.gpt /dev/sda

```

This backs up the partition data; and you can restore it with another command:

```

sudo sgdisk -l sda.gpt /dev/sda

```

You can do this from the interactive gdisk program, too, using the "b" command on the main menu to back up and the "l" command on the recovery & transformation menu to restore.

[quote=Matrix01]HP mini has 150 GB of hard drive space, 
and unallocated one has 1 MiB.[/quote]

That's probably an effect of the new 1 MiB (2048-sector) alignment policy of most partitioning tools. The standard has changed from sector 63 to sector 2048 because of the needs of Advanced Format disks, certain types of RAID arrays, and SSD drives, which can suffer from performance problems if partitions are not aligned to whatever boundary is appropriate. These are power-of-2 multiples of sectors and vary from 8 sectors (for Advanced Format) to at least 512 sectors (256 KiB), and perhaps more. A 1 MiB alignment policy works for all these disk types, so it's a safe default. On disks that don't need this type of alignment, there's the tiny cost of slightly less than 1 MiB of lost space at the start of the disk, but that's pretty trivial. This new type of alignment is being done on both MBR and GPT disks, BTW.

Recent versions of GParted don't bother to report small gaps like that, presumably to avoid confusing users who don't understand why they appear. Older versions sometimes show them.

---

