---
title: "2 linux, 2 hard dirves"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by the wombat on 2009-09-04
hey all! 
well i downsized my station from a dual boot xp/linux machine and another ubuntu machine into one machine with 2 hard drives. so my grub menu work fine with linux/xp, and now i want to add the ubuntu drive to the menu.lst file. ubuntu is on a SATA while the other 2 are on an IDE. 
now... i booted into ubuntu and copied ITS menu.lst file and simply put it into the other linux grub menu file. only that doesnt work lol. so here is what the ubuntu part looks like in the xp/linux machine..
```

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=62344c33-9ac0-4592-85c8-6604d5185ace ro quiet splash 
initrd          /boot/initrd.img-2.6.28-15-generic
quiet
```

so i want to know, what do i need to add to this entry to make it just work?
heres the fdisk -l from the other linux OS...

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x689e689e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9786    78606013+   7  HPFS/NTFS
/dev/hda2            9787       19457    77682307+   5  Extended
/dev/hda5            9787       19057    74469276   83  Linux
/dev/hda6           19058       19457     3212968+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x397c397c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19012   152713858+  83  Linux
/dev/sda2           19013       19457     3574462+   5  Extended
/dev/sda5           19365       19457      746991   82  Linux swap / Solaris
/dev/sda6           19014       19364     2819376   82  Linux swap / Solaris

Partition table entries are not in disk order
```

any help is gonna be awesome!! thanks everyone!

---

### Post by Hospadar on 2009-09-04
Could you post (in code blocks like you've done) your entire menu.lst files from both machines?

---

### Post by LewRockwell on 2009-09-04
it is possible that a Super Grub Disk might assist you in this task

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by the wombat on 2009-09-04
surely, let me just copy those and ill post them in a min. 
now, what exactly will this super grub disk do? ive read around the website, and im just not 100% clear...

---

### Post by the wombat on 2009-09-04
ok here is the menu.lst from my ubuntu drive...
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=62344c33-9ac0-4592-85c8-6604d5185ace ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=62344c33-9ac0-4592-85c8-6604d5185ace

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

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro quiet splash 
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro  single
initrd          /boot/initrd.img-2.6.28-15-generic

title           Ubuntu 9.04, kernel 2.6.28-14-generic
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro quiet splash 
initrd          /boot/initrd.img-2.6.28-14-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro  single
initrd          /boot/initrd.img-2.6.28-14-generic

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro quiet splash 
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro  single
initrd          /boot/initrd.img-2.6.28-13-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro quiet splash 
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=62344c33-9ac0-4592-85
8-6604d5185ace ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

and here it is from the xp/linux machine...

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts fro
m 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the defa
ult entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the def
ault entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactiv
e editing
# control (menu entry editor and command-line)  and entries protected
 by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options be
low

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02


## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not wi
th the
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

splashimage=0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02/boot/grub/splash.xpm
.gz

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           BackTrack 4
uuid            0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02
kernel          /boot/vmlinuz-2.6.29.4 root=UUID=0e5e1caf-5dd2-4bb1-8
95f-29cbdfac1c02 ro quiet splash
initrd          /boot/initrd.img-2.6.29.4
quiet

title           Ubuntu
uuid            62344c33-9ac0-4592-85c8-6604d5185ace
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=62344c33-9a
c0-85c8-6604d5185ace ro quiet splash
initrd          /boot/initrd.im-2.6.28-15-generic
quiet

#title          Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
#uuid           0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02
#kernel         /boot/vmlinuz-2.6.29.4 root=UUID=0e5e1caf-5dd2-4bb1-8
95f-29cbdfac1c02 ro  single
#initrd         /boot/initrd.img-2.6.29.4

#title          Ubuntu 8.10, memtest86+
#uuid           0e5e1caf-5dd2-4bb1-895f-29cbdfac1c02
#kernel         /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the 
Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-li
nux OS
# on /dev/hdc1

```

hope that helps some :neutral:

---

### Post by zerhacke on 2009-09-04
I'm trying to work out in my head the mapping that you will have to use because the second hard drive is going to assume it is on /dev/sda since that's where it was when it was installed.

Can't work it out right now, though.  It's been a long day.

---

