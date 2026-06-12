---
title: "Another GRUB - Windows thread"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Nevyn on 2009-12-04
.Sorry to bring this to you but I've searched "recover grub" and similar, found many threads and tried the examples but have not been able to make GRUB boot properly.

Setup:
Ubuntu 9.04 upgraded to 9.10 installed on /media/disk; /dev/sda1 and have used it for a long time.
Windows XP recently installed on separate disk. The Win install naturally overwrote my bootloader and I can now only boot into Windows.
LiveCD unfortunately 9.04, ad I'm out of CD's.

This probably means I have GRUB 1.97 on my Ubuntu install and GRUB 1 on my LiveCD (?)
I've followed this guide: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD) and got the message ```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub /dev/sda1
sudo: grub-setup: command not found
```

I've followed this guide: [http://ubuntuforums.org/showthread.php?t=224351&highlight=recover+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=recover+grub) and got the message: ```
grub> find /media/disk/boot/grub/stage1

Error 15: File not found

```

I've downloaded GRUB 1.97 beta4 but I have no idea how I get the terminal grub-command to choose to replace the GRUB on /media/disk with this.

Am I way off or am I just missing the right command?

---

### Post by namok on 2009-12-04
Please follow the ['Boot Info Script: How to']("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by Nevyn on 2009-12-04
Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003659a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,262,859    39,262,797  83 Linux
/dev/sda3          39,262,860   482,528,339   443,265,480  83 Linux
/dev/sda4         482,528,340   488,392,064     5,863,725   5 Extended
/dev/sda5         482,528,403   488,392,064     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e3c3e3b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    81,947,564    81,947,502  83 Linux
/dev/sdb2          81,947,565   321,669,494   239,721,930   5 Extended
/dev/sdb5          81,947,628   321,669,494   239,721,867  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d7715

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdc2         204,796,620 1,953,503,999 1,748,707,380   f W95 Ext d (LBA)
/dev/sdc5         204,796,683 1,953,503,999 1,748,707,317   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="66f12859-967c-4ed8-92b9-4cae5efe21ad" TYPE="ext3" 
/dev/sda3: UUID="0128cf9e-a938-4c8c-abef-5c66ba2e2497" TYPE="ext3" 
/dev/sda5: UUID="cb46b1db-b761-431f-bb4e-3c12cbeb4033" TYPE="swap" 
/dev/sdb1: UUID="aa7a2a44-495b-423a-9f19-8f9a192a2437" TYPE="ext2" 
/dev/sdb5: UUID="4086295d-9d5f-43bc-abe6-00ea45e04460" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="9C5446A154467E50" TYPE="ntfs" 
/dev/sdc5: UUID="1DEC-3A4F" TYPE="vfat" 

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
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


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
#      password --md5 xxx
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
# kopt=root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66f12859-967c-4ed8-92b9-4cae5efe21ad

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-11-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.10, kernel 2.6.27-9-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-9-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 9.10, kernel 2.6.27-7-generic
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.10, memtest86+
uuid		66f12859-967c-4ed8-92b9-4cae5efe21ad
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=66f12859-967c-4ed8-92b9-4cae5efe21ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=0128cf9e-a938-4c8c-abef-5c66ba2e2497 /home           ext3    relatime        0       2
# /dev/sda5
UUID=cb46b1db-b761-431f-bb4e-3c12cbeb4033 none            swap    sw              0       0
# /dev/sdb1
UUID=aa7a2a44-495b-423a-9f19-8f9a192a2437 /media/warehouse	ext2 defaults	0	2
# /dev/sdb5
UUID=4086295d-9d5f-43bc-abe6-00ea45e04460 /media/hangar	ext3	defaults	0	2

=================== sda1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/menu.lst
   5.5GB: boot/grub/stage2
   5.5GB: boot/initrd.img-2.6.27-11-generic
   5.6GB: boot/initrd.img-2.6.27-7-generic
   5.5GB: boot/initrd.img-2.6.27-9-generic
   5.6GB: boot/initrd.img-2.6.28-16-generic
   5.5GB: boot/initrd.img-2.6.31-14-generic
   5.5GB: boot/initrd.img-2.6.31-15-generic
   5.5GB: boot/vmlinuz-2.6.27-11-generic
   5.5GB: boot/vmlinuz-2.6.27-7-generic
   5.5GB: boot/vmlinuz-2.6.27-9-generic
   5.6GB: boot/vmlinuz-2.6.28-16-generic
   5.6GB: boot/vmlinuz-2.6.31-14-generic
   5.5GB: boot/vmlinuz-2.6.31-15-generic
   5.5GB: initrd.img
   5.5GB: initrd.img.old
   5.5GB: vmlinuz
   5.6GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by namok on 2009-12-04
MBR of sda disk(250GB) looks good. It should be possible to start Ubuntu using this disk as first in BIOS. if not, install the grub just like in the guide. You entered a command:
```
grub> find [COLOR=Red]/media/disk[/COLOR]/boot/grub/stage1
```The correct command is: ```
grub> find /boot/grub/stage1
```grub should find (hd0,0),
next type:
```
root (hd0,0)
setup (hd0)
quit
```

---

### Post by Nevyn on 2009-12-04
Your post made me check BIOS again and sure enough, the very similar names on two of my hard drives had made me mix them up and had the wrong one as first boot device. Now the stuff I had done earlier gave result. Thanks a lot for helping me fix the issue!

---

