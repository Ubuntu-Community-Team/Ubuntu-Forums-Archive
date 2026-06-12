---
title: "Can't seem to load up Windows"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-04-13
Well I installed Windows 7 (again) and then used the Ubuntu LiveCD to get grub back but I can't load up Windows >.<

here is what is on the menu.lst file

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
# kopt=root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=c95d1f16-a008-47a3-929b-a52438473996

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and fdisk -l output:

```
~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2c8e2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14761   118567701   83  Linux
/dev/sda2   *       14762       19270    36218542+   7  HPFS/NTFS
/dev/sda3           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris

```

maybe I got to modify it?

Also for some reason when I do this command it doesn't find the file look:

```
grub> find /boot/grub/stage1

Error 15: File not found

```

O.o?

---

### Post by moredhel on 2009-04-13
So at the moment can you load Ubuntu on your harddrive? Or only your cd (and so neither OS off your harddrive)?

---

### Post by AXeS on 2009-04-13
[http://ubuntuforums.org/showthread.php?p=7064680#post7064680](http://ubuntuforums.org/showthread.php?p=7064680#post7064680)
maybe that post could lead you in the right direction, if not then at least you a bit wiser.

---

### Post by lil_kid1333 on 2009-04-13
No I can't load Windows. I used the LiveCD to get grub back and now i'm in Ubuntu currently but I can't load up Windows it doesn't give me an option

---

### Post by steve101101 on 2009-04-13
did you try using super grub disk that you can make to restore your grub if you messed it up.

---

### Post by lil_kid1333 on 2009-04-13
> **AXeS said:**
> [http://ubuntuforums.org/showthread.php?p=7064680#post7064680](http://ubuntuforums.org/showthread.php?p=7064680#post7064680)
maybe that post could lead you in the right direction, if not then at least you a bit wiser.

Thanks I seem to have fixed it thanks to those post :) and some other page I saw :)

I just added

title Microsoft Windows 7
root (hd0,1)
savedefault
makeactive
chainloader +1

to the menu.lst 

thanks =]

---

### Post by Sonicgoo on 2010-10-31
Thanks this worked for me as well. 

I was getting a disk read error.

---

