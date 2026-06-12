---
title: "Won't boot. Please look at my boot script?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-14
Here's the boot script if anyone has any suggestions.

```
Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bfd06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   165,148,199   165,148,137  83 Linux
/dev/sda2         300,415,500   312,576,704    12,161,205   5 Extended
/dev/sda5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris
/dev/sda3         212,266,845   300,415,499    88,148,655  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x531d9fcc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   320,159,384   320,159,322  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74e3c250-12d0-4313-ae9c-1d6e7b2f63bb   ext3                                     
/dev/sda3        5ec01415-5915-4e99-8d9c-f91c2262a279   ext3                                     
/dev/sda5        300acce5-0b6b-409a-a1f8-a463045a0e2d   swap                                     
/dev/sdb1        a8ae8287-4ef1-4ba5-87f4-9c43744b04d6   ext3       data                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/data              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1        /mnt/sdb1                ext3       (rw)
/dev/sda3        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=300acce5-0b6b-409a-a1f8-a463045a0e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

/dev/sda3 /home/ ext3 defaults 0 0


=================== sda1: Location of files loaded by Grub: ===================


  34.1GB: boot/grub/menu.lst
  34.1GB: boot/grub/stage2
  34.1GB: boot/initrd.img-2.6.24-23-generic
  34.1GB: boot/initrd.img-2.6.24-23-generic.bak
  34.1GB: boot/initrd.img-2.6.24-26-generic
  34.1GB: boot/initrd.img-2.6.24-26-generic.bak
  34.1GB: boot/initrd.img-2.6.24-27-generic
  34.1GB: boot/initrd.img-2.6.24-27-generic.bak
  34.1GB: boot/vmlinuz-2.6.24-23-generic
  34.1GB: boot/vmlinuz-2.6.24-26-generic
  34.1GB: boot/vmlinuz-2.6.24-27-generic
  34.1GB: initrd.img
  34.1GB: initrd.img.old
  34.1GB: vmlinuz
  34.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

The background to this issue is that I was trying to create a separate home partition and screwed it up somehow.

I'm about to wipe the system and reinstall unless someone has another suggestion

---

### Post by audiomick on 2010-02-15
My guess is that the computer is set to boot from the drive sdb, which has a grub on it that points to nothing.
I think that if you change the drives in the boot order (BIOS) to make it boot from sda1, that might allow you to boot. There is a grub there too, but it looks like it is complete and could work.

---

