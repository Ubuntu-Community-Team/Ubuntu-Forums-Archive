---
title: "Grub only boots Ubuntu, not Windows"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Elpram on 2009-01-25
Hi,

I had reinstalled windows, thereby wiping out grub.  I've now reinstalled it, but when I select WIndows XP, it flicks to "loading GRUB stage2" and then right back to the grub menu....But I can boot into Ubuntu fine.

Here is my fdisk -l

```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb55bb55b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde88de88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2370    19036993+  83  Linux
/dev/sdb2            2371        2434      514080   82  Linux swap / Solaris
```

And here is the output of the boot_info_script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 21666807 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 21750855 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Boot file info:     
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb55bb55b

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   80,276,804   80,276,742   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde88de88

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63   38,074,049   38,073,987  83 Linux
/dev/sdb2         38,074,050   39,102,209    1,028,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="20cec954-8b5b-4f82-b784-fd190a2e1407" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="3bfe6c45-e83f-416f-84cc-2b5eaef3bff6" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)



varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)

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
# kopt=root=UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
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
rootnoverify		(hd0,0)
#savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=20cec954-8b5b-4f82-b784-fd190a2e1407 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb2 :
UUID=3bfe6c45-e83f-416f-84cc-2b5eaef3bff6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdb1: Location  of files loaded by Grub: ===================


  11.1GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  11.0GB: boot/initrd.img-2.6.24-16-generic
  11.0GB: boot/initrd.img-2.6.24-16-generic.bak
  11.1GB: boot/initrd.img-2.6.24-22-generic
  11.0GB: boot/initrd.img-2.6.24-22-generic.bak
  11.0GB: boot/vmlinuz-2.6.24-16-generic
  11.1GB: boot/vmlinuz-2.6.24-22-generic
  11.1GB: initrd.img
  11.0GB: initrd.img.old
  11.1GB: vmlinuz
  11.0GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

I also can't seem to mount my Windows partition anymore either.

Any help would be much appreciated.  Thanks.

---

### Post by theozzlives on 2009-01-25
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

---

### Post by Elpram on 2009-01-25
Yeah, I've tried reinstalling grub several times in a few different ways, but to no avail.  Again, it's only Windows that won't boot.

---

### Post by caljohnsmith on 2009-01-25
It looks like you accidentally ran "setup (hd0,0)" at some point, because you have Grub installed to the boot sector of your Windows partition. That's not good because then you can't boot, mount, or read that partition until you fix it. But fortunately the fix is usually easy, if you can boot your Windows XP Install CD, go to the command line (recovery console), and do:
```
fixboot
```
And then you should be able to boot Windows using the Grub entry you all ready have in your menu.lst. Let me know how it goes or if you run into problems.

---

### Post by Elpram on 2009-01-25
Well, I'm trying to get into the recovery console, but when I'm presented with the partition list, my windows is listed as "unknown" and there is no "press r for recovery"....Although this might be because of the installation CD I'm using (I had set it up to auto-install)
I'll try and get another installation cd.

---

### Post by caljohnsmith on 2009-01-26
Elpram, if you can't get your hands on a Windows Install CD that will work, there's a good possibility you can fix the Windows partition boot sector with "testdisk" in Ubuntu. Let me know if you want directions for how to do that.

---

### Post by Elpram on 2009-01-26
Well I managed to find an ISO with on the recovery mode on it; I can now only boot into windows again.  Apparently whatever directions I followed messed me up, would you mind telling me how I should get grub back?

Thanks a ton.

---

### Post by caljohnsmith on 2009-01-26
If you used any of the automated repair options from the Windows CD, probably what happened is it also ran "fixmbr" which overwrites Grub in the MBR (Master Boot Record). To fix that, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
Then I think you should be all set, but let me know if you run into problems.

---

