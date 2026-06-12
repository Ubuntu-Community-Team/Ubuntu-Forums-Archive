---
title: "The drive I am using shows up in Gparted as unpartitioend space???"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by powel212 on 2009-09-20
Hi guys

I have 3 drives in my machine.

One boot drive, (300G), and 2 - 1000Gig Drives.

I am using all 3 drives and they all show up in nautilus and I can make changes to the files on all 3 drives but one of the drives shows up in Gparted as unallocated space.

Why?

Here is the output of fdisk

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf117f117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10597    85120371    7  HPFS/NTFS
/dev/sda2           10598       19732    73376887+  83  Linux
/dev/sda3           19733       37724   144520740   83  Linux
/dev/sda4           37725       38913     9550642+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b98637

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
224 heads, 19 sectors/track, 459004 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Disk identifier: 0xd729843d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      459005   976759808    7  HPFS/NTFS
```

Any help is appreciated

Powel

---

### Post by egalvan on 2009-09-21
> **powel212 said:**
> 
3 drives in my machine.

One boot (300G), 2 - 1000Gig Drives.

one shows up in Gparted as unallocated space.

Why?

Here is the output of fdisk
**WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.**



This is probably the reason...

---

### Post by powel212 on 2009-09-21
Thanks

> WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Is there another partitioning tool that can read the GPT? I mean a GUI based partion editor?

Powel

---

### Post by egalvan on 2009-09-22
> **powel212 said:**
> Thanks

Is there another partitioning tool that can read the GPT? I mean a GUI based partion editor?


sorry about the delayed response, I had to work...
but I'm back...

The latest gparted can manage GPT...
Ubuntu distros don't always have the latest...
Hardy LTS is at 0.3.5, Jaunty is at 0.4.3

you can either download a gparted liveCD
the latest being  5 August 2009 : GParted 0.4.6
on the website

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)


or download a mini-distro that keeps up with the latest,
such as partedmagic, which is using gparted-0.4.6

partedmagic.com

partedmagic is a great mini-distro, which can do much more than just partition drives...
it's a rather full distro in it's own right, yet small enough to allow constant downloads to keep up with the latest.
I use it all the time;
the authors actually listen to use input,
so I donate $2 a month (subscription).


And one final thought...
gparted is just one part of the 'tool-chain' that is used to access files...
the entire 'chain' needs to be aware of GPT to have full use of it.

ErnestG

---

