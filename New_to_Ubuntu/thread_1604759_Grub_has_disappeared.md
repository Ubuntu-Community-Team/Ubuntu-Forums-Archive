---
title: "Grub has disappeared"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by mosquetero on 2010-10-24
Hi!

It's a long time since I used Ubuntu, almost a year, so I feel a bit newbie again. Today I created a partition in my hard drive and I deployed Ubuntu 10.10 on it. The installation went perfectly but when I boot the computer, there is not GRUB menu or anything, so Windows boots and starts as if nothing had happened. I checked the hard drive in windows and it is smaller which means that the partition has actually been made but I have no clue about how can I access Ubuntu. Can you help me please?

Thanks a lot

---

### Post by oldfred on 2010-10-24
So we can see what installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by akand074 on 2010-10-24
Or might be easiest just to reinstall [grub]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") from a Live CD

---

### Post by mosquetero on 2010-10-24
> **oldfred said:**
> So we can see what installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Thank you. This is what I got

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   412,222,472   412,015,625   7 HPFS/NTFS
/dev/sda3         412,223,486   488,394,751    76,171,266   5 Extended
/dev/sda5         412,223,488   413,237,247     1,013,760  82 Linux swap / Solaris
/dev/sda6         413,239,296   488,394,751    75,155,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0EF20F9BF20F8665                       ntfs       Reservado para el sistema     
/dev/sda2        984C12FA4C12D33C                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        34feeda5-379b-4dcc-90ea-6fdea0baf49b   swap                                     
/dev/sda6        76933082-7a7d-494c-827d-1c11eefedf4c   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=76933082-7a7d-494c-827d-1c11eefedf4c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=76933082-7a7d-494c-827d-1c11eefedf4c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 76933082-7a7d-494c-827d-1c11eefedf4c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0ef20f9bf20f8665
	chainloader +1
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=76933082-7a7d-494c-827d-1c11eefedf4c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34feeda5-379b-4dcc-90ea-6fdea0baf49b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 244.1GB: boot/grub/core.img
 237.4GB: boot/grub/grub.cfg
 246.8GB: boot/initrd.img-2.6.35-22-generic
 244.1GB: boot/vmlinuz-2.6.35-22-generic
 246.8GB: initrd.img
 244.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 0f 00 00 fe  |...........x....|
000001d0  ff ff 05 fe ff ff 02 78  0f 00 00 d0 7a 04 00 00  |.......x....z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-10-24
For some reason Grub has not been installed in the mbr of your hard drive. In order to remedy this you should boot from your Ubuntu Live CD and then enter the commands below, one line at a time, into a terminal.

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot without the Live CD in the drive and when Ubuntu boots run
sudo update-grub
in a terminal. When grub.cfg is generated watch to see whether the Windows partition is picked up.

*** Please note that after this Windows may not be bootable and the Windows bootloader may need to be repaired using the Windows repair disc.

---

