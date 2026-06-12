---
title: "How to access external storage?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by svjensen on 2011-01-23
Granted, I am completely new to Ubuntu :)

I have a akasa elite 3,5 inch external USB drive, that I am trying to access. According to their website supported OS are Windows 2000/XP/Vista/7 and Mac Os 9 and OS X.

I have tried running a couple of commands in a terminal window (since it was suggested in a thread with a similar problem). The results are:

command: ubuntu@ubuntu:~$ sudo fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3c6e3a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       30402   228796600    7  HPFS/NTFS

Disk /dev/sdb: 4110 MB, 4110417920 bytes
16 heads, 32 sectors/track, 15680 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47d65a7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15680     4014064    c  W95 FAT32 (LBA)

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0630c8e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          66      530113+  83  Linux
/dev/sdc2              67         132      530145   82  Linux swap / Solaris
/dev/sdc3             133      243138  1951945695   83  Linux
/dev/sdc4          243139      243200      498015   83  Linux

```Command: ubuntu@ubuntu:~$ sudo blkid
```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="F6ECCCDCECCC97EF" TYPE="ntfs" 
/dev/sda3: UUID="C806FAFF06FAED76" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="F8B1-DDD6" TYPE="vfat" 
/dev/sdc1: UUID="704fadb0-e0c9-1b7c-d92e-d0de214a2df8" TYPE="linux_raid_member" 
/dev/sdc2: UUID="f25f91d9-acec-3401-f768-434176eae194" TYPE="linux_raid_member" 
/dev/sdc3: UUID="09165bd2-15bc-2f05-1004-04667480d454" TYPE="linux_raid_member" 
/dev/sdc4: UUID="277e86a2-3d86-0914-a50c-1b506ad8991f" TYPE="linux_raid_member" 

```Command: ubuntu@ubuntu:~$ lsusb
```

Bus 008 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 13fd:1340 Initio Corporation Hi-Speed USB to SATA Bridge
Bus 002 Device 003: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```As far as I can read the results above, the system can see the device (sdc 1 through 4 if I am correct), but how can I access it?

/Soren

---

### Post by fabricator4 on 2011-01-23
Are you running a Wubi install?  I can't see a linux boot partition on sda.  If the device doesn't automount when you plug it in you can mount it manually.  In this example I'll mount the third partition (the largest one) to a directory in your home directory.  In a terminal:

```

mkdir ~/Aname
sudo mount /dev/sdc3 ~/Aname

```

You'll have to give your password when prompted, as superuser rights are required for mounting.  If you now go to your home folder you'll see a directory called Aname, and inside this directory will be the contents of sdc3

Note that file and directory names in Linux are case sensitive.

Chris.

---

