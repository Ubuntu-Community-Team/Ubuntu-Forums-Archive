---
title: "grub error 15"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by j-d33zy on 2010-01-24
hi, i'm having trouble getting grub to work again on my laptop, i had ubuntu 9.04 installed and also windows xp. it was running a dual boot configuration with grub as the boot loader. I installed backtrack 4 (which is now based on ubuntu) and grub now only lets me get into windows and backtrack, whenever i push any ubuntu entry (recovery, memtest, etc) it gives me a grub 15 error. here is my grub menu.lst file:

```
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
# kopt=root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03a7899e-456a-41fd-a7a8-3035caa32c4a

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=03a7899e-456a-41fd-a7a8-3035caa32c4a/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9 (on sda7)
root        (hd0,6)
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
root        (hd0,6)
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot

```what do i need to do to get it working again? also my ubuntu partiton is formatted ext4 while the backtrack partition is ext3.

do i need to edit the menu.lst file on the ubuntu partition too?

---

### Post by 73ckn797 on 2010-01-24
What is the result of:
```
sudo fdisk -l
``` in terminal?

---

### Post by presence1960 on 2010-01-24
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by j-d33zy on 2010-01-25
on a live cd, this is what i got for fdisk:
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd25cd25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7650       38913   251128080    5  Extended
/dev/sda5           38287       38913     5036346   82  Linux swap / Solaris
/dev/sda6            7650       35713   225424017   83  Linux
/dev/sda7           35714       38286    20667591   83  Linux

Partition table entries are not in disk order
```

---

### Post by j-d33zy on 2010-01-25
...and the info script:
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcd25cd25

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,880,239   122,880,177   7 HPFS/NTFS
/dev/sda2         122,881,185   625,137,344   502,256,160   5 Extended
/dev/sda5         615,064,653   625,137,344    10,072,692  82 Linux swap / Solaris
/dev/sda6         122,881,311   573,729,344   450,848,034  83 Linux
/dev/sda7         573,729,408   615,064,589    41,335,182  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6AE4A6BCE4A689C1" LABEL="winderp" TYPE="ntfs" 
/dev/sda5: UUID="b9c505a5-f478-4e53-9f09-52e5ca7f848e" TYPE="swap" 
/dev/sda6: LABEL="Ubuntu" UUID="b7b0b071-7cd5-4779-b024-01e11b807d2d" TYPE="ext4" 
/dev/sda7: UUID="03a7899e-456a-41fd-a7a8-3035caa32c4a" TYPE="ext3" 

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
/dev/sda6 on /media/Ubuntu type ext4 (rw,nosuid,nodev,uhelper=hal)
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

splashimage=(hd0,5)/boot/grub/splash.xpm

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
# kopt=root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7b0b071-7cd5-4779-b024-01e11b807d2d

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

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


title Backtrack 3 Final KDE
rootnoverify (hd0,6)
kernel /boot/vmlinuz vga=0x317 root=/dev/sda7
ro quiet splash autoexec=xconf;kdm
boot
makeactive
chainloader    +1



=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b9c505a5-f478-4e53-9f09-52e5ca7f848e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 223.4GB: boot/grub/menu.lst
  64.7GB: boot/grub/stage2
  64.7GB: boot/initrd.img-2.6.28-11-generic
  64.3GB: boot/initrd.img-2.6.28-13-generic
 224.4GB: boot/initrd.img-2.6.28-14-generic
 146.3GB: boot/initrd.img-2.6.28-15-generic
 211.2GB: boot/initrd.img-2.6.28-16-generic
 223.4GB: boot/initrd.img-2.6.28-17-generic
  64.8GB: boot/vmlinuz-2.6.28-11-generic
  74.4GB: boot/vmlinuz-2.6.28-13-generic
  94.7GB: boot/vmlinuz-2.6.28-14-generic
 134.7GB: boot/vmlinuz-2.6.28-15-generic
 188.6GB: boot/vmlinuz-2.6.28-16-generic
 188.6GB: boot/vmlinuz-2.6.28-17-generic
 223.4GB: initrd.img
 211.2GB: initrd.img.old
 188.6GB: vmlinuz
 188.6GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03a7899e-456a-41fd-a7a8-3035caa32c4a

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=03a7899e-456a-41fd-a7a8-3035caa32c4a/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9 (on sda7)
root        (hd0,6)
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
root        (hd0,6)
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b9c505a5-f478-4e53-9f09-52e5ca7f848e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 307.4GB: boot/grub/menu.lst
 307.4GB: boot/grub/stage2
 307.5GB: boot/initrd.img-2.6.30.9
 307.5GB: boot/vmlinuz-2.6.30.9
 307.5GB: initrd.img
 307.5GB: vmlinuz
```

neat little script you got there, very useful...

---

### Post by presence1960 on 2010-01-25
When you installed Backtrack it overwrote GRUB on MBR. I would put GRUB back with the Ubuntu Live CD. Boot the Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5) (hd0,6)". 
5. Type "root (hd0,5)"
6. Type "setup (hd0)"
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

If you can't boot backtrack from the GRUB menu you have to edit the entry in menu.lst
Boot into Ubuntu and open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst
Scroll down to this:
```
title Backtrack 3 Final KDE
rootnoverify (hd0,6)
kernel /boot/vmlinuz vga=0x317 root=/dev/sda7
ro quiet splash autoexec=xconf;kdm
boot
makeactive
chainloader    +1
```

Change it to:
```
title           Backtrack Linux
rootnoverify    (hd0,6)
chainloader     +1
```

---

### Post by j-d33zy on 2010-01-26
i tried what you said, and i got ubuntu back, but now when i try to boot backtrack i get an error 13, invalid or unsupported executable format

i will post both menu.lst's here from both ubuntu and backtrack.

Ubuntu:
```
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

splashimage=(hd0,5)/boot/grub/splash.xpm

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
# kopt=root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7b0b071-7cd5-4779-b024-01e11b807d2d

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b7b0b071-7cd5-4779-b024-01e11b807d2d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


title Backtrack 4
rootnoverify (hd0,6)
chainloader    +1


```



Backtrack 4:
```
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
# kopt=root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03a7899e-456a-41fd-a7a8-3035caa32c4a

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=03a7899e-456a-41fd-a7a8-3035caa32c4a/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.30.9 (on sda7)
root		(hd0,6)
uuid		03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro quiet splash 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
root		(hd0,6)
uuid		03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=03a7899e-456a-41fd-a7a8-3035caa32c4a ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		03a7899e-456a-41fd-a7a8-3035caa32c4a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b7b0b071-7cd5-4779-b024-01e11b807d2d ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```


Thanks a bunch for all the help! :)

---

### Post by j-d33zy on 2010-01-26
nevermind, i figured it out, i just copied the ubuntu 8.10 segment from my backtrack grub and put it into my ubuntu grub, and it works great. Thanks for all the help! :)

---

### Post by presence1960 on 2010-01-26
> **j-d33zy said:**
> nevermind, i figured it out, i just copied the ubuntu 8.10 segment from my backtrack grub and put it into my ubuntu grub, and it works great. Thanks for all the help! :)

Glad you got it working! Enjoy.

P.S. I use BackTrack to recover data from unbootable windows machines.

---

### Post by SoFl W on 2010-01-26
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

---

