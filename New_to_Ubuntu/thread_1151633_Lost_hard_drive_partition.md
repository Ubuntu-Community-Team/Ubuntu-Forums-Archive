---
title: "Lost hard drive partition"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by studiodude on 2009-05-07
Hi All,

I recently merged two partitions together using Gparted, one was a linux partition i created at the install process and one was an old windows partition that I emptied with the purpose of merging.  

First I deleted the windows partition, then resized the existing linux partition into its space and set Gparted to reformat the partition as ext3 -(as was the original linux partition) All went well it seemed, and I can see the drive in "places" and file browser but I cant access the drive in any way - i cant write to it, or indeed mount any of the partitions including my windows partition. 

What I was intending to do was move my home/ folder there as I keep running out of space there...........

Can anyone help? Did I reformat it wrongly - thanks in advance.

---

### Post by Didius Falco on 2009-05-07
download the little (57k) script in my signature to your desktop.

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named RESULTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

I suspect it'd going to be just a matter of fixing the changed UUID for that partition, but it's better to have that info so whoever is around can see what is up.

Regards,

Didius

---

### Post by studiodude on 2009-05-07
Ok, here goes ............. thank you very much for this, I appreciate all the great work that goes on here.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 164730573.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83c8036e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065    60,629,309    60,613,245   7 HPFS/NTFS
/dev/sda3         164,730,510   234,436,544    69,706,035   f W95 Ext d (LBA)
/dev/sda5         164,730,573   198,788,372    34,057,800   b W95 FAT32
/dev/sda6         198,788,436   202,997,339     4,208,904  82 Linux swap / Solaris
/dev/sda7         202,997,403   234,436,544    31,439,142  83 Linux
/dev/sda4          60,629,310   164,730,509   104,101,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B6D8C23FD8C1FD9D" LABEL="WINDOWS" TYPE="ntfs" 
/dev/sda4: UUID="7db5ef0a-0fc7-450c-8ee4-10a02a61711b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1320-6FF5" TYPE="vfat" 
/dev/sda6: UUID="043f22c5-68cf-46e9-ad34-c5ed377ab39b" TYPE="swap" 
/dev/sda7: UUID="2dd4158b-a928-4303-96f7-563321622c6f" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marc)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

timeout=1

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\Windows="Windows XP Pro" /fastdetect


=========================== sda7/boot/grub/menu.lst: ===========================

# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,6)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz
foreground = ffffff
background = 555500

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
timeout		5

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
# kopt=root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2dd4158b-a928-4303-96f7-563321622c6f

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
# howmany=2

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


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/memtest86+.bin
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST







=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=2dd4158b-a928-4303-96f7-563321622c6f /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=043f22c5-68cf-46e9-ad34-c5ed377ab39b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 118.4GB: boot/grub/menu.lst
 118.5GB: boot/grub/stage2
 118.4GB: boot/initrd.img-2.6.24-19-generic
 118.5GB: boot/initrd.img-2.6.24-19-generic.bak
 118.5GB: boot/initrd.img-2.6.24-23-generic
 118.4GB: boot/initrd.img-2.6.24-23-generic.bak
 118.6GB: boot/initrd.img-2.6.27-11-generic
 112.5GB: boot/initrd.img-2.6.28-11-generic
 118.4GB: boot/vmlinuz-2.6.24-19-generic
 118.5GB: boot/vmlinuz-2.6.24-23-generic
 118.5GB: boot/vmlinuz-2.6.27-11-generic
 118.6GB: boot/vmlinuz-2.6.28-11-generic
 112.5GB: initrd.img
 118.6GB: initrd.img.old
 118.6GB: vmlinuz
 118.5GB: vmlinuz.old
```

---

### Post by Didius Falco on 2009-05-07
If you simply want to have a separate /Home partition, then follow this tutorial to set it up:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I'd delete that partition and start fresh from this. Bookmark this website, too - lots of good stuff in there.

Regards,

Didius

PS, everything looks okay in the readout, so it shouldn't be a problem...

---

### Post by studiodude on 2009-05-07
Thanks Didius, looking at that tutorial now - great website - thanks for the time.

---

### Post by studiodude on 2009-05-07
ok, the tutorial in the link given in a previous post falls over for me with an error about permissions, i suppose its to do with me trying to move my home folder rather than the broken partition, though it could be either.

The partition I want to write to will mount and I can see a folder called lost and found which has a small icon-tag thing in the shape of an orange rounded edged rectangle with a cross in it and when i try to open it it tells me i dont have permission (in file browser).  I dont remember setting any permissions for that drive and right clicking on the properties /permissions gives the following.

YOU ARE NOT THE OWNER SO YOU CANT CHANGE THESE PERMISSIONS


  I am thinking now that I have a "whole month" whoopee....! of experience with my ubuntu installation that I may back up all my important files and start the whole hard drive anew including XP, as my system is a bit cobbled together at the moment and I feel I can cope with the trauma (!) but I would love to know how I managed to create a 50gig partition and some how not give myself access to it!! What kind of dumb*ss am I?  -LOL :confused:

Thanks again for any guidance

---

### Post by studiodude on 2009-05-07
I got to write to the partition in the end by opening Gparted and changing the file system of the drive to FAT32 - Will live with this a while longer and consider my total reformatting of the hard drive option while I learn some more - I do now know that I can select a partition for the home directory during the install, something i missed when I originally installed UBUNTU.

---

