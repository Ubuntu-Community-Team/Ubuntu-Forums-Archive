---
title: "Pen drive failure"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-01
Hi,

I've followed a procedure to install Ibex on a pen drive but some probs occured it seems,(see below) and at boot up it stalls at: SYSLINUX... boot:


nnjond@nnjond-desktop:~$ wget pendrivelinux.com/downloads/u810/u810.sh
--2009-04-01 12:04:10--  [http://pendrivelinux.com/downloads/u810/u810.sh](http://pendrivelinux.com/downloads/u810/u810.sh)
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3074 (3.0K) [application/x-sh]
Saving to: `u810.sh.2'

100%[======================================>] 3,074       16.2K/s   in 0.2s    

2009-04-01 12:04:11 (16.2 KB/s) - `u810.sh.2' saved [3074/3074]

nnjond@nnjond-desktop:~$ chmod +x u810.sh && sh u810.sh
############# USB INSTALLER SCRIPT #############

This script can be used to create a Ubuntu 8.10
Persistent USB flashdrive from a 2GB+ USB drive.

================================================
================= WARNING! =====================
================================================

This USB installer script is being offered AS-IS
for FREE and comes with absolutely no warranty.
Proceed at your own risk.

If you agree, press Enter to continue...


================================================

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104483+  82  Linux swap / Solaris
/dev/sda2   *         263        2873    20972857+  83  Linux
/dev/sda3            2874        3199     2618595   83  Linux
/dev/sda4            3200       11709    68356575   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6248591f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

Disk /dev/sdc: 2023 MB, 2023751680 bytes
63 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x000f1a62

   Device Boot      Start         End      Blocks   Id  System

=========== Locate your flash drive ============

Please locate your flash drive from the list of
devices displayed above and enter it's letter.

For example, if your flash drive is /dev/sdx,
you would type x and then press Enter

What is your drive letter?:
c

=========== Creating the partitions ===========

dev/sdc1 is ready
dev/sdc2 is ready
Error: Partition doesn't exist.
Error: Partition doesn't exist.


















============ Creating filesystem ============

mkfs.vfat 2.11 (12 Mar 2005)
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=casper-rw
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61824 inodes, 246999 blocks
12349 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=255852544
8 block groups
32768 blocks per group, 32768 fragments per group
7728 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

============ Stage 1 completed ==============

Please remove and reinsert your flash drive.
Wait for the mounted partitions to appear on
your desktop, and then press Enter to continue






===== Stage 2: creating the portable USB ====

Moving on to create the portable system.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
syslinux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

Now copying files to your flash drive.
Please wait...

cp: cannot stat `casper': No such file or directory
cp: cannot stat `dists': No such file or directory
cp: cannot stat `install': No such file or directory
cp: cannot stat `pics': No such file or directory
cp: cannot stat `pool': No such file or directory
cp: cannot stat `preseed': No such file or directory
cp: cannot stat `.disk': No such file or directory
cp: cannot stat `isolinux/*': No such file or directory
cp: cannot stat `md5sum.txt': No such file or directory
cp: cannot stat `README.diskdefines': No such file or directory
cp: cannot stat `install/mt86plus': No such file or directory
cp: cannot stat `isolinux.cfg': No such file or directory
rm: cannot remove `text.cfg': No such file or directory
--2009-04-01 12:07:27--  [http://pendrivelinux.com/downloads/u810/text.cfg](http://pendrivelinux.com/downloads/u810/text.cfg)
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 864 [text/plain]
Saving to: `text.cfg'

100%[======================================>] 864         --.-K/s   in 0s      

2009-04-01 12:07:28 (61.3 MB/s) - `text.cfg' saved [864/864]


=========== Stage 2 completed =============

All finished, your flash drive is now ready
Press Enter to close this window...

nnjond@nnjond-desktop:~$

---

### Post by cariboo on 2009-04-02
It looks like you don't have the Ubuntu iso on your system. follow the tutorial [here]("http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401"), I've tried it and it works well.

Jim

---

