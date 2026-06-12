---
title: "correct way to set up backup hard drive ???"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-11-30
OK I just installed a 2nd hard drive to use as a data backup device.

I think I need to go to fstab or somewhere to add the device for mounting.

The computer "sees" the new drive on bootup as SCSI drive but can't mount it right now.

Should I set the drive up as one partition or more? Can i configure this drive to be bootable in the event my main drive becomes defective on bootup? 

Any other useful ideas would be appreciated at this point.

Ed

P.S.   My current Fstab & Fdisk -l

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9360d76a-ddb7-4a4a-8a92-21d35c903ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d31d0c7-73ab-4b92-a354-c34d2bb6bf5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

# Floppy Drive
/dev/fd0        /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0


ed@House:~$ sudo fdisk -l
[sudo] password for ed: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00460046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       25583   154296292+   5  Extended
/dev/sda5            6375       24610   146480638+  83  Linux
/dev/sda6           24611       25583     7815591   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36de36de

---

### Post by cariboo on 2009-12-03
You need to partition /dev/sdc. Install gparted, using either Add/Remove if your using 9.04 or older, the Software Center for 9.10+ or Sysnaptic Package Manager.

---

