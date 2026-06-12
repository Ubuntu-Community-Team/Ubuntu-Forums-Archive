---
title: "Dual boot with 2 Hard drives"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Denton Larson on 2011-04-20
Hi Everybody

This is what I have, I have a dual boot computer now but it is broke. Can I install a old hard drive in my machine Install Windows XP on a 80g and then load Ubuntu 10.04 LTS on the 500g. 

I did have a dual boot on the single drive and it worked fine but the I got stuck on a format of a USB stick for Ubuntu and somehow windows got erased. I am a clutz in this (I formated the USB stick with windows an anther machine)

Here is what I get when I select Windows XP

Anything you can pass along will be helpful, thank you in advance.

Denton Larson

---

### Post by Hippytaff on 2011-04-20
Hi and welcome. Before any body gives advice on this it is probably best if you can boot from a live cd and download and run the bottinfo script found [here]("http://sourceforge.net/projects/bootinfoscript/"). then post the results so that people can see wha is what :-)

---

### Post by Denton Larson on 2011-04-20
> **Hippytaff said:**
> Hi and welcome. Before any body gives advice on this it is probably best if you can boot from a live cd and download and run the bottinfo script found [here]("http://sourceforge.net/projects/bootinfoscript/"). then post the results so that people can see wha is what :-)

Here is what I have.


     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   496,442,107   496,442,045   7 HPFS/NTFS
/dev/sda2         496,443,390   976,773,119   480,329,730   5 Extended
/dev/sda5         496,443,392   969,254,911   472,811,520  83 Linux
/dev/sda6         969,256,960   976,773,119     7,516,160  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   976,707,583   976,705,536   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   123,379,199   123,379,137   7 HPFS/NTFS
/dev/sdd2         123,379,200   156,296,384    32,917,185   5 Extended
/dev/sdd5         123,379,263   154,818,404    31,439,142  83 Linux
/dev/sdd6         154,818,468   156,296,384     1,477,917  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3EA0-CFEB                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7c41c30a-d731-4f3b-8803-f8dbed1cdfeb   ext4                                     
/dev/sda6        40f1fc57-1735-42ac-8e4f-244171e14967   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        EA6854D268549F5F                       ntfs       My Passport                   
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        D0889C76889C5D32                       ntfs                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        d300eec1-1ab1-4f0b-be67-65fe2314527f   ext4                                     
/dev/sdd6        9fade630-88f4-4e91-a113-a2fe33054725   swap                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/way2cool          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdd5        /media/d300eec1-1ab1-4f0b-be67-65fe2314527f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/My Passport       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/D0889C76889C5D32  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/3EA0-CFEB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=7c41c30a-d731-4f3b-8803-f8dbed1cdfeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=7c41c30a-d731-4f3b-8803-f8dbed1cdfeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c41c30a-d731-4f3b-8803-f8dbed1cdfeb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c41c30a-d731-4f3b-8803-f8dbed1cdfeb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7c41c30a-d731-4f3b-8803-f8dbed1cdfeb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 22706c23706bfbc3
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=7c41c30a-d731-4f3b-8803-f8dbed1cdfeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=40f1fc57-1735-42ac-8e4f-244171e14967 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 456.1GB: boot/grub/core.img
 436.8GB: boot/grub/grub.cfg
 456.3GB: boot/initrd.img-2.6.32-29-generic
 456.3GB: boot/initrd.img-2.6.32-30-generic
 456.1GB: boot/vmlinuz-2.6.32-29-generic
 456.1GB: boot/vmlinuz-2.6.32-30-generic
 456.3GB: initrd.img
 456.3GB: initrd.img.old
 456.1GB: vmlinuz
 456.1GB: vmlinuz.old

=========================== sdd5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root=(hd2,5)
search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
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
insmod ext2
set root=(hd2,5)
search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	echo	Loading Linux 2.6.32-14-generic ...
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro quiet splash
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro single
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-13-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro quiet splash
	initrd /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-13-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro single
	initrd /boot/initrd.img-2.6.32-13-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=9fade630-88f4-4e91-a113-a2fe33054725 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


  65.6GB: boot/grub/core.img
  77.1GB: boot/grub/grub.cfg
  64.0GB: boot/initrd.img-2.6.32-14-generic
  65.6GB: boot/vmlinuz-2.6.32-14-generic
  64.0GB: initrd.img
  65.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e9 57 4d d6 cc 19 c2 e4  75 a8 d0 0e ab e5 c5 67  |.WM.....u......g|
00000010  47 23 5d d3 14 13 e5 21  d8 74 87 f1 48 ee e3 cc  |G#]....!.t..H...|
00000020  9c ed 4c c0 c8 b8 ea ba  66 82 41 69 77 58 c8 5b  |..L.....f.AiwX.[|
00000030  11 70 fb 95 70 00 00 01  09 1a 74 83 38 3e 97 5b  |.p..p.....t.8>.[|
00000040  4e 10 55 bd 78 b5 09 8e  a6 97 bf 27 cb 88 13 88  |N.U.x......'....|
00000050  d5 a3 11 54 a9 7e 5f a6  82 e3 dd 2a ea 57 6a ba  |...T.~_....*.Wj.|
00000060  b3 ab 3a 47 ae 7b 9e 9b  ef 38 f9 d7 31 3e 9a 8d  |..:G.{...8..1>..|
00000070  01 9e de 58 ea 5c ba 6c  c1 d7 23 61 fe 3a da b4  |...X.\.l..#a.:..|
00000080  63 41 74 1f 74 f5 1a 64  7e b1 70 83 ae 9b 28 15  |cAt.t..d~.p...(.|
00000090  79 35 a3 87 7e b4 66 cb  95 4d 16 84 8f 8c 97 54  |y5..~.f..M.....T|
000000a0  e9 81 8c b8 25 7e 09 95  4e c8 54 a8 78 a8 75 bd  |....%~..N.T.x.u.|
000000b0  36 21 da be 87 dd 34 22  a6 54 ba 68 de bb 8e f4  |6!....4".T.h....|
000000c0  d9 81 40 92 e6 3a 4a 87  dd 53 66 26 17 07 db 5d  |..@..:J..Sf&...]|
000000d0  3a 06 2d 62 ac 6a 05 38  9b 62 57 be 19 b8 1e a5  |:.-b.j.8.bW.....|
000000e0  dd 36 58 31 bb c9 83 10  34 a0 85 11 60 1d 86 23  |.6X1....4...`..#|
000000f0  06 e6 38 5f 8a ba d3 8a  bc 73 4d b5 6c 31 d7 1e  |..8_.....sM.l1..|
00000100  6c b1 d7 4f 01 f1 91 f2  69 b6 c9 5e fd 34 59 24  |l..O....i..^.4Y$|
00000110  07 2d eb 59 a0 7c 54 70  dc e7 59 60 39 08 24 47  |.-.Y.|Tp..Y`9.$G|
00000120  57 63 8b 6a 30 e9 43 a3  e9 a2 a8 4d fb 8a b5 63  |Wc.j0.C....M...c|
00000130  9a 0a ba ec 2b 54 a6 d1  92 fc 7d 68 de bb df 78  |....+T....}h...x|
00000140  45 6c 87 a2 0d 36 92 aa  a6 d3 66 63 87 c9 75 0b  |El...6....fc..u.|
00000150  be 3e 57 5c b9 54 d2 4e  67 5d 3c 9b cb ad b0 d5  |.>W\.T.Ng]<.....|
00000160  0b 73 c2 e2 6e 2c 04 85  ad 03 e0 f8 e3 8c ba d4  |.s..n,..........|
00000170  4c 1b 4a 38 67 3d d1 ce  8b c1 ad 89 45 9d 3e 6e  |L.J8g=......E.>n|
00000180  78 45 d3 07 e0 fd dc bc  67 79 6d 59 d6 41 d6 b8  |xE......gymY.A..|
00000190  7c d5 00 00 00 01 0a 1a  ef 03 e9 15 30 eb ba da  ||...........0...|
000001a0  44 e5 47 53 41 24 11 6f  8a ac cf e0 ef 2a 9e 49  |D.GSA$.o.....*.I|
000001b0  e7 ad 95 6f 3a 9a 3a ea  5d db 65 11 20 f9 00 fe  |...o:.:.].e. ...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 2e 1c 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  2e 1c 00 b8 72 00 00 00  |............r...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by Denton Larson on 2011-04-20
Now I have just the 1 hard drive,

   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   496,442,107   496,442,045   7 HPFS/NTFS
/dev/sda2         496,443,390   976,773,119   480,329,730   5 Extended
/dev/sda5         496,443,392   969,254,911   472,811,520  83 Linux
/dev/sda6         969,256,960   976,773,119     7,516,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3EA0-CFEB                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7c41c30a-d731-4f3b-8803-f8dbed1cdfeb   ext4                                     
/dev/sda6        40f1fc57-1735-42ac-8e4f-244171e14967   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/3EA0-CFEB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

---

### Post by Iusedtowearatie on 2011-04-20
A basic configuration:

Install the (wiped) 80G disk. Install XP on it.
Install the (wiped) 500G disk.
Boot the Ubuntu LiveCD.
Choose install.

Then take care where you select to install the Ubuntu OS. Leave the 80G disk out of it!

After usual installation steps you will hopefully end up with something like this:

80G: Grub plus XP
500G: Ubuntu, with the partitions you decided during setup.

If you want, you can go for more complex setups, with various crosswise partitions, eg for backup reasons, but then you would have to start with building partitions using a partitioning SW.

To wipe disks, I recommend dban (Darik's boot and nuke).

---

### Post by oldfred on 2011-04-20
Grub does not use boot flag, but windows has to have a boot flag (active partition) to boot, install or repair a NTFS partition. Your first boot script showed other drives without boot flags.

You can use gparted to add a boot flag, click on partition and right click manage flags. You also can use Disk Utility or command line.

set boot flag on for [COLOR=RoyalBlue]sda[/COLOR][COLOR=Red]2[/COLOR] (off on others) Change to your [COLOR=RoyalBlue]drive[/COLOR] & [COLOR=Red]partition(s)[/COLOR].
sudo sfdisk -A[COLOR=Red]2[/COLOR] /dev/[COLOR=RoyalBlue]sda[/COLOR]
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.
Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (not gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug;

---

