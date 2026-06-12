---
title: "Operating System not found"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by demalition on 2010-12-10
hi please help
 i have a samsung n210 which had windows7. i decided to be free and tried to get debian which failed and i went to install ubuntu 10.10 using a 2GB pen. the installation went ok but when i rebooted i got the error OS not found. i ran a fdisk -l and here is the result:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a24b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
62 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cfc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017     1954643    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by amjjawad on 2010-12-10
> **demalition said:**
> hi please help
 i have a samsung n210 which had windows7. i decided to be free and tried to get debian which failed and i went to install ubuntu 10.10 using a 2GB pen. the installation went ok but when i rebooted i got the error OS not found. i ran a fdisk -l and here is the result:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a24b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
62 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cfc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017     1954643    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

Hello and welcome :)

I see you're having two HDDs. One (sda) for Ubuntu and the other (sdb) for Windows. 
1) I'd suggest to check your BIOS settings and make sure sda is the first HDD to boot not sdb.

2) Are you able to boot into Windows? or you can't boot anything at all?

---

### Post by Rubi1200 on 2010-12-10
Agree with amjjawad about checking the settings in BIOS.

Also, from a LiveCD, post the results of the boot info script linked at the bottom of my post.

Thanks.

---

