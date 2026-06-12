---
title: "error 17 from USB drive"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-06
I installed Hardy on a hard drive via USB...

After solving an error 21 problem here I am...

It booted fine on my linux laptop.  Now I brought that drive over to a windows XP desktop.  I select a 1 time boot menu and select boot from the USB drive. 

I get the grub menu and then this after selecting the only OS on there... 
"error 17: unable to mount selected partition"

A little background info...
I convinced this friend to try Ubuntu because their computer completely crashed wouldn't even boot.  They believed it was a virus.  They didn't want to spend 100+ dollars on an OS or buy a new hardrive/ computer...  I said "let me take the drive home.  I'll try and save the files on the drive and install another OS."

So I put the files they wanted to save on the desktop of the windows computer.  Wiped the drive and then installed hardy on it.

Can anyone help me solve this error 17?

---

### Post by hortstu on 2010-02-06
Will anyone suggest a better forum for this question?

---

### Post by -kg- on 2010-02-06
This forum is fine.  I don't have sufficient information yet, but I'll try.

I never have had very good luck installing an OS on one computer then transferring the drive to another.  According to my research, GRUB error 17 refers to a bad partition table.  [This link]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/") will tell you how to deal with it.  Of course, these procedures are best done on the computer that will be using the installation.

Does the computer in question have an internal hard drive?  Does it have a CD-ROM drive?  Is it an Eee-computer?  If it has an internal hard drive it would be best to install it on that.  An internal drive runs much faster than an external, and BIOS will boot to it by default.  I've mounted Ubuntu to an external before and in my experience it runs much slower due to the USB bottleneck.

Or maybe someone will pop in that knows more than I do.

---

### Post by hortstu on 2010-02-06
> **-kg- said:**
> I never have had very good luck installing an OS on one computer then transferring the drive to another.  According to my research, GRUB error 17 refers to a bad partition table.  [This link]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/") will tell you how to deal with it.  Of course, these procedures are best done on the computer that will be using the installation.

Does the computer in question have an internal hard drive?  Does it have a CD-ROM drive?  Is it an Eee-computer?  If it has an internal hard drive it would be best to install it on that.  An internal drive runs much faster than an external, and BIOS will boot to it by default.  I've mounted Ubuntu to an external before and in my experience it runs much slower due to the USB bottleneck.

Or maybe someone will pop in that knows more than I do.

Thanks.  Judging from your response I didn't explain myself clearly.  I'm already running hardy from my laptop.  I used my laptop to install hardy on a hard drive via a usb external connection.  I plan to install that hard drive into a friends computer internally after I get it working properly but I've gotten hung up a few places along the way.

Thanks for your help.  I'll check out that link.

---

### Post by hortstu on 2010-02-07
Maybe this will help...

```
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
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bfd06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,415,499   300,415,437  83 Linux
/dev/sda2         300,415,500   312,576,704    12,161,205   5 Extended
/dev/sda5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffa8ffa8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   224,829,674   224,829,612  83 Linux
/dev/sdb2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdb5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74e3c250-12d0-4313-ae9c-1d6e7b2f63bb   ext3                                     
/dev/sda5        300acce5-0b6b-409a-a1f8-a463045a0e2d   swap                                     
/dev/sdb1        8ca1995b-31b9-495c-bf74-62d48021775f   ext3                                     
/dev/sdb5        d25cf50e-9ec3-4f72-af28-7def510cd15e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash 
initrd		/boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single 
initrd		/boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8ca1995b-31b9-495c-bf74-62d48021775f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d25cf50e-9ec3-4f72-af28-7def510cd15e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/menu.lst
  27.9GB: boot/grub/stage2
  28.0GB: boot/initrd.img-2.6.24-23-generic
  27.9GB: boot/initrd.img-2.6.24-23-generic.bak
  28.0GB: boot/initrd.img-2.6.24-26-generic
  27.9GB: boot/initrd.img-2.6.24-26-generic.bak
  27.9GB: boot/vmlinuz-2.6.24-23-generic
  28.0GB: boot/vmlinuz-2.6.24-26-generic
  28.0GB: initrd.img
  28.0GB: initrd.img.old
  28.0GB: vmlinuz
  27.9GB: vmlinuz.old
```

---

### Post by -kg- on 2010-02-07
OK, I see what you are doing now.

I still stick with my statement though.  The very best method in installing Ubuntu (or any OS, for that matter) is to install it with the hard drive in the computer it is going to be used on.  That is, unless the computers that you're using are identical.

The inherent problems can be dealt with, but it's much easier to do it that way.  I would think that, if the two computers are dissimilar enough, that you would have quite a few problems with drivers and such.

Again, I could be wrong and not know what I'm talking about here (not one of my strongest points), but I've never attempted to install Ubuntu to a disk that was going to be installed in another computer.  I've always installed it *on* the computer, with the hard drive where it will reside.

As far as the data you saved; you could transfer that with a USB flash drive once the installation is done.  Just some thoughts.

---

### Post by presence1960 on 2010-02-07
```
## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
[COLOR="Red"]root		(hd1,0[/COLOR])
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8ca1995b-31b9-495c-bf74-62d48021775f ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, memtest86+
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
Above in red is why you get error 17. When you installed ubuntu from your machine it was (hd1) as your internal is (hd0). But when you put the disk into your friends machine it is (hd0)

Put the disk into your friends machine and at the GRUB menu highlight the Ubuntu kernel- DO NOT PRESS ENTER- instead press "e". Use the arrow keys to navigate to the (hd1,0) and change it to (hd0,0). press "b" to boot Ubuntu. Once in ubuntu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` Scroll down to the part I posted at the beginning and change the designation in all the root lines to read (hd0,0). Click Save on toolbar & close file.

Or if the disk is attached to your machine boot into Ubuntu, mount the external disk by clicking on it in a file browser (on left pane) in Places > Computer. It is mounted when you see directories on the right. Now run in terminal ```
gksu nautilus
``` This will open a browser with root priviledge. navigate from the root browser to the external disk's /boot/grub/menu.lst

Open menu.lst and change the 1 to 0 in the root line s as described above. Click save & close the file.

---

### Post by hortstu on 2010-02-07
> **-kg- said:**
> As far as the data you saved; you could transfer that with a USB flash drive once the installation is done.  Just some thoughts.

Thanks for all your input... This other drive isn't mine and it had some other issues that I couldn't work on from the owners computer.  They don't live too close to me so I'm hoping to get everything done that I can via USB at home.  Then on my next visit I'll install the drive and fine tune everything for them.

As far as the data goes, it is over 60Gigs and I don't have any flash drives that can handle that.

---

### Post by hortstu on 2010-02-07
presence,

Ok I will try this from my computer however, I've not brought this drive back to the computer it will reside in.

The problem I'm running into is when I try to boot via USB in another desktop that also has win XP running in it.  That's when I get error 17.  Not sure if that makes a difference.

I'm under the impression here that since it is still an external hooked up to a computer with an internal that this drive should still be recognized as (hd1,0)

I understand now that when I put it into the owners computer it will be the only drive and it must be recognized as a (hd0,0) but will this allow it to work in the xp machine where an internal drive already resides?

Thanks

---

