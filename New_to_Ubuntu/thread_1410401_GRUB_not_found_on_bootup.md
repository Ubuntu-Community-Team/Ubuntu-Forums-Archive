---
title: "GRUB not found on bootup"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by vlad1975 on 2010-02-18
Hello,

I had some problems earlier with ubuntu so i decided to reinstall it. installation went well but now when it reboots, GRUB  then No file found then GRUB REPAIR. when i do a LS it give a list of the HD0

HELP PLEASE

---

### Post by vlad1975 on 2010-02-18
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=77c510bd-a88f-496c-9bfc-2fcd71019e2c)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c879c87

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,829,674   224,827,627   7 HPFS/NTFS
/dev/sda2         224,829,675   234,436,544     9,606,870   f W95 Ext d (LBA)
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xee836e47

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x454c0ef7

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1A9875BD987597C9                       ntfs                                     
/dev/sda5        02f1b85a-e77c-4d5b-9819-72acfffd6777   swap                                     
/dev/sdb1        f0a89614-3434-47ba-8701-efae48ff3a20   ext4                                     
/dev/sdb5        b69ba4d8-1574-401d-a7b5-599abba7a1a6   swap                                     
/dev/sdd1        725045305044FC7B                       ntfs       LaCie                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/f0a89614-3434-47ba-8701-efae48ff3a20 ext4       (rw,nosuid,nodev,uhelper=devkit)


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f0a89614-3434-47ba-8701-efae48ff3a20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b69ba4d8-1574-401d-a7b5-599abba7a1a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by vlad1975 on 2010-02-18
Any idea what this mean? and how to fix it?

---

### Post by RJARRRPCGP on 2010-02-18
This may be a bad HDD. I seen an OS appear to start installing fine, but an OS error occurs on reboot, with a bad Western Digital Caviar WD5000AAJS. 

If the HDD isn't bad, it usually means you changed an installer option for GRUB when the default shall have been used.

---

### Post by Miljet on 2010-02-18
It will be pretty much impossible for anyone to help you with no more information than you have given. What version? How installed, Wubi or dual boot? How many disks? How is it/they partitioned? Exact error messages?

Best advice at this point is check your installation disk to be sure it is good and reinstall again. Pay particular attention during installation to where Grub is being installed.

Sorry, looks like you did post additional information while I was typing.

---

### Post by oldfred on 2010-02-18
Your grub install in sda is pointing to a UUID that now does not exist. But you also seem to be missing essential files in /boot and /boot/grub. Please check if your boot and grub folders have files like this from my older boot script (not all shown so my be inconsistent versions):

316.7GB: boot/grub/grub.cfg
 316.7GB: boot/initrd.img-2.6.31-14-generic
 316.7GB: boot/vmlinuz-2.6.31-14-generic
 316.7GB: initrd.img
 316.7GB: vmlinuz

At the very least you need to reinstall grub and maybe your system files. I would install grub to the same drive as the Ubuntu install sdb as it boots slightly faster and set that drive to first in BIOS.

---

### Post by Miljet on 2010-02-18
Also your Windows boot loader is installed in the MBR of your Ubuntu disk (sdb) and Grub is installed in the MBR of your Vista drive (sda).

Since I am still running legacy Grub and am not that familiar with Grub2, I will bow out and leave it to those more knowledgeable than I.

---

