---
title: "error during 9.10 install. please help."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Velenjak on 2011-06-07
Ok so I run windows 7 as my primary, and i was re-installing ubuntu on a different partition. There was an error during installation and now my computer wont log into windows. I guess I deleted my windows loader on accident?

here is the script... please help
                

  Boot Info Script 0.60    from 17 May 2011



============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for (,msdos4)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /etc/fstab

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 4939636 of /dev/sdb for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb275b50

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   176,842,751   176,635,904   7 NTFS / exFAT / HPFS
/dev/sda3         176,843,520   312,496,379   135,652,860   5 Extended
/dev/sda5         299,724,768   312,496,379    12,771,612  82 Linux swap / Solaris
/dev/sda6         176,843,646   299,724,704   122,881,059  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6480F1BF80F1982E                       ntfs       System Reserved
/dev/sda2        14EAF6BEEAF69B66                       ntfs       
/dev/sda5        c058745c-98c5-4f84-8ce6-bc5dc6155154   swap       
/dev/sda6        29164295-8a3f-4a5e-b2de-f7df975c0f9a   ext4       
/dev/sdb         FE51-60A1                              vfat       4.0 GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=29164295-8a3f-4a5e-b2de-f7df975c0f9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c058745c-98c5-4f84-8ce6-bc5dc6155154 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.c32                                       1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v3.xx)

---

### Post by Bucky Ball on 2011-06-07
Slightly off topic but 9.10 is no longer supported. Try 10.04 LTS for long-term support or 10.10.

Looks like your Windows boot loader is still there and you have Grub also. You'd be better perhaps to describe the error that occurred during installation. ;)

What happens exactly when you boot the machine?

---

### Post by Velenjak on 2011-06-07
> **Bucky Ball said:**
> Slightly off topic but 9.10 is no longer supported. Try 10.04 LTS for long-term support or 10.10.

Looks like your Windows boot loader is still there and you have Grub also. You'd be better perhaps to describe the error that occurred during installation. ;)

What happens exactly when you boot the machine?

Oh good to know, I'll burn a 10.04 version.

I don't quite remember the exact error but it said that there was either an error with the CD or the harddisk... the CD is decently scratched up so i hope that was the issue.

the error i get at boot is:

error: no such partition.
grub rescue>


when i boot from the windows 7 cd I also get the same error message. [I am able to boot from ubuntu live disk however]

---

### Post by Velenjak on 2011-06-07
Do you think I would be OK if I were to boot from 10.04 and re-install?

---

### Post by Bucky Ball on 2011-06-07
> **Velenjak said:**
> Do you think I would be OK if I were to boot from 10.04 and re-install?

Good idea.  Is Win7 already installed? If not, install Win7 first and leave free space for the Ubuntu 10.04 LTS install if you are looking to dual-boot.

---

