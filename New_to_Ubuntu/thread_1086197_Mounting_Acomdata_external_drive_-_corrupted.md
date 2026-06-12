---
title: "Mounting Acomdata external drive - corrupted?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by neanderthalman on 2009-03-03
My boss has been having some trouble with an external hard drive, and I offered to take a look.  It's a 60gb acomdata usb drive.  When mounted under windows, it gives an error that the drive may be corrupted, at which point it vanishes.  Several years ago, I encountered a similar error on an internal drive, and was able to mount the drive using a knoppix livecd.

Knowing windows will barf up a drive at the first sign of trouble, I'd like to attempt something similar - mount the drive on my unbuntu install, pull the data, repartition and reformat.

However, I cannot get the drive to mount - not unexpected, given the questionable behaviour under windows.  If anyone with more experience could point out any blatant errors, or offer suggestions of alternative solutions, it would be most appreciated.  I'd like to leave reformat & data recovery software as a last resort due to the inherent risks involved.

The following details the hardware and mount error(s) I'm seeing.

```
neanderthalman@Pinky-Ubuntu:~$ sudo fdisk -l
[sudo] password for neanderthalman: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        3824    15358140   83  Linux
/dev/sda4            3825       14594    86502986    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6            3825        4322     4000122   82  Linux swap / Solaris
/dev/sda7            4323       14266    79875148+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60009545728 bytes
239 heads, 63 sectors/track, 7784 cylinders
Units = cylinders of 15057 * 512 = 7709184 bytes
Disk identifier: 0xe8f2c597

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7784    58595008    7  HPFS/NTFS

neanderthalman@Pinky-Ubuntu:~$ blkid
/dev/sda1: UUID="423C42803C426F4B" TYPE="ntfs" 
/dev/sda2: UUID="ead73abd-0e3b-41c8-9cab-3e683e08f502" TYPE="ext3" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="A4E6-092B" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="a1acbab6-c458-46a6-9174-d4e5ceb351ec" 
/dev/sda7: UUID="161834F71834D807" TYPE="ntfs" 
/dev/mmcblk0p1: LABEL="KODAK" UUID="FC30-3DA9" TYPE="vfat" 
neanderthalman@Pinky-Ubuntu:~$ lsusb
Bus 006 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 002: ID 0c0b:2bcf Dura Micro, Inc. (Acomdata) 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

neanderthalman@Pinky-Ubuntu:~$ sudo mount /dev/sdb1 /media/external
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

neanderthalman@Pinky-Ubuntu:~$ ls -la /media
total 28
drwxr-xr-x  6 root           root  4096 2009-03-03 19:18 .
drwxr-xr-x 22 root           root  4096 2009-02-13 18:50 ..
drwxrwxr-x  1 neanderthalman users 8192 2009-02-19 00:00 C
lrwxrwxrwx  1 root           root     6 2009-02-10 19:31 cdrom -> cdrom0
drwxr-xr-x  2 root           root  4096 2009-02-10 19:31 cdrom0
drwxrwxr-x  1 neanderthalman users 4096 2009-03-01 11:17 D
drwxr-xr-x  2 root           root  4096 2009-03-03 19:00 external
-rw-r--r--  1 root           root     0 2009-03-03 19:15 .hal-mtab
-rw-------  1 root           root     0 2009-03-03 19:15 .hal-mtab-lock
neanderthalman@Pinky-Ubuntu:~$ 

neanderthalman@Pinky-Ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /media/external -o force
[sudo] password for neanderthalman: 
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
neanderthalman@Pinky-Ubuntu:~$ 

```



Any ideas?

---

