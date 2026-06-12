---
title: "GRUB no longer lists XP after Ubuntu upgrade to 9.04"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by NDX on 2009-05-18
Hi, I recently upgraded my Ubuntu partition to 9.04 which left Windows XP out of the list in GRUB. If I remember correctly, during the upgrade process it asked if I wanted to keep the current menu.lst or upgrade... and I chose the wrong option :p. 

I have tried [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") and it did not change anything.

 How would I get XP back in the list? Thanks a lot!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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
Disk identifier: 0x07a507a4

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   138,753,404   138,753,342  83 Linux
/dev/sda2    *    138,753,405   306,520,199   167,766,795   7 HPFS/NTFS
/dev/sda3         306,520,200   312,576,704     6,056,505   5 Extended
/dev/sda5         306,520,263   312,576,704     6,056,442  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dc76a7a6-dca7-423c-83b6-4adf3f38aa97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="3C98AD7098AD28FA" TYPE="ntfs" 
/dev/sda5: UUID="0810a732-95e0-4dac-8f4c-f1c7e85157b9" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
#timeout		3

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
# kopt=root=UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 ro

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, memtest86+
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
UUID=dc76a7a6-dca7-423c-83b6-4adf3f38aa97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0810a732-95e0-4dac-8f4c-f1c7e85157b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  15.2GB: boot/grub/menu.lst
    .2GB: boot/grub/stage2
    .1GB: boot/initrd.img-2.6.24-23-generic
    .1GB: boot/initrd.img-2.6.24-23-generic.bak
  14.4GB: boot/initrd.img-2.6.28-11-generic
    .1GB: boot/vmlinuz-2.6.24-23-generic
  14.4GB: boot/vmlinuz-2.6.28-11-generic
  14.4GB: initrd.img
  14.4GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```

---

### Post by NDX on 2009-05-18
I think I should note that the info above was generated with a live CD. I don't know if that would alter the information. I have managed to manually add XP back in but it says the device is not found. How do I tell which partition XP is located in?

I have tried:

title Windows XP
root (hd0,2)
saveddefault
makeactive
chainloader +1

I got the "(hd0,2)" by guessing from the "default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS" generated by the script.

Thanks again for the help if it comes!

---

### Post by Elfy on 2009-05-18
try (hd0,1) - grub numbers from 0 so the first partition is 0, second is 1 etc - same for harddrives - so your sda2 is hd0,1 fro grub

> /dev/sda1                  63   138,753,404   138,753,342  83 Linux
**/dev/sda2    *    138,753,405   306,520,199   167,766,795   7 HPFS/NTFS**
/dev/sda3         306,520,200   312,576,704     6,056,505   5 Extended
/dev/sda5         306,520,263   312,576,704     6,056,442  82 Linux swap / Solaris

---

### Post by NDX on 2009-05-18
Thanks that worked!

---

### Post by Celauran on 2009-05-18
Should be
```
title Windows XP
root (hd0,1)
saveddefault
makeactive
chainloader +1
```
as far as I can tell.

Bah, too slow.

---

### Post by NightwishFan on 2009-05-18
You could keep a supergrub disc around for situations such as these, it works great for Windows as well.

---

