---
title: "Grub2 Error 2"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by AlistairH on 2010-04-20
After my computer completely hung on me today I was forced to switched it off. When I rebooted, when Grub went into stage 1.5 it reported Error 2 and stopped.

I believe Error 2 is reported when the hard disk is not recognised or reported by BIOS. However, after rebooting and checking the BIOS settings, the hard disk is indeed being found by the BIOS.

Furthermore, on booting to a Live CD, the disk in question is accessible and all the files are visible and OK. I even did a backup from within the Live CD before going any further.

Thinking that the issue may by Grub2 related, I have since following the instruction at [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) but that didn't do anything for me.

I'm a little at a loss as to how to proceed. Any suggestion would be most welcome.

Thanks in advance.

PS: Sorry I forgot to mention I'm using Ubuntu 9.10

---

### Post by oldfred on 2010-04-20
Grub2 does not report many errors. Did you upgrade to 9.10 so you still have grub legacy(0.97) not grub2(1.97)?

[http://members.iinet.net.au/~herman546/p15.html#2_](http://members.iinet.net.au/~herman546/p15.html#2_)

If you installed parts of grub2 your system may be confused, grub & grub2 do not work together.

to see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by AlistairH on 2010-04-20
My Ubuntu 9.10 was a full clean install that I did when it first came out. Only when I rebooted after the computer completely froze did I start getting this issue.

As you'll see from the output from the script you mentioned, I have two physical hard disks. The master disk contains 9.10. The slave contains 9.04 but is not mounted automatically. I haven't accessed that drive for months.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.95 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008dd83

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    59,906,384    59,906,322  83 Linux
/dev/sda2          59,906,385    64,019,024     4,112,640  82 Linux swap / Solaris
/dev/sda3          64,019,025   390,716,864   326,697,840  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00056d69

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    78,156,224    78,156,162  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8fb1f62e-4828-40c5-bb5d-3e33d0fac596   ext4                                     
/dev/sda2        be665eeb-e150-4322-9ef9-9a2d4a1c0f9f   swap                                     
/dev/sda3        35e8a156-f89b-4450-aec6-2892b7971337   ext3       Data                          
/dev/sdb1        026432ae-2d64-46d1-b77b-2b4cc7ff32f6   ext3       UbuntuDrive                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8fb1f62e-4828-40c5-bb5d-3e33d0fac596
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8fb1f62e-4828-40c5-bb5d-3e33d0fac596 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=be665eeb-e150-4322-9ef9-9a2d4a1c0f9f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.31-14-generic
   1.5GB: boot/initrd.img-2.6.31-15-generic
   1.8GB: boot/initrd.img-2.6.31-16-generic
   1.2GB: boot/initrd.img-2.6.31-17-generic
   2.9GB: boot/initrd.img-2.6.31-19-generic
   3.3GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.4GB: boot/vmlinuz-2.6.31-15-generic
   1.5GB: boot/vmlinuz-2.6.31-16-generic
   1.8GB: boot/vmlinuz-2.6.31-17-generic
   1.7GB: boot/vmlinuz-2.6.31-19-generic
   3.3GB: boot/vmlinuz-2.6.31-20-generic
   3.3GB: initrd.img
   2.9GB: initrd.img.old
   3.3GB: vmlinuz
   1.7GB: vmlinuz.old

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
# kopt=root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=026432ae-2d64-46d1-b77b-2b4cc7ff32f6

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
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		026432ae-2d64-46d1-b77b-2b4cc7ff32f6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro splash vga=771 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro single 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro splash vga=771 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro splash vga=771 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=026432ae-2d64-46d1-b77b-2b4cc7ff32f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=be665eeb-e150-4322-9ef9-9a2d4a1c0f9f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  21.8GB: boot/grub/menu.lst
  21.9GB: boot/grub/stage2
  21.9GB: boot/initrd.img-2.6.28-11-generic
  22.0GB: boot/initrd.img-2.6.28-15-generic
  21.9GB: boot/initrd.img-2.6.28-16-generic
  22.0GB: boot/vmlinuz-2.6.28-11-generic
  22.0GB: boot/vmlinuz-2.6.28-15-generic
  21.8GB: boot/vmlinuz-2.6.28-16-generic
  21.9GB: initrd.img
  22.0GB: initrd.img.old
  21.8GB: vmlinuz
  22.0GB: vmlinuz.old
```

---

### Post by AlistairH on 2010-04-20
Bizarre!

I've been struggling with this all evening. The 9.10 drive is configured as a master with the 9.04 installation which I do not use, configured as a slave to the aforementioned master.

Just out of curiosity I disconnected the power from the slave and it booted straight into 9.10 after doing some file system checks.

I switched off, reconnected the power to the slave and it booted straight into 9.10 as it should.

I've marked this thread as solved simply because it is working again, though I still don't know why it did what it did.

Thanks for your assistance in any case.

---

