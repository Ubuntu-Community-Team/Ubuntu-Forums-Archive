---
title: "Linux partition not showing up on ubuntu livecd"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by PC1910 on 2010-10-07
I hope this isn't a redundant post but after searching for hours I could not find any solutions to my problem. 
I had windows 7 and ubuntu running on the same drive and everything was working fine until I reinstalled windows. I know that the reinstall overwrote grub but none of the guides for fixing or reinstalling worked. When I use a livecd only my windows7 shows up in the computer folder - ubuntu is missing. The only place I can install grub is on this live cd. I am new to linux but these are some of the commands that I ran to try to figure out the problem but I'm lost. I'd like to at least be able to recover the data on the ubuntu...any help is appreciated.

[HTML]sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28812881

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9791    78646176    7  HPFS/NTFS
/dev/sda2           29027       38245    74050561    5  Extended
/dev/sda3           38245       60801   181181440    7  HPFS/NTFS
/dev/sda5           37942       38245     2440192   82  Linux swap / Solaris
ubuntu@ubuntu:~$ [/HTML]Then I ran boot_info_script055.sh and got:
[HTML]
                                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   157,292,414   157,292,352   7 HPFS/NTFS
/dev/sda2         466,302,974   614,404,095   148,101,122   5 Extended
/dev/sda5         609,523,712   614,404,095     4,880,384  82 Linux swap / Solaris
/dev/sda3         614,404,096   976,766,975   362,362,880   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 520 MB, 520880128 bytes
255 heads, 63 sectors/track, 63 cylinders, total 1017344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,017,343     1,017,281   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C0A876F9A876ED72                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        864E75064E74EFF3                       ntfs                                     
/dev/sda5        168728bb-f7ab-4075-8f78-afa76e87bb5b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        55c22d55-691a-462d-89a1-9974ecc6e5bf   ext4       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/864E75064E74EFF3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /mnt                     ext4       (rw)[/HTML]

---

### Post by Rubi1200 on 2010-10-07
According to the results you no longer have an Ubuntu partition only a swap partition.

Where was Ubuntu originally installed? On sda1?

You could try using Testdisk to see if it can find and recover the Ubuntu partition:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Be careful, though, because you do not want to wipe out the Windows installation (I suspect you may have written over the Ubuntu install if you had originally done a side-by-side install).

---

### Post by PapaNerd on 2010-10-07
It appears that the Windoze re-installation clobbered your Linux partition (disk blocks 9792 through 29026).  You would have to create the partition in order to mount it and recover data, but re-writing the partition table (using fdisk) would delete the file index and not allow you access to your files.  Hopefully, someone else knows of a recovery application that might help.

---

### Post by PC1910 on 2010-10-07
Thanks for the advice. Running testdisk right now and doing deeper search which seems it will take forever. I am not sure if I installed ubuntu on sda1. I'm sure I did not delete it...I reinstalled windows on the same partition it was on before. Thanks for your help.

---

