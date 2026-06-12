---
title: "XP disappeared from Grub"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by rcbinwi on 2009-10-22
I just got an update on Jaunty, and now when I boot, the XP option is no longer in the Grub menu.  What can I do to get XP back on the list?  Thanks!

---

### Post by themusicalduck on 2009-10-22
Could you post the output of ```
cat /boot/grub/menu.lst
``` and ```
sudo fdisk -l
``` (lower case L)

You should be able to re-add the entry by editing your grub menu.lst, using something like this ```
title		Windows XP
rootnoverify	(hd0,0)
savedefault
map		(hd0) (hd0)
map		(hd0) (hd0)
chainloader	+1
```

But if you put details from those commands up, we could make an entry up that you can copy and paste.

---

### Post by LewRockwell on 2009-10-22
we experienced that as well

fortunately we had our fresh /boot/grub/menu.lst.backup to cut and paste from to tidy everything up quite nicely

we elaborated briefly about it here:> **LewRockwell said:**
> you can check for the kernel specifics by looking in your /boot directory

then you should make a backup copy of your /boot/grub/menu.lst```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```then you'll need to start a sudo session of gedit to make changes to your /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```When kernel updates require an update of the grub menu.lst file the update asks you what you want to do

You can then open a terminal session, backup the current menu.lst file(as above), and then feel secure in allowing the update session to update the grub menu.lst file since you have a backup

Then, if you need to make changes you can open two editing sessions and cut, paste, and save to your heart's content!

Honestly, once you figure out how to make backups and to compare files and to move, copy, and edit files...then *nix distros become MUCH more entertaining AND useful!

.

.

---

### Post by rcbinwi on 2009-10-22
Good point.  I thought I had a backup, but I was mistaken (or I put it somewhere that I can't find.)

Here's the whole grub file:
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
# kopt=root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=595fd4ae-ba0c-4ddf-96b4-13dc5341393c

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=595fd4ae-ba0c-4ddf-96b4-13dc5341393c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		595fd4ae-ba0c-4ddf-96b4-13dc5341393c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And here's fdisk -l:
```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4524    36290835    7  HPFS/NTFS
/dev/sda3            4525        7113    20796142+   5  Extended
/dev/sda5            4525        7000    19888438+  83  Linux
/dev/sda6            7001        7113      907641   82  Linux swap / Solaris

```

Thanks!

---

### Post by oldfred on 2009-10-22
About a third of the way down in menu.lst is this:
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs


and at the very bottom:
### END DEBIAN AUTOMAGIC KERNELS LIST

You probably had your windows stanza in the automagic  area so it was overwriten.

You entry does not need the map commands as it is on the same hard drive:

Your entry should be this, but put before or after the automagic lines:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader +1

---

### Post by rcbinwi on 2009-10-22
Problem solved, and menu.lst backed up properly.

While I have your attention, though . . .

How do you make blank lines in grub?

Thanks!

---

### Post by oldfred on 2009-10-22
You cannot do blank lines. You need both a title & blank root line. My work around, the dash is almost blank:

title        Grub Chainload Menu
root
title        -
root

---

### Post by rcbinwi on 2009-10-24
Thanks!  Got it.

---

