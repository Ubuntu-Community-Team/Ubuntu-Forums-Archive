---
title: "Can't login to windows 7 after installing Ubuntu 10.10...no Windows boot disk"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by cdoebbler on 2010-11-30
After I installed Ubuntu 10.10 in dual boot mode (at least so I thought) I am not able to boot into Windows 7...it does not even appear on the boot menu. Windows 7 came pre-loaded on my HP 7100 (i-7 processor) so I do not have a boot disk or other Windows recovery disk. In other words, I have to fix my boot sequence from within Ubuntu 10.10, which is the only system that now boots.

Partition record attached and bootscript below.

Can this problem be fixed from within ubuntu?

P.S. - Why does Ubuntu 10.10 indicate that you can install it dual boot, if you can not...it is a pretty bad development error no?

```
[CENTER]Boot Info Script 0.55    dated February 15th, 2010 [/CENTER]                   

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     4,194,303     4,192,256   7 HPFS/NTFS
/dev/sda2           4,196,350    94,283,775    90,087,426   f W95 Ext d (LBA)
/dev/sda5           4,196,352    60,086,283    55,889,932   7 HPFS/NTFS
/dev/sda6          60,088,320    92,760,063    32,671,744  83 Linux
/dev/sda7          92,762,112    94,283,775     1,521,664  82 Linux swap / Solaris
/dev/sda3    *     94,285,485 1,937,487,194 1,843,201,710   7 HPFS/NTFS
/dev/sda4       1,937,494,016 1,953,520,064    16,026,049   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               8,192     7,744,511     7,736,320   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CE0ABBB70ABB9AC3                       ntfs       SYSTEM                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        01CB70914703A0A0                       ntfs       OS                            
/dev/sda4        147227167226FC5C                       ntfs       HP_RECOVERY                   
/dev/sda5        8A84F82F84F81EFF                       ntfs       New Volume                    
/dev/sda6        6840df40-394b-40d6-9f7b-752819a32800   ext4                                     
/dev/sda7        2a243c02-6eb8-4651-949c-ba2c6740ef33   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sde1        3465-6137                              vfat                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sde1        /media/3465-6137         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/LXFDVD139         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


======================== sda5/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

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
search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=6840df40-394b-40d6-9f7b-752819a32800 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=6840df40-394b-40d6-9f7b-752819a32800 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 6840df40-394b-40d6-9f7b-752819a32800
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
UUID=6840df40-394b-40d6-9f7b-752819a32800 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2a243c02-6eb8-4651-949c-ba2c6740ef33 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  42.1GB: boot/grub/core.img
  44.1GB: boot/grub/grub.cfg
  31.8GB: boot/initrd.img-2.6.35-23-generic-pae
  42.1GB: boot/vmlinuz-2.6.35-23-generic-pae
  31.8GB: initrd.img
  42.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sdf sdg sdh
```

---

### Post by wilee-nilee on 2010-11-30
Can't gaurantee the return of wubi that is bcbc's area, but reloading the MS bootloader is easy, pick the link here for a recovery disc then boot to the recovery terminal and run the highlighted command after the instructions. Read carefully know what your doing if you don't stop and repost.

It also looks as if the boot flag is on the wrong partition as well should be on sda1 you can change this with gparted from a live Ubuntu cd booted in try not install. Right click the unmounted sda1 and then manage flags and click boot for sda1

Vista: [http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)

Here are the instructions and a windows 7 forum link to see the process of using and getting to the correct command console.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section.
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr

[http://www.sevenforums.com/tutorials...ot-record.html](http://www.sevenforums.com/tutorials...ot-record.html)

---

### Post by wilee-nilee on 2010-11-30
n

---

### Post by Mark Phelps on 2010-11-30
> Windows 7 came pre-loaded on my HP 7100 (i-7 processor) so I do not have a boot disk or other Windows recovery disk. 

Actually ... if you had spent five minutes looking into the Backup feature on Win7, you would have discovered that it provides the ability to create and burn a Win7 Repair CD for your machine.  You should have done that BEFORE messing around with installing another OS.

---

### Post by cdoebbler on 2010-11-30
Got Windows working by following above instructions and Ubuntu appears in dual boot grub boot menu, but when trying to boot to Ubuntu I get a message that Windows is not boot enabled?

---

