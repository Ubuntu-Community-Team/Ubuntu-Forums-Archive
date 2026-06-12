---
title: "Trouble with dual booting Ubuntu and opensuse"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-06-29
Hi,
I 'av installed ubuntu(created a ext4 partition) on the system which had opensuse 11.1. but when i want to login to suse it doesnt boot. It says "fsck failed for at least one file system(not /) please repair manually and reboot".

here is my grub/menu.lst {Ubuntu (grub 1.5)}

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default	 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	 3	

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title	 Windows 95/98/NT/2000
# root	 (hd0,0)
# makeactive
# chainloader	+1
#
# title	 Linux
# root	 (hd0,1)
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a1b98979-504b-4601-bb3f-3347dddb6ddc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a1b98979-504b-4601-bb3f-3347dddb6ddc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title	 Ubuntu 9.04, kernel 2.6.28-13-generic
uuid	 a1b98979-504b-4601-bb3f-3347dddb6ddc
kernel	 /boot/vmlinuz-2.6.28-13-generic root=UUID=a1b98979-504b-4601-bb3f-3347dddb6ddc ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-13-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid	 a1b98979-504b-4601-bb3f-3347dddb6ddc
kernel	 /boot/vmlinuz-2.6.28-13-generic root=UUID=a1b98979-504b-4601-bb3f-3347dddb6ddc ro single
initrd	 /boot/initrd.img-2.6.28-13-generic

title	 Ubuntu 9.04, kernel 2.6.28-11-generic
uuid	 a1b98979-504b-4601-bb3f-3347dddb6ddc
kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=a1b98979-504b-4601-bb3f-3347dddb6ddc ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-11-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid	 a1b98979-504b-4601-bb3f-3347dddb6ddc
kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=a1b98979-504b-4601-bb3f-3347dddb6ddc ro single
initrd	 /boot/initrd.img-2.6.28-11-generic

title	 Ubuntu 9.04, memtest86+
uuid	 a1b98979-504b-4601-bb3f-3347dddb6ddc
kernel	 /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title	 Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title	 openSUSE 11.1 - 2.6.27.23-0.1 (on /dev/sda1)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.27.23-0.1-default root=/dev/disk/by-id/ata-WDC_WD1600BEVS-60RST0_WD-WXC707318338-part1 resume=/dev/disk/by-id/ata-WDC_WD1600BEVS-60RST0_WD-WXC707318338-part7 splash=verbose showopts vga=0x317 
initrd	 /boot/initrd-2.6.27.23-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title	 Failsafe -- openSUSE 11.1 - 2.6.27.23-0.1 (on /dev/sda1)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.27.23-0.1-default root=/dev/disk/by-id/ata-WDC_WD1600BEVS-60RST0_WD-WXC707318338-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317 
initrd	 /boot/initrd-2.6.27.23-0.1-default
savedefault
boot

What changes should I do now.
Thanks

---

### Post by bhargava470 on 2009-06-29
The issue is resolved now. Just needed to change the fstab entries

---

