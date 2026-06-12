---
title: "GParted is showing entire hard drive is unallocated"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jestang93 on 2009-11-12
fdisk shows:

omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10570    84855330    7  HPFS/NTFS
/dev/sda3           10571       13768    25687935    5  Extended
/dev/sda4           11219       11473     2048256   82  Linux swap / Solaris
/dev/sda5           10571       11183     4923859+  83  Linux
/dev/sda6           11184       11218      281106   82  Linux swap / Solaris
/dev/sda7           11474       13768    18434556   83  Linux




I originally had 8.10 installed and I attempted to upgrade to 9.04 through update manager but something went wrong. I ended up installing 9.04 with the Live CD. What I'm trying to do now is delete 8.10. 

Thanks!

---

### Post by louieb on 2009-11-12
Know the reason - non-standard partition table - primary partition sda4 inside extended partition sda3. Gparted see that and show the disk as blank. 

Note that sda5, sda6, and sda7 are also inside sda3 - thats as it should be - they are logical partitions.  

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10570    84855330    7  HPFS/NTFS
[COLOR=Red]/dev/sda3           10571       13768    25687935    5  Extended[/COLOR]
[COLOR=Red]/dev/sda4           11219       11473     2048256   82  Linux swap / Solaris[/COLOR]
/dev/sda5           10571       11183     4923859+  83  Linux
/dev/sda6           11184       11218      281106   82  Linux swap / Solaris
/dev/sda7           11474       13768    18434556   83  Linux

```Have not used it but fdisk, sfdisk or maybe testdisk could delete sda4. 
[sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

