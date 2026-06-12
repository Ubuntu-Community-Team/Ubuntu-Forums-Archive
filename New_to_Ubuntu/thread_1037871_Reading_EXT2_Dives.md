---
title: "Reading EXT2 Dives"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Crabro on 2009-01-12
I have a D-Link DNS-323 configured in RAID1 (mirrored) mode. D-Link say that when the drives are formatted, they are formatted as EXT2 drives.

I am running ubuntu 8.10 AMD64.

Although the drives are mirrored, if the enclosure fails, I would need to read the drives directly to recover data. To test this, I removed a drive from the enclosure and attached it to my PC, then rebooted.

Although the drive showed up in Nautilus, it was not the correct size, and I could not see any of the test directories and files I had copied to it.

I tried the second drive with similar results.

Any pointers to what I am doing wrong, please?

Thanks in advance,

Dick

---

### Post by Bachstelze on 2009-01-12
Please paste the output of

```
sudo fdisk -l
```

---

### Post by Crabro on 2009-01-12
> **HymnToLife said:**
> Please paste the output of

```
sudo fdisk -l
```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93659365

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       24792   168425460    f  W95 Ext'd (LBA)
/dev/sda5            3825       19122   122881153+  83  Linux
/dev/sda6           19123       23979    39013821   83  Linux
/dev/sda7           23980       24792     6530391   82  Linux swap / Solaris

This is without the EXT2 drive attached.

Dick

PS I have to visit a customer, back later. Thanks.

---

### Post by Bachstelze on 2009-01-12
> **Crabro said:**
> 
This is without the EXT2 drive attached.


We need it *with* the disk attached. ;)

---

### Post by Crabro on 2009-01-12
Ok, I have delayed my customer visit ;-)

Without the EXT2:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93659365

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       24792   168425460    f  W95 Ext'd (LBA)
/dev/sda5            3825       19122   122881153+  83  Linux
/dev/sda6           19123       23979    39013821   83  Linux
/dev/sda7           23980       24792     6530391   82  Linux swap / Solaris

With the EXT2:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93659365

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       24792   168425460    f  W95 Ext'd (LBA)
/dev/sda5            3825       19122   122881153+  83  Linux
/dev/sda6           19123       23979    39013821   83  Linux
/dev/sda7           23980       24792     6530391   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77a6c312

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          66      530113+  82  Linux swap / Solaris
/dev/sdb2             131       30286   242228070   83  Linux
/dev/sdb4              67         130      514080   83  Linux

Partition table entries are not in disk order


I think you have nudged me - I am using drives that I have recovered from an earlier ubuntu build, and I simply forgot to re-partition them!

That's pretty dumb of me - I apologise for troubling you. In the very least, though, I have learnt another useful command.

When I get back I will check this forum to see your comments, then repartition and reformat both drives.

D'oh!

Dick

---

### Post by Bachstelze on 2009-01-12
> **Crabro said:**
> 
I think you have nudged me - I am using drives that I have recovered from an earlier ubuntu build, and I simply forgot to re-partition them!

Indeed, the partition layout of your second drive is that of a typical Ubuntu install (root, home and swap partitions). I guess that settles it then. ;)

---

### Post by Crabro on 2009-01-12
I have managed to work out what was going on, and thought I would feed it back.

After some experimenting, I discovered that the D-Link DNS-323 created three partitions on the drive during its initial drive format. You can see these on my earlier post. I discovered this after using gparted to repartition my drive, then reformat it with the DNS-323. When I re-attached the drive to my PC I found identical partitions to the original ones posted.

I decided to see if I could mount the drive - new territory to me. I read up the mount command, created a mount point in my .media directory so I could see what was going on and mounted the large partition:

```
sudo mount -t ext2 /dev/sdb2 /media/tmpmnt
```

At last, I was then able to see my files.

I am a happy bunny now that I know that I can recover my files in case of an enclosure failure. I can now commit to this unit as my file server.

Many thanks for your help - I have learned quite a bit today!

Dick

---

