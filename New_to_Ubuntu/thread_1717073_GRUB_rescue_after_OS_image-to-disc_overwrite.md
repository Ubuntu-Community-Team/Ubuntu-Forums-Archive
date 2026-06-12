---
title: "GRUB rescue after OS image-to-disc overwrite"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Erandros on 2011-03-29
I have two drives. One (sda) has Windows 7 and Documents, the other one (sdb) had Ubuntu Lucid running normal also with Documents. I had made a clonezilla image of sdb, and stored it in sda. I wanted to try Debian out, so I did a fresh install on sdb, but after I tried it, I wanted to roll back to Ubuntu. So I restored the Ubuntu image on sdb, but then I got the famous GRUB rescue prompt. I tried doing this:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```This starts Win7 with no alternatives.

Though my Ubuntu is Lucid, I can only boot from (and I am on live) 8.04 version, because of some weird freeze at loading in 10.04 live that I expect to tackle soon.
I want to boot Ubuntu again.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec25ec25

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    78,161,919    77,955,072   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00094013

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74240DA0240D6688                       ntfs       Reservado para el sistema     
/dev/sda2        B0801B22801AEE9A                       ntfs                                     
/dev/sdb1        ff3c5309-5e99-4991-a7ac-b9dabe206226   ext3                                     
/dev/sdb5        c3aa330d-c046-4757-a366-195bf0d73669   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 ro  single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ff3c5309-5e99-4991-a7ac-b9dabe206226 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c3aa330d-c046-4757-a366-195bf0d73669 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.9GB: boot/grub/menu.lst
  30.9GB: boot/grub/stage2
  30.9GB: boot/initrd.img-2.6.24-28-generic
  30.9GB: boot/initrd.img-2.6.24-28-generic.bak
  30.9GB: boot/initrd.img-2.6.32-24-generic
  30.9GB: boot/initrd.img-2.6.32-25-generic
  30.8GB: boot/vmlinuz-2.6.24-28-generic
  30.8GB: boot/vmlinuz-2.6.32-24-generic
  30.9GB: boot/vmlinuz-2.6.32-25-generic
  30.9GB: initrd.img
  30.9GB: initrd.img.old
  30.9GB: vmlinuz
  30.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by erasmusp on 2011-03-29
Hi Erandros,

I had a similar problem and this is what worked for me:

First, grab a copy of the latest Ubuntu LiveCD and boot it. 

Open a terminal and type 

$*sudo*fdisk*-l 

Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt 

$*sudo*mount*/dev/sda1*/mnt 

If you have /boot on a separate partition, that need's to be mounted aswell. For reference, /dev/sda2 will be used. 
$*sudo*mount*/dev/sda2*/mnt/boot Make sure you don't mix these up, pay attention to the output of FDISK 
Now mount the rest of your devices and some other things needed in the chroot 

$*sudo*mount*--bind*/dev*/mnt/dev
$*sudo*mount*--bind*/proc*/mnt/proc
$*sudo*mount*--bind*/sys*/mnt/sys 

Now chroot into your system 

$*sudo*chroot*/mnt 

You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo. 
Now you need to edit the /etc/default/grub file to fit your system 

$*nano*/etc/default/grub 

When that is done you need to run update-grub to create the configuration file. If you have a separate /boot partition you need to mount it first! 

$*update-grub 

To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda 

$*grub-install*/dev/sda 

If you encounter any errors, try grub-install --recheck /dev/sda 

$*grub-install*--recheck*/dev/sda 

Press Ctrl+D to exit out of the chroot. 
Once you exit back to your regular console, undo all the mounting, first the /dev and others 

$*sudo*umount*/mnt/dev
$*sudo*umount*/mnt/sys
$*sudo*umount*/mnt/proc 

Now you can unmount the root system. (But if you have a separate boot partition which you mounted earlier, you have to unmount this first, or you will get a "device busy" error message.) 

$*sudo*umount*/mnt 

And you should be free to restart your system right into GRUB 2 and then into your system installation. 
If you had alternate OS entries, update-grub might say "Cannot find list of partitions!". Ignore it and continue - once you can boot into your linux installation, do so and then rerun update-grub and grub-install*/dev/sda as root.

---

### Post by Erandros on 2011-03-29
Should I erase all the stars? I don-t get it.

---

### Post by Erandros on 2011-03-29
It worked! Thanks... old options at grub are back...
Though the part of editing /etc/default/grub... I didn't get it, so I did nothing...

---

