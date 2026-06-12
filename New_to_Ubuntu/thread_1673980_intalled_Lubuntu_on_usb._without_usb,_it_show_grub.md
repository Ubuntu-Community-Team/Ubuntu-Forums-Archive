---
title: "intalled Lubuntu on usb. without usb, it show grub rescue&gt;"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by santhust on 2011-01-23
Hi. help needed please.

I installed Lubuntu on a usb memory stick(pen-drive) from a live CD.[i wanted to install Lubuntu on a usb memory stick] During installation I took care to install it on "sdb". it got installed.
Problem: now, if i dont plug in that usb stick, I am given:

```
couldn't locate device... xxxxxxxx...xx (some thing like this)
grub rescue>
```

however if the usb stick is plugged in, I can boot in using my previously installed Ubuntu and Windows Vista (OS on sda)

Could someone please help.

the output of the bash_info_script055.sh is:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,489,534   164,489,472   7 HPFS/NTFS
/dev/sda2         164,491,262   488,396,799   323,905,538   5 Extended
/dev/sda5         164,491,264   454,510,107   290,018,844  83 Linux
/dev/sda6         475,168,768   488,396,799    13,228,032  82 Linux swap / Solaris
/dev/sda7         454,510,592   474,177,535    19,666,944  83 Linux
/dev/sda8         474,179,584   475,154,431       974,848  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
124 heads, 62 sectors/track, 1020 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048     7,385,087     7,383,040  83 Linux
/dev/sdb2           7,387,134     7,841,791       454,658   5 Extended
/dev/sdb5           7,387,136     7,841,791       454,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4A81E30A81E119A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39f21451-811b-4c15-aca4-f6f735f2bc3c   ext4                                     
/dev/sda6        12c3d2b7-6166-45b9-be40-786463ce10d1   swap                                     
/dev/sda7        c6e373c9-3417-43f8-ad0f-0fc4e96ece54   ext4                                     
/dev/sda8        b3be9bb0-a46c-4bf6-a123-80e674c1a519   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d0b67e6b-da05-4a71-95f4-142aece5e3f1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b54be4dd-67e1-4152-8139-11884dacb24f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/d0b67e6b-da05-4a71-95f4-142aece5e3f1 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4a81e30a81e119a
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12c3d2b7-6166-45b9-be40-786463ce10d1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 232.5GB: boot/grub/core.img
 120.6GB: boot/grub/grub.cfg
 136.9GB: boot/initrd.img-2.6.32-26-generic
 154.1GB: boot/initrd.img-2.6.35-23-generic
 153.7GB: boot/initrd.img-2.6.35-24-generic
 101.4GB: boot/vmlinuz-2.6.32-26-generic
 101.4GB: boot/vmlinuz-2.6.35-23-generic
  95.0GB: boot/vmlinuz-2.6.35-24-generic
 153.7GB: initrd.img
 154.1GB: initrd.img.old
  95.0GB: vmlinuz
 101.4GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4a81e30a81e119a
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=d0b67e6b-da05-4a71-95f4-142aece5e3f1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=d0b67e6b-da05-4a71-95f4-142aece5e3f1 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b3be9bb0-a46c-4bf6-a123-80e674c1a519 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 239.5GB: boot/grub/core.img
 239.5GB: boot/grub/grub.cfg
 233.6GB: boot/initrd.img-2.6.35-24-generic-pae
 239.4GB: boot/vmlinuz-2.6.35-24-generic-pae
 233.6GB: initrd.img
 239.4GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=d0b67e6b-da05-4a71-95f4-142aece5e3f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=d0b67e6b-da05-4a71-95f4-142aece5e3f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set d0b67e6b-da05-4a71-95f4-142aece5e3f1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4a81e30a81e119a
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=d0b67e6b-da05-4a71-95f4-142aece5e3f1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b54be4dd-67e1-4152-8139-11884dacb24f none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-24-generic-pae
    .9GB: boot/vmlinuz-2.6.35-24-generic-pae
   1.1GB: initrd.img
    .9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  20 32 2e 32 36 2e 31 2d  31 0a 52 65 70 6c 61 63  | 2.26.1-1.Replac|
00000010  65 73 3a 20 6c 69 62 67  74 6b 6d 6d 2d 32 2e 34  |es: libgtkmm-2.4|
00000020  2d 31 63 32 61 20 28 3c  3c 20 31 3a 32 2e 31 33  |-1c2a (<< 1:2.13|
00000030  29 0a 44 65 70 65 6e 64  73 3a 20 6c 69 62 63 36  |).Depends: libc6|
00000040  20 28 3e 3d 20 32 2e 32  2e 35 29 2c 20 6c 69 62  | (>= 2.2.5), lib|
00000050  63 61 69 72 6f 32 20 28  3e 3d 20 31 2e 32 2e 34  |cairo2 (>= 1.2.4|
00000060  29 2c 20 6c 69 62 63 61  69 72 6f 6d 6d 2d 31 2e  |), libcairomm-1.|
00000070  30 2d 31 20 28 3e 3d 20  31 2e 36 2e 34 29 2c 20  |0-1 (>= 1.6.4), |
00000080  6c 69 62 66 6f 6e 74 63  6f 6e 66 69 67 31 20 28  |libfontconfig1 (|
00000090  3e 3d 20 32 2e 38 2e 30  29 2c 20 6c 69 62 66 72  |>= 2.8.0), libfr|
000000a0  65 65 74 79 70 65 36 20  28 3e 3d 20 32 2e 32 2e  |eetype6 (>= 2.2.|
000000b0  31 29 2c 20 6c 69 62 67  63 63 31 20 28 3e 3d 20  |1), libgcc1 (>= |
000000c0  31 3a 34 2e 31 2e 31 29  2c 20 6c 69 62 67 6c 69  |1:4.1.1), libgli|
000000d0  62 32 2e 30 2d 30 20 28  3e 3d 20 32 2e 32 33 2e  |b2.0-0 (>= 2.23.|
000000e0  35 29 2c 20 6c 69 62 67  6c 69 62 6d 6d 2d 32 2e  |5), libglibmm-2.|
000000f0  34 2d 31 63 32 61 20 28  3e 3d 20 32 2e 32 34 2e  |4-1c2a (>= 2.24.|
00000100  30 29 2c 20 6c 69 62 70  61 6e 67 6f 31 2e 30 2d  |0), libpango1.0-|
00000110  30 20 28 3e 3d 20 31 2e  32 33 2e 30 29 2c 20 6c  |0 (>= 1.23.0), l|
00000120  69 62 70 6e 67 31 32 2d  30 20 28 3e 3d 20 31 2e  |ibpng12-0 (>= 1.|
00000130  32 2e 31 33 2d 34 29 2c  20 6c 69 62 73 69 67 63  |2.13-4), libsigc|
00000140  2b 2b 2d 32 2e 30 2d 30  63 32 61 20 28 3e 3d 20  |++-2.0-0c2a (>= |
00000150  32 2e 30 2e 32 29 2c 20  6c 69 62 73 74 64 63 2b  |2.0.2), libstdc+|
00000160  2b 36 20 28 3e 3d 20 34  2e 31 2e 31 29 2c 20 6c  |+6 (>= 4.1.1), l|
00000170  69 62 78 31 31 2d 36 2c  20 6c 69 62 78 72 65 6e  |ibx11-6, libxren|
00000180  64 65 72 31 2c 20 7a 6c  69 62 31 67 20 28 3e 3d  |der1, zlib1g (>=|
00000190  20 31 3a 31 2e 31 2e 34  29 0a 43 6f 6e 66 6c 69  | 1:1.1.4).Confli|
000001a0  63 74 73 3a 20 6c 69 62  67 74 6b 6d 6d 2d 32 2e  |cts: libgtkmm-2.|
000001b0  34 2d 31 63 32 61 20 28  3c 3c 20 31 3a 32 00 d3  |4-1c2a (<< 1:2..|
000001c0  49 cb 82 20 78 e8 02 00  00 00 00 f0 06 00 00 00  |I.. x...........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by ajgreeny on 2011-01-23
Unfortunately you installed grub on to the MBR of your internal hard disk, but the configuration files for grub are all on the lubuntu install, on the USB.  Therefore when the USB is not attached, grub can not run as it should, as most of its files are missing.

The first thing you need to do is run lubuntu on the USB and put grub onto the USB drive with ```
sudo grub-install /dev/sdb
```

I note you have two installs of ubuntu 10.10 as well as windows on the internal hard disk, so you should be able to restore grub to that disk from a live CD or USB
In the terminal of the live CD, type:
    ```
sudo mkdir /media/sda5
    sudo mount /dev/sda5 /media/sda5
```
To reinstall grub:
    ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```
Push enter and you’re done!

I show sda5 here, but you also have ubuntu 10.10 on sda7, and you will need to choose which you want to use for the grub.  Both are grub2, so if both are working OSs, it should not matter which you use.

Now when you boot up, if the USB disk is attached you will get grub from the USB with all OSs showing, and when the USB is missing you will get grub from either sda5 or sda7 which may not show the USB OS, depending on whether or not you have run **sudo update-grub** with the USB attached.

---

### Post by santhust on 2011-01-23
```
Now when you boot up, if the USB disk is attached you will get grub from the USB with all OSs showing, and when the USB is missing you will get grub from either sda5 or sda7 which may not show the USB OS, depending on whether or not you have run sudo update-grub with the USB attached.
```

It didn't help. I get a blank screen now, with usb not attached.
with usb attached I am able to boot into either of the OS :(

---

### Post by ajgreeny on 2011-01-23
OK, so run the boot-info-script again.  I can not figure out why it did not work if the first RESULTS.txt file is a true representation of your system.

You do still have the two versions of ubuntu on your hard disk, I assume, and have not made any major changes to your disks.

Also is the system set to boot first from the USB and second from the internal hard disk?

EDIT:
I have just noticed that the first paragraph of your RESULTS.txt file says:-
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub. but the first partition on the drive is your windows ntfs partition so will not contain the files that the system is looking for.
Now I am a bit baffled as to where you can go, other than trying the commands again, which I assume you copied as I wrote them, with /dev/sda5 and not dev/sda1

---

### Post by quadproc on 2011-01-23
> **santhust said:**
> Hi. help needed please.

I installed Lubuntu on a usb memory stick(pen-drive) from a live CD.[i wanted to install Lubuntu on a usb memory stick] During installation I took care to install it on "sdb". it got installed.

I think that you may have run into the fact that sdX labels can change.  These labels are assigned by the operating system and, if you do something like add or remove a USB device, then the label can change.

The way around this problem is to use UUIDs to specify the particular device that you want.  A UUID is a unique 128 bit number (represented in hex) which is assigned to the actual hardware.  If you want to see what is in your system do a 
```
sudo blkid
```and you will get a list.

Commands that allow you to specify devices using the /dev/sdX format will usually also allow you to use a UUID.  Here is an example from my fstab:

> # / was on /dev/sda9 during installation
UUID=71059336-6d53-4273-ad4e-49dd1a223ed4 /               ext3    errors=remount-ro 0       1I hope that this helps.

quadproc

---

### Post by Quackers on 2011-01-23
Santhust, you know what to do. You did it yesterday! :-)
What worked yesterday, when re-installing grub to the mbr? Do that again then :-)
But unplug the usb flash drive first! We can fix that later.
If you're not sure just come back :-)

---

### Post by santhust on 2011-01-24
Hi :)
Thanks all for your help.
the problem is solved. i attaching the .pdf file whose steps I followed. (Sorry, I couldn't get the same link when I googled it again. but since I saved a copy of it, I am attaching it after converting it to a pdf file.)
Hope it is help to some others too. :)

Thanks again all.

---

### Post by Quackers on 2011-01-24
Well done :-) It's fun isn't it :-)

---

