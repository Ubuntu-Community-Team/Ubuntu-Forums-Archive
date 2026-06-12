---
title: "dualboot install"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by zozo1 on 2009-03-24
Hello, and thanks for checking my post out. I have been trying to do a dual boot on a striped array. I realize now that this might not have been a good thing to do. After my first install attempt I got an error 17, while trying to load grub. I now also could not boot into windows, same error.I began with a partitioned striped array with XP installed on one of the partitions. It was my intent to install ubuntu on the other partition.I went ahead, and now I cannot access anything.
I thoought maybe it was a fake array issue and followed the   howto on fake satas,used all kinds of variants on dmraid option, and it got me nowhere. Finally I found a script that gave me.....................................
.............................. Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   624,992,759   624,992,697   7 HPFS/NTFS
/dev/sda2         624,992,760 1,249,985,519   624,992,760   5 Extended
Invalid MBR Signature found
Empty Partition

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff0470ff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   612,992,204   612,992,142  83 Linux
/dev/sdb2         612,992,205   625,137,344    12,145,140   5 Extended
/dev/sdb5         612,992,268   625,137,344    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="43755dad-548a-44bd-8a4d-0d714258290a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="7d90f45e-0541-4171-9ce4-92ca58d20230" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=43755dad-548a-44bd-8a4d-0d714258290a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=43755dad-548a-44bd-8a4d-0d714258290a

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		43755dad-548a-44bd-8a4d-0d714258290a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43755dad-548a-44bd-8a4d-0d714258290a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		43755dad-548a-44bd-8a4d-0d714258290a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43755dad-548a-44bd-8a4d-0d714258290a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		43755dad-548a-44bd-8a4d-0d714258290a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=43755dad-548a-44bd-8a4d-0d714258290a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7d90f45e-0541-4171-9ce4-92ca58d20230 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 106.2GB: boot/grub/menu.lst
 106.2GB: boot/grub/stage2
 106.1GB: boot/initrd.img-2.6.27-7-generic
 106.2GB: boot/vmlinuz-2.6.27-7-generic
 106.1GB: initrd.img
 106.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 


I am hoping someone here can decypher this to get the pertinent info from it. Presently, I can't boot into either of my OS's, and am connecting via ubuntu live cd.
motherboard....MSI
Processor...Amd Athlon 64x2 dual core 4200+
Bios vers....v1.6.042308
Physical mem.....2048MB
cache...1024MB
2x300 Gb maxtor sata drives

thanx
zozo1

---

### Post by ronparent on 2009-03-24
zozo1

I got your message and posted here so others may post thier own ideas. Your message to me didn't give me enough info. But I see above what I needed. First off, I see that you inadvertently installed Ubuntu on sdb1 (the first partition on your second hard drive). I hate to be bearer of bad news, but that probably destroyed your raid0 array. The array as raid0 is defined, in all likelyhood spanned both drives creating a stripped array. If that was the case, then the array was destroyed when the Linux partion was created on your second drive! My reply was delayed while I tested my hunch on my computer. When I ran the partitioner from the live CD it didn't see my array. If I had continued with an install, manual or otherwise, the process would have destroyed my WinXP install mounted on my raid0 array. To correct your impression in your private massage to me, I installed Ubuntu on a separate drive to avoid all possible problems with the array. I have already destroyed two windows installations trying to install two prior linux distributions (my own ignorant fault) and didn't want to chance a repeat performance. I do considerate it a deficency in the current ubuntu installation package in that an unwary user can easily bring disaster to their data on windows drive on a raid0 array.

The good news, I guess, is that you can configure grub to load ubuntu if it successfully installed. Maybe caljohnsmith can jump in and assist you here.

Good luck and best regards, ron

---

