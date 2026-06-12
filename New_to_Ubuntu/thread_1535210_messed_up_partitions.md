---
title: "messed up partitions"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by erjoalgo on 2010-07-20
I messed up partition information after using the Windows XP cd to overwrite MBR and other things. 
When I boot to ubuntu from grub, I get error, disk does not exist, I've installed grub before without this error.
From the live cd, when I do
```

ubuntu@ubuntu:~$ sudo mount /dev//sda1 /mnt/
mount: you must specify the filesystem type

```So mount doesnt know that /dev/sda1 is ext3.
I figured I can mount it by specifying type as an argument:
```

sudo mount -t ext3 /dev//sda1 /mnt/

```But I think this is the problem with grub, the partition tables? were corrupted by windows.

This is the output of some commands:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15556   124953538+  83  Linux
/dev/sda2           15557       15751     1566337+  82  Linux swap / Solaris
/dev/sda4           15752       19452    29728282+   7  HPFS/NTFS

```/dev/sda1 is where ubuntu is installed
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15556   124953538+  83  Linux
/dev/sda2           15557       15751     1566337+  82  Linux swap / Solaris
/dev/sda4           15752       19452    29728282+   7  HPFS/NTFS


```Clearly there is something wrong, how can I fix this?

---

### Post by drs305 on 2010-07-20
Normally you should be able to just run the command as "sudo mount /dev/sda1 /mnt" and it should work, so there could be deeper problems. 

However, for now just post the results of this boot info script by *meierfra* so we can see the status of Grub and  your system:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Please paste the contents within "code" tags, which you generate by pressing the # icon in the post's top menu.

---

### Post by erjoalgo on 2010-07-20
Thanks for prompt reply. I decided to trust this code, here is the output```
ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   249,907,139   249,907,077  83 Linux
/dev/sda2         249,907,140   253,039,814     3,132,675  82 Linux swap / Solaris
/dev/sda4         253,039,815   312,496,379    59,456,565   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2        f0b977a4-446f-4f01-acb4-d7f2968c81a8   swap                                     
/dev/sda4        1ACCFF59CCFF2D9F                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/1ACCFF59CCFF2D9F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda4/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by erjoalgo on 2010-07-20
It seems that mount doesnt know where my ext3 partition starts, where it ends, or what filesystem type it is. How can I repair the partition tables?

---

### Post by drs305 on 2010-07-20
As you can see from the RESULTS.txt info, the system is having problems reading what's on sda1. 

Testdisk is an app that may be able to sort it out for you. The app's web site has a fairly good example page although using it can still be a bit overwhelming.  Here is the link:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

Herman's site may also help:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

If you get stuck someone in here familiar with partition problems can probably help you with your specific situation.

---

