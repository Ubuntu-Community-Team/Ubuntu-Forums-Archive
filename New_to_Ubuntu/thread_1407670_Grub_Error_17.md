---
title: "Grub Error 17"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by jryprt on 2010-02-15
I dualboot Window 7 & 9.10 (updated from 9.04) Then installed EasyBCD onto Win 7 It boots 7 OK but after neogrub come up & I choose 9.10 the grub comes up & from grub I hit enter & get error 17 9.10 will not load. Here is some info. 
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   202,820,624   202,820,562   7 HPFS/NTFS
/dev/sda2         202,820,625   232,123,184    29,302,560  83 Linux
/dev/sda3         306,439,875   312,496,379     6,056,505   f W95 Ext d (LBA)
/dev/sda5         306,439,938   312,496,379     6,056,442  82 Linux swap / Solaris
/dev/sda4         232,123,185   306,439,874    74,316,690  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1EB20989B209669D                       ntfs                                     
/dev/sda2        db38e58b-8c17-4012-8602-0edc6e0c8f39   ext3                                     
/dev/sda4        ba8783fa-c156-4df8-b56e-6d4deb52c647   ext3                                     
/dev/sda5        b5e69887-0c95-43db-bfe3-de3b286fdc46   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD


## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, kernel 2.6.27-17-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 9.10, memtest86+
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=db38e58b-8c17-4012-8602-0edc6e0c8f39

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, kernel 2.6.27-17-generic
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 9.10, memtest86+
uuid		db38e58b-8c17-4012-8602-0edc6e0c8f39
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=db38e58b-8c17-4012-8602-0edc6e0c8f39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=ba8783fa-c156-4df8-b56e-6d4deb52c647 /home           ext3    relatime        0       2
# /dev/sda5
UUID=b5e69887-0c95-43db-bfe3-de3b286fdc46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 113.7GB: boot/grub/menu.lst
 113.6GB: boot/grub/stage2
 113.7GB: boot/initrd.img-2.6.27-17-generic
 113.7GB: boot/initrd.img-2.6.28-18-generic
 113.7GB: boot/initrd.img-2.6.31-19-generic
 113.6GB: boot/vmlinuz-2.6.27-17-generic
 113.6GB: boot/vmlinuz-2.6.28-18-generic
 113.6GB: boot/vmlinuz-2.6.31-19-generic
 113.7GB: initrd.img
 113.7GB: initrd.img.old
 113.6GB: vmlinuz
 113.6GB: vmlinuz.old

```
can someone help fix this 
Thanks

---

### Post by jryprt on 2010-02-15
got it used this [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) 
reinstalled 9.10

---

### Post by hortstu on 2010-02-15
Recently had a similar problem...

[http://ubuntuforums.org/showthread.php?t=1400104](http://ubuntuforums.org/showthread.php?t=1400104)

This is where I got help.

The post that I think will help you is this one...
[http://ubuntuforums.org/showpost.php?p=8788338&postcount=7](http://ubuntuforums.org/showpost.php?p=8788338&postcount=7)
See if you have the same problems presence points out for me.

I see our situations are different sorry this is the best I can do for you.

---

