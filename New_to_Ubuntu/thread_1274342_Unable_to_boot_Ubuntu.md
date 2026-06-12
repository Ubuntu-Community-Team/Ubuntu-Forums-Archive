---
title: "Unable to boot Ubuntu"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by se_anderson on 2009-09-24
I cannot boot after after a synaptic update. It might be the drive. I've got work outstanding, I hope i can get it going:confused:

 I have used an install disk to boot up and have run the boot info script;

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009d611

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   964,622,924   964,622,862  83 Linux
/dev/sda2         964,622,925   976,768,064    12,145,140   5 Extended
/dev/sda5         964,622,988   976,768,064    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f46a8b7d-517b-4ce4-877e-bdd4f24ddce4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="7f018673-27c3-4d92-b9d9-d5779fd653ed" TYPE="swap" 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 9.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 9.04, kernel 2.6.24-18-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 9.04, kernel 2.6.24-17-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 9.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7f018673-27c3-4d92-b9d9-d5779fd653ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//10.1.1.3/stuff  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0

=================== sda1: Location of files loaded by Grub: ===================


 469.9GB: boot/grub/menu.lst
 469.8GB: boot/grub/stage2
 469.9GB: boot/initrd.img-2.6.24-16-generic
 470.0GB: boot/initrd.img-2.6.24-16-generic.bak
 469.9GB: boot/initrd.img-2.6.24-17-generic
 469.9GB: boot/initrd.img-2.6.24-17-generic.bak
 469.9GB: boot/initrd.img-2.6.24-18-generic
 470.0GB: boot/initrd.img-2.6.24-18-generic.bak
 469.9GB: boot/initrd.img-2.6.24-19-generic
 469.9GB: boot/initrd.img-2.6.24-19-generic.bak
 470.0GB: boot/initrd.img-2.6.24-21-generic
 469.9GB: boot/initrd.img-2.6.24-21-generic.bak
 470.0GB: boot/initrd.img-2.6.27-11-generic
 470.0GB: boot/initrd.img-2.6.28-11-generic
 469.9GB: boot/initrd.img-2.6.28-13-generic
 470.0GB: boot/initrd.img-2.6.28-14-generic
 470.0GB: boot/initrd.img-2.6.28-15-generic
 469.9GB: boot/vmlinuz-2.6.24-16-generic
 469.9GB: boot/vmlinuz-2.6.24-17-generic
 470.0GB: boot/vmlinuz-2.6.24-18-generic
 469.9GB: boot/vmlinuz-2.6.24-19-generic
 469.9GB: boot/vmlinuz-2.6.24-21-generic
 470.0GB: boot/vmlinuz-2.6.27-11-generic
 470.0GB: boot/vmlinuz-2.6.28-11-generic
 469.9GB: boot/vmlinuz-2.6.28-13-generic
 470.0GB: boot/vmlinuz-2.6.28-14-generic
 470.0GB: boot/vmlinuz-2.6.28-15-generic
 470.0GB: initrd.img
 470.0GB: initrd.img.old
 470.0GB: vmlinuz
 470.0GB: vmlinuz.old

---

### Post by se_anderson on 2009-09-24
tried this;
 sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 833501/30146560 files, 54900721/120577857 blocks (check in 4 mounts)

---

### Post by LewRockwell on 2009-09-24
Each trouble-call should be issued in a new thread

we need more specific detail regarding what is and is-not happening when you initiate the power-on sequence of the machine in question

.

---

### Post by Darkwing-Duck on 2009-09-24
You can also try this guide to help restore your MBR.
 
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)
 
Hope this helps ya out.

---

### Post by ibuclaw on 2009-09-24
Posts moved to a new thread.

---

### Post by LewRockwell on 2009-09-24
> **tinivole said:**
> Posts moved to a new thread.

Thanks Denny Crane!

.

---

