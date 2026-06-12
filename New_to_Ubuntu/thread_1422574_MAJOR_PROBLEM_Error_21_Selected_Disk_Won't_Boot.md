---
title: "MAJOR PROBLEM: Error 21: Selected Disk Won't Boot"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-03-05
Ok guys, I have ubuntu 8.04.2 installed on a USB external Hard drive.

IT WORKED PERFECTLY for a long time, then all of a sudden It didnt boot at all.

So I went on a live dvd, and did a fdisk -l, and the boot partition for the /dev/sda1 was not flagged.

So I flagged it bootable, restarted and got the Error 21 after the grub timer was done.

I see a /dev/sda1 /dev/sda2 /dev/sda5 on fdisk-l while in the live dvd environment, I only set /dev/sda1 to bootable and it gave me the error.

I tried to set them all to bootable and grub didnt even come up at all.

Anyone got a fix for this, it is my work computer and I am in dire need of help :(.

---

### Post by kansasnoob on 2010-03-05
If you're able to boot a Live CD (or DVD) while all drives are plugged in post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ericeclifford on 2010-03-05
Thanks for the help, I am so irritated right now lol, I have work to do by today and this problem came out of nowhere. Now prior to this I had a solid state disk in here, but it worked fine with it in, I took it out recently and I believe it worked fine even after, but not 100% sure.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00008152

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,479,759   300,479,697  83 Linux
/dev/sda2         300,479,760   312,576,704    12,096,945   5 Extended
/dev/sda5         300,479,823   312,576,704    12,096,882  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e436c1de-bff2-44cc-b2af-67c6724b071d   ext3                                     
/dev/sda5        c309eeb3-44f4-4e3c-bce0-9dd2388a8f2c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=e436c1de-bff2-44cc-b2af-67c6724b071d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=e436c1de-bff2-44cc-b2af-67c6724b071d ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=e436c1de-bff2-44cc-b2af-67c6724b071d ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e436c1de-bff2-44cc-b2af-67c6724b071d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e436c1de-bff2-44cc-b2af-67c6724b071d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e436c1de-bff2-44cc-b2af-67c6724b071d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c309eeb3-44f4-4e3c-bce0-9dd2388a8f2c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  31.4GB: boot/grub/menu.lst
  31.4GB: boot/grub/stage2
  31.4GB: boot/initrd.img-2.6.24-23-generic
  31.4GB: boot/initrd.img-2.6.24-23-generic.bak
  31.5GB: boot/initrd.img-2.6.24-24-generic
  31.4GB: boot/initrd.img-2.6.24-24-generic.bak
  31.4GB: boot/vmlinuz-2.6.24-23-generic
  31.5GB: boot/vmlinuz-2.6.24-24-generic
  31.5GB: initrd.img
  31.4GB: initrd.img.old
  31.5GB: vmlinuz
  31.4GB: vmlinuz.old
```

---

### Post by psusi on 2010-03-05
The bootable flag only tells the DOS MBR which partition's boot sector should be loaded to boot the system.  It is meaningless since you have grub installed.  Fdisk should not have let you set more than one active at a time anyhow since only one partition can be the dos/windows boot partition at any given time.

It sounds like grub was installed on the drive you yanked out so it is now missing.  You need to reinstall it on the drive that is still there.

---

### Post by psusi on 2010-03-05
Actually you didn't mention that the error happens AFTER the grub menu, not before.  Now that I look at the output from the boot info script, the problem is that your menu.lst is pointing to hd1 instead of hd0.  Change all of the hd1 to hd0.

---

### Post by ericeclifford on 2010-03-05
DUDE you fixed it, you are my new Ubuntu IDOL.

Btw I live in Palm Bay Florida, I have family in Orlando :). 

But as far as  I know it is working, it is just doing a disk check right now, but I think you nailed it man.

I cant tell you how much I appreciate this guys.

Let me know if there is anything I can do for you.

(fix) was to change the 1 to 0 like the above said.

THANKS AGAIN!

---

### Post by kansasnoob on 2010-03-05
> **psusi said:**
> Actually you didn't mention that the error happens AFTER the grub menu, not before.  Now that I look at the output from the boot info script, the problem is that your menu.lst is pointing to hd1 instead of hd0.  Change all of the hd1 to hd0.

+1!

I'm curious why an external drive seems to be the only drive?

It appears that you've removed a drive????????????

---

### Post by ericeclifford on 2010-03-05
> **kansasnoob said:**
> +1!

I'm curious why an external drive seems to be the only drive?

It appears that you've removed a drive????????????

Well I had a solid state disk in a IDE port.

I removed it one day, then next thing you know grub got screwed.

I think because the SSD had grub installed to on it, was the reason why my external USB hardrive got confused and changes menu.lst.

Im sure it is more technical than that, but I think it is based on that problem.

---

### Post by psusi on 2010-03-05
While you had both drives, the one you have Ubuntu on was hd1 so all was well.  When you removed the SSD, hd1 became hd0.

---

