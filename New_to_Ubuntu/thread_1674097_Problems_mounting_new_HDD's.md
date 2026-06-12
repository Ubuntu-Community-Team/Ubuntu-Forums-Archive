---
title: "Problems mounting new HDD's"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by bazzieb on 2011-01-23
Hi There

I am trying to mount 2x 500gig SATA HDD's. I followed these intructions [https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot](https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot)

When i reboot my PC i get the following error: Serious errors were found while checking the disk drive for /media/mountfolders 

My fstab entry looks like this:
# drive for music 
/dev/sdb	/media/music_drive	ext3	defaults	0      2	
# drive for multimedia data
/dev/sdc	/media/data_drive	ext3	defaults	0	2

when i sudo lshw -C disk, i get the following for these 2 disks:

*-disk:0
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: SD15
       serial: 9QM2XHH8
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000078e3
  *-disk:1
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: SD15
       serial: 9QM2XQ7E
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0001133f

I have changed the permissions on the folders in /media/mountfolders.

All assistance will be appreciated
Regards
BazzieB

---

### Post by pbpersson on 2011-01-23
Please take a look at or if you are not sure, show us the output of the following command in a terminal session:

```
sudo fdisk -l
```

Looking at the instructions and seeing what you put into your fstab file, there is a huge difference which you have overlooked.  In the example, they have designations such as:

sda5
sdb1


You do not have the digit at the end so you are not specifying a partition to mount, you are specifying the entire drive which of course will not work - therein lies the problem.

---

### Post by MooPi on 2011-01-23
Similarly I prefer to use the UUID of a partition instead of the drives designation. To get the UUID run this command from terminal ```
sudo blkid
```Then you can plug that info into your fstab file like so....```
UUID=764bed9f-aef9-4e4b-b432-7ff91c297883 /media/data_drive ext3 defaults 0 0
``` I prefer to use mnt instead of media so mine looks like this ```
UUID=764bed9f-aef9-4e4b-b432-7ff91c297883 /mnt/Data1 ext4 defaults 0 0
```

---

### Post by bazzieb on 2011-01-24
> **pbpersson said:**
> Please take a look at or if you are not sure, show us the output of the following command in a terminal session:

```
sudo fdisk -l
```

Looking at the instructions and seeing what you put into your fstab file, there is a huge difference which you have overlooked.  In the example, they have designations such as:

sda5
sdb1


You do not have the digit at the end so you are not specifying a partition to mount, you are specifying the entire drive which of course will not work - therein lies the problem.

Here is the printout of sudo fdisk -l:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000078e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    6  FAT16

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001133f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       60801   488376000    7  HPFS/NTFS

Thanks for help so far:)

---

### Post by oldfred on 2011-01-24
The ext3 entry refers to the linux format of ext3. You have one drive formated as FAT and the other as NTFS. So you have to use vfat and ntfs mounting.

You do know that FAT has a max file size of 4GB and any files over that size copied to the drive will probably just be damaged without warning.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

This was my entry for a NTFS partition with my UUID:
# Entry for /dev/sda1 :"
UUID=04B05B70B05B6768          /mnt/cdrive  ntfs-3g      defaults           0  0

---

### Post by bazzieb on 2011-01-30
Would it help if i formatted these HDD's to ext3/4?

---

### Post by oldfred on 2011-01-31
If you are only going to use the partitions with Linux then ext3/ext4 would be better, as then you have ownership and permissions that you control.

With FAT & NTFS you set ownership & permission defaults at boot with fstab as that is the only way Linux can use the NTFS partition. But FAT is not now intended for large partitions. It has no journal (so repairs are more difficult) and cannot store files over 4GB.

---

