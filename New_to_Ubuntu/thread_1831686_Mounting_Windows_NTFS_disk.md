---
title: "Mounting Windows NTFS disk"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by davesyd on 2011-08-23
Hi Everyone,

I have given Ubuntu another shot moving away from Windows 7.  I just installed Ubuntu on the SDA1 partition of my hard drive where Windows 7 used to be installed.  On the SDA3 partition I had windows files stored separately (in Windows it was my D: drive).  

On Ubuntu I ran "sudo fdisk -l" and came up with the below:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600   83  Linux
/dev/sda2           13055       15013    15728640   1b  Hidden W95 FAT32
/dev/sda3           15013       38911   191963136    7  HPFS/NTFS
/dev/sda4           38911       38914       20824   ef  EFI (FAT-12/16/32)

I googled my problem and found that i should try to run the below command:

sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /media/Downloads

After hitting enter I receive this error message:

NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---------------

Any advice would be appreciated... I don't want to format the SDA3 partition as I have alot of documents on it.

Thanks,
Dave

---

### Post by oldfred on 2011-08-23
Ubuntu cannot run chkdsk nor do fixboot, both which may be required. Since you kept NTFS, did you keep a windows repairCD so you could maintain your NTFS partition?

Testdisk can see if the backup partition boot sector is valid.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by madjr on 2011-08-23
> **davesyd said:**
> Hi Everyone,

I have given Ubuntu another shot moving away from Windows 7.  I just installed Ubuntu on the SDA1 partition of my hard drive where Windows 7 used to be installed.  On the SDA3 partition I had windows files stored separately (in Windows it was my D: drive).  

On Ubuntu I ran "sudo fdisk -l" and came up with the below:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600   83  Linux
/dev/sda2           13055       15013    15728640   1b  Hidden W95 FAT32
/dev/sda3           15013       38911   191963136    7  HPFS/NTFS
/dev/sda4           38911       38914       20824   ef  EFI (FAT-12/16/32)

I googled my problem and found that i should try to run the below command:

sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /media/Downloads

After hitting enter I receive this error message:

NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---------------

Any advice would be appreciated... I don't want to format the SDA3 partition as I have alot of documents on it.

Thanks,
Dave

have you tried mounting them with nautilus?

---

