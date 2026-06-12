---
title: "Need help accessing my ntfs raid"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by maxmouse24 on 2010-04-27
I have windows XP Home and Ubuntu 9.10 installed on my computer. I have a 500GB raid that I can access in XP I want to access my movies from Ubuntu as well can you help me please? Thank you in advance

Here is my fdisk info if that helps

# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb854d39b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        6006    41945715    7  HPFS/NTFS
/dev/sda3            6007       19457   108045157+   f  W95 Ext'd (LBA)
/dev/sda5            6007        7222     9767488+  83  Linux
/dev/sda6            7223       19457    98277606   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x048fac46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       61031   490231476    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
#

---

### Post by nhasian on 2010-04-27
according to the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004") for the new Ubuntu 10.04 Lucid Lynx, fake-raid is detected and supported out of the box.

---

### Post by warfacegod on 2010-04-27
> **nhasian said:**
> according to the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004") for the new Ubuntu 10.04 Lucid Lynx, fake-raid is detected and supported out of the box.

In other words, wait two days, do an upgrade or fresh install, and it will work.

---

