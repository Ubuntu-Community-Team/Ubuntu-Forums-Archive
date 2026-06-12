---
title: "Problems going from grub to grub2"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by DannyJohansson on 2010-06-05
i tried to upgrade from grub to grub2.  part of the way thru, i got nervous and tried to cancel out of it at (what i thought was) a safe point, but alas, it was apparently not safe.

so the process went like this.  i started the upgrade and told me to reboot.  when i rebooted, it gave me the "chain-load" message which was great and it seemed like it was working.  so i then did the "upgrade-from-grub-legacy", and this is where i got scared and tried to quit.  instead of stopping the process, it completed without actually writing _something important_ to the various drives.

here is the boot_info_script output.  any help is much appreciated!



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 914259213.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdh1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdh1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   914,259,149   914,259,087   7 HPFS/NTFS
/dev/sda2         914,259,150   976,768,064    62,508,915   5 Extended
/dev/sda5         914,259,213   971,595,134    57,335,922   b W95 FAT32
/dev/sda6         971,595,198   976,768,064     5,172,867  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   144,215,504   144,215,442   7 HPFS/NTFS
/dev/sdb2         144,215,505   286,888,769   142,673,265  83 Linux
/dev/sdb3         286,888,770   293,041,664     6,152,895   5 Extended
/dev/sdb5         286,888,833   293,041,664     6,152,832  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1024 MB, 1024966656 bytes
32 heads, 62 sectors/track, 1009 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             62     2,001,855     2,001,794   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9C8237218236FF78                       ntfs       EasternAvenue                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        479E-6395                              vfat       SEWALLSTREE                   
/dev/sda6        e155d296-269b-496f-a0b4-1f862f8eb139   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F890F32A90F2EDCE                       ntfs       CoburnStreet                  
/dev/sdb2        37e7e50e-f011-4a77-8a99-f04b7f636512   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        289e31e3-815b-4c9c-81ca-be2bc99ff56a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D4E8F74AE8F7297E                       ntfs       EssexStreet                   
/dev/sdc: PTTYPE="dos" 
/dev/sdh1        17DD-3AAF                              vfat                                     
/dev/sdh: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdh1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/37e7e50e-f011-4a77-8a99-f04b7f636512 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37e7e50e-f011-4a77-8a99-f04b7f636512

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

title		Chainload into GRUB 2
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	echo	'Loading Linux 2.6.28-15-generic ...'
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 37e7e50e-f011-4a77-8a99-f04b7f636512
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f890f32a90f2edce
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e155d296-269b-496f-a0b4-1f862f8eb139 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=289e31e3-815b-4c9c-81ca-be2bc99ff56a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  74.0GB: boot/grub/core.img
  75.2GB: boot/grub/grub.cfg
  80.5GB: boot/grub/menu.lst
  74.0GB: boot/initrd.img-2.6.28-15-generic
  82.9GB: boot/initrd.img-2.6.31-20-generic
  87.3GB: boot/initrd.img-2.6.32-21-generic
  84.3GB: boot/initrd.img-2.6.32-22-generic
  78.1GB: boot/vmlinuz-2.6.28-15-generic
  83.2GB: boot/vmlinuz-2.6.31-20-generic
  82.8GB: boot/vmlinuz-2.6.32-21-generic
  84.3GB: boot/vmlinuz-2.6.32-22-generic
  84.3GB: initrd.img
  87.3GB: initrd.img.old
  84.3GB: vmlinuz
  82.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by oldfred on 2010-06-05
The script shows grub legacy still in the MBR. I do not see any reason why it should not boot. Have you tried both sda & sdb (they both look the same).

But I do not know what the upgrade to grub2 does beside install the grub2 boot loader to the MBR.

Do you want to install grub2 to the MBR or reinstall grub legacy. Not sure which or if either works since you stopped half way thru. 

You may have to chroot into your system and totally uninstall both and totally reinstall grub or grub2. The upgrade is designed to work but mixed grub & grub2 often has problems.

---

### Post by DannyJohansson on 2010-06-05
at this point, i don't really care if i revert or go to grub2.  i guess eventually i'd like to get to grub2, isn't v2 always better than v1?  :biggrin:

oh and i forgot to mention when i reboot i get an error 15.

i'll chroot if you tell me to, but i'll require lots of hand-holding.

---

### Post by qwerty2009 on 2010-06-05
you could use the live cd to mount your drive and install grub that way.

> sudo -i
mount /dev/sda* /mnt
mount /dev/sda* /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub

"*" being the mount number

---

### Post by oldfred on 2010-06-05
qwerty2009 instructions are ok just I will give you your drive & partition based on boot script, not sure if from liveCD you need sudo -i

Install from LiveCD:
Find linux partition  should be sdb2 but just to check.
```
sudo fdisk -l
sudo mkdir /mnt/sdb2
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

```
Make sure you set BIOS or (test with one time boot key) to boot from sdb. (150GB drive)

---

### Post by DannyJohansson on 2010-06-15
Thanks Oldfred, i had to think a bit, but i eventually did get this to work.  when I entered your commands, it still didn't boot, but i realized that was because ubuntu 10.04 has grub2;  so after booting from flashdrive, i uninstalled grub2 and marked old grub for installation.  I then entered your commands again and voila, it worked.

after this, i was able to complete the update from old grub to new grub by just following the commands (which I of course should have done the first time).

All in all a success.  thanks very much.

---

