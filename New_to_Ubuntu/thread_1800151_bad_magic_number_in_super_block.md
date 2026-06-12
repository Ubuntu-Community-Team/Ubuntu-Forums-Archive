---
title: "bad magic number in super block"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by nicos99 on 2011-07-08
Hi Guys,
 
I'm quite new in Linux, I really need your help for the problem I got here.
 
I have a Linux server with 2 old disks about 32G each, since the capacity is not enough, we bough a new disk. 
The first thing we did is use dd to dump one of the disk out, it's everything ok until there. Now we took one old disk out and input the new one. 
We used Gparted to format the disk with ext3 and mount it using sudo mount /dev/sdb1 /mnt
but I found eveytime, reboot the system in live CD, it seems unmounted automatically.
The second thing, of course, I use dd again to input the dump file to the new disk, but I always get bad magic number in super block. I think there is something wrong I forgot or there is error already in the beginning. Here is result for the bootinfo, please help.
 
```
 
 
Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Lilo is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdd.
sda1: __________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf /map
sda2: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3: __________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Red Hat Enterprise Linux ES 
                       release 3 (Taroon Update 4) Kernel on an
    Boot files:        /etc/fstab /etc/lilo.conf
sdb1: __________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        
sdc1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sdd1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *              1       208,844       208,844  83 Linux
/dev/sda2             192,780     4,498,199     4,305,420  82 Linux swap / Solaris
/dev/sda3           4,498,200    71,087,624    66,589,425  83 Linux
/dev/sda1 overlaps with /dev/sda2
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 146.8 GB, 146815733760 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1                  63   286,744,184   286,744,122  83 Linux
 
Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS
 
Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 1021 MB, 1021313024 bytes
15 heads, 46 sectors/track, 2890 cylinders, total 1994752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdd1                 240     1,994,751     1,994,512   6 FAT16
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        3e75b32d-4307-498e-b2f1-c52f5744bec1   ext3       /boot
/dev/sda2                                               swap       
/dev/sda3        d6b77d59-b5ad-4e02-9279-ae36e5fa7e47   ext3       /
/dev/sdb1        8a8742e6-8409-4544-a128-6c6fca2c6794   ext3       
/dev/sdc1        104C9D4C4C9D2E0A                       ntfs       LaCie
/dev/sdd1        5AA0-D65C                              vfat       
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     ext3       (rw)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,uid=999,umask=0077,shortname=winnt,utf8)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
============================= sda1/grub/grub.conf: =============================
--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda3
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,0)/grub/splash.xpm.gz
title Red Hat Enterprise Linux ES (2.4.21-27.0.2.EL)
 root (hd0,0)
 kernel /vmlinuz-2.4.21-27.0.2.EL ro root=LABEL=/
 initrd /initrd-2.4.21-27.0.2.EL.img
title Red Hat Enterprise Linux ES (2.4.21-27.0.2.ELsmp)
 root (hd0,0)
 kernel /vmlinuz-2.4.21-27.0.2.ELsmp ro root=LABEL=/
 initrd /initrd-2.4.21-27.0.2.ELsmp.img
--------------------------------------------------------------------------------
=================== sda1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
   0.045413494 = 0.048762368    grub/grub.conf                                 1
   0.045413494 = 0.048762368    grub/menu.lst                                  1
   0.012554646 = 0.013480448    initrd-2.4.21-27.0.2.EL.img                    3
   0.006787777 = 0.007288320    initrd-2.4.21-27.0.2.ELsmp.img                 3
   0.017273426 = 0.018547200    vmlinuz-2.4.21-27.0.2.EL                       7
   0.012217045 = 0.013117952    vmlinuz-2.4.21-27.0.2.ELsmp                    7
=============================== sda3/etc/fstab: ================================
--------------------------------------------------------------------------------
LABEL=/                 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
none                    /dev/pts                devpts  gid=5,mode=620  0 0
none                    /proc                   proc    defaults        0 0
none                    /dev/shm                tmpfs   defaults        0 0
/dev/sda2               swap                    swap    defaults        0 0
/dev/sdb                /mnt/sdb                ext3    defaults        1 2
/dev/cdrom              /mnt/cdrom              udf,iso9660 noauto,owner,kudzu,ro 0 0
--------------------------------------------------------------------------------
============================= sda3/etc/lilo.conf: ==============================
--------------------------------------------------------------------------------
prompt
timeout=50
default=2.4.21-27.0.2.E
boot=/dev/sda
map=/boot/map
install=/boot/boot.b
linear
image=/boot/vmlinuz-2.4.21-27.0.2.EL
 label=2.4.21-27.0.2.1
 initrd=/boot/initrd-2.4.21-27.0.2.EL.img
 read-only
 append="root=LABEL=/"
image=/boot/vmlinuz-2.4.21-27.0.2.ELsmp
 label=2.4.21-27.0.2.E
 initrd=/boot/initrd-2.4.21-27.0.2.ELsmp.img
 read-only
 append="root=LABEL=/"
--------------------------------------------------------------------------------
 
 
 

```

---

### Post by oldfred on 2011-07-08
I do not think it is the bad magic number but overlapping partitions.

/dev/sda1 overlaps with /dev/sda2

If you look carefully you can see your swap starts before the sda1 ends. I would write a backup and delete swap. Then you could recreate swap that is vaild.

Just in case the swap deletion screws up sda1, you can then easily recover partition table.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

You do have to be very careful with dd. It is very powerful but also has the nickname Data Destroyer.:)

---

### Post by nicos99 on 2011-07-11
Thank you oldfred,
I think you are right, but when I do sudo sfdisk -d -f /dev/sda2 >PY.txt, I got following error msg:
sfdisk: Error: Sector 0 does not have an Msdos signature 
dev/sda2: unrecognized partition table type
No Partitions found
 
need help

---

### Post by oldfred on 2011-07-12
do not include the partition number in the command. You are backing up the full partition table from sda.

sudo sfdisk -d /dev/sda > PT.txt

You posted sda2 in the command you ran.

---

### Post by nicos99 on 2011-07-12
Hi oldfred,
when I do: sudo sfdisk -d /dev/sda > PT.txt
it seems nothing happened, don't know why.

---

### Post by oldfred on 2011-07-12
You will find a file called PT.txt in your standard /home/$USER folder. Save that file somewhere else.

Then see if you can delete swap.

---

