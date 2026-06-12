---
title: "Re: Unable to boot into sda2"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by adevrani on 2011-04-24
i am also facing same problem but in different manner
i was having window7 and for dual booting
i had installed ubuntu 10.10
but now there is no boot menu
it is directly going in ubuntu
it may be a wrong thread for this question......
but if someone can help me out....
(window7 partition is there only.....no formatting)



thanks in advance

---

### Post by bcbc on 2011-04-24
> **adevrani said:**
> i am also facing same problem but in different manner
i was having window7 and for dual booting
i had installed ubuntu 10.10
but now there is no boot menu
it is directly going in ubuntu
it may be a wrong thread for this question......
but if someone can help me out....
(window7 partition is there only.....no formatting)



thanks in advance
You should generally create a new thread - since this seems to be different. 
Did you install through wubi and did you modify the default boot order and set the timeout to zero (this stops windows from booting)? 
Or did you do a normal install and now it can't find windows? Do you see the grub menu at all?

---

### Post by adevrani on 2011-04-24
i am also facing same problem but in different manner
i was having window7 and for dual booting
i had installed ubuntu 10.10
but now there is no boot menu
it is directly going in ubuntu
it may be a wrong thread for this question......
but if someone can help me out....
(window7 partition is there only.....no formatting)

RESULT.TXT file is attached

thanks in advance

---

### Post by Elfy on 2011-04-24
Please do not hijack other people's threads - really please don't do it twice.

---

### Post by bcbc on 2011-04-24
It looks like Windows boot files were likely on /dev/sda1 (because it has the boot flag set) but this is now shown as swap. I can't see any other boot files for windows. Try running testdisk (to install enter: sudo apt-get install testdisk). Then see if it can recover whatever was on /dev/sda1.

I don't know what else to suggest.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for (,msdos11)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     4,016,127     4,014,080  82 Linux swap / Solaris
/dev/sda3           4,018,174   625,121,279   621,103,106   f W95 Ext d (LBA)
/dev/sda5          40,965,813   143,364,059   102,398,247   7 HPFS/NTFS
/dev/sda6         143,364,123   245,762,369   102,398,247   7 HPFS/NTFS
/dev/sda7         245,762,433   348,160,679   102,398,247   7 HPFS/NTFS
/dev/sda8         348,160,743   450,558,989   102,398,247   7 HPFS/NTFS
/dev/sda9         450,559,053   552,957,299   102,398,247   7 HPFS/NTFS
/dev/sda10        552,957,363   625,121,279    72,163,917   7 HPFS/NTFS
/dev/sda11          4,018,176    40,964,095    36,945,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       987883F67883D204                       ntfs       WINDOW 7                      
/dev/sda11       6a014237-a994-460e-8278-87db768c3d1d   ext4                                     
/dev/sda1        96df83d3-aae5-4f0d-ac33-a235bfa64bdd   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        84EC2DC6EC2DB2FA                       ntfs       Downloads                     
/dev/sda6        DA402442402427A9                       ntfs       SONGS                         
/dev/sda7        6C641CDE641CACB8                       ntfs       GARBAGE                       
/dev/sda8        8CBC141ABC1400FE                       ntfs       MOVIES                        
/dev/sda9        EC98D90298D8CC68                       ntfs       SOFTWARE                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda10       /media/WINDOW 7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


========================== sda11/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro single 
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
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=6a014237-a994-460e-8278-87db768c3d1d /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


  15.2GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.35-22-generic
   5.2GB: boot/initrd.img-2.6.35-28-generic
  15.2GB: boot/vmlinuz-2.6.35-22-generic
  15.2GB: boot/vmlinuz-2.6.35-28-generic
   5.2GB: initrd.img
   5.2GB: initrd.img.old
  15.2GB: vmlinuz
  15.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 20 00 40  a4 00 00 00 00 00 88 00  |..... .@........|
00000010  00 00 b2 00 20 10 10 20  00 00 11 0a 0c 11 00 00  |.... .. ........|
00000020  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000030  00 00 02 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000050  11 0c f2 ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  13 00 00 00 13 00 00 00  10 00 00 00 ff ff ff ff  |................|
00000090  01 00 00 00 99 00 00 00  02 00 00 00 b9 00 00 00  |................|
000000a0  03 00 00 00 d1 00 00 00  04 00 00 00 e9 00 00 00  |................|
000000b0  05 00 00 00 01 01 00 00  06 00 00 00 19 01 00 00  |................|
000000c0  07 00 00 00 31 01 00 00  08 00 00 00 49 01 00 00  |....1.......I...|
000000d0  09 00 00 00 61 01 00 00  0e 00 00 00 79 01 00 00  |....a.......y...|
000000e0  15 00 00 00 91 01 00 00  16 00 00 00 c9 01 00 00  |................|
000000f0  18 00 00 00 e1 01 00 00  19 00 00 00 f9 01 00 00  |................|
00000100  21 00 00 00 11 02 00 00  22 00 00 00 69 02 00 00  |!......."...i...|
00000110  23 00 00 00 a9 02 00 00  25 00 00 00 c1 02 00 00  |#.......%.......|
00000120  28 00 00 00 d9 02 00 00  00 00 00 00 00 00 00 00  |(...............|
00000130  03 00 00 00 00 00 00 00  19 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  53 79 6d 75 73 69 63 00  |........Symusic.|
00000150  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000160  79 fa f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |y...............|
00000170  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000180  d9 bd f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
000001a0  39 fa f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |9...............|
000001b0  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 01  |................|
000001c0  c1 ff 07 fe ff ff b7 c6  33 02 27 79 1a 06 00 fe  |........3.'y....|
000001d0  ff ff 05 fe ff ff de 3f  4e 08 66 79 1a 06 00 00  |.......?N.fy....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by adevrani on 2011-04-25
> **bcbc said:**
> It looks like Windows boot files were likely on /dev/sda1 (because it has the boot flag set) but this is now shown as swap. I can't see any other boot files for windows. Try running testdisk (to install enter: sudo apt-get install testdisk). Then see if it can recover whatever was on /dev/sda1.

I don't know what else to suggest.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for (,msdos11)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     4,016,127     4,014,080  82 Linux swap / Solaris
/dev/sda3           4,018,174   625,121,279   621,103,106   f W95 Ext d (LBA)
/dev/sda5          40,965,813   143,364,059   102,398,247   7 HPFS/NTFS
/dev/sda6         143,364,123   245,762,369   102,398,247   7 HPFS/NTFS
/dev/sda7         245,762,433   348,160,679   102,398,247   7 HPFS/NTFS
/dev/sda8         348,160,743   450,558,989   102,398,247   7 HPFS/NTFS
/dev/sda9         450,559,053   552,957,299   102,398,247   7 HPFS/NTFS
/dev/sda10        552,957,363   625,121,279    72,163,917   7 HPFS/NTFS
/dev/sda11          4,018,176    40,964,095    36,945,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       987883F67883D204                       ntfs       WINDOW 7                      
/dev/sda11       6a014237-a994-460e-8278-87db768c3d1d   ext4                                     
/dev/sda1        96df83d3-aae5-4f0d-ac33-a235bfa64bdd   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        84EC2DC6EC2DB2FA                       ntfs       Downloads                     
/dev/sda6        DA402442402427A9                       ntfs       SONGS                         
/dev/sda7        6C641CDE641CACB8                       ntfs       GARBAGE                       
/dev/sda8        8CBC141ABC1400FE                       ntfs       MOVIES                        
/dev/sda9        EC98D90298D8CC68                       ntfs       SOFTWARE                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda10       /media/WINDOW 7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


========================== sda11/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6a014237-a994-460e-8278-87db768c3d1d ro single 
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
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6a014237-a994-460e-8278-87db768c3d1d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=6a014237-a994-460e-8278-87db768c3d1d /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


  15.2GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.35-22-generic
   5.2GB: boot/initrd.img-2.6.35-28-generic
  15.2GB: boot/vmlinuz-2.6.35-22-generic
  15.2GB: boot/vmlinuz-2.6.35-28-generic
   5.2GB: initrd.img
   5.2GB: initrd.img.old
  15.2GB: vmlinuz
  15.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 20 00 40  a4 00 00 00 00 00 88 00  |..... .@........|
00000010  00 00 b2 00 20 10 10 20  00 00 11 0a 0c 11 00 00  |.... .. ........|
00000020  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000030  00 00 02 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000050  11 0c f2 ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  13 00 00 00 13 00 00 00  10 00 00 00 ff ff ff ff  |................|
00000090  01 00 00 00 99 00 00 00  02 00 00 00 b9 00 00 00  |................|
000000a0  03 00 00 00 d1 00 00 00  04 00 00 00 e9 00 00 00  |................|
000000b0  05 00 00 00 01 01 00 00  06 00 00 00 19 01 00 00  |................|
000000c0  07 00 00 00 31 01 00 00  08 00 00 00 49 01 00 00  |....1.......I...|
000000d0  09 00 00 00 61 01 00 00  0e 00 00 00 79 01 00 00  |....a.......y...|
000000e0  15 00 00 00 91 01 00 00  16 00 00 00 c9 01 00 00  |................|
000000f0  18 00 00 00 e1 01 00 00  19 00 00 00 f9 01 00 00  |................|
00000100  21 00 00 00 11 02 00 00  22 00 00 00 69 02 00 00  |!......."...i...|
00000110  23 00 00 00 a9 02 00 00  25 00 00 00 c1 02 00 00  |#.......%.......|
00000120  28 00 00 00 d9 02 00 00  00 00 00 00 00 00 00 00  |(...............|
00000130  03 00 00 00 00 00 00 00  19 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  53 79 6d 75 73 69 63 00  |........Symusic.|
00000150  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000160  79 fa f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |y...............|
00000170  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
00000180  d9 bd f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |................|
000001a0  39 fa f1 ff 00 00 00 00  00 00 00 00 00 00 00 00  |9...............|
000001b0  00 00 00 00 00 00 00 00  03 00 00 00 00 00 00 01  |................|
000001c0  c1 ff 07 fe ff ff b7 c6  33 02 27 79 1a 06 00 fe  |........3.'y....|
000001d0  ff ff 05 fe ff ff de 3f  4e 08 66 79 1a 06 00 00  |.......?N.fy....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
actually earlier there were 3 os.
window7, xp & ubuntu10.04( installed in xp as a programme)
3 were working fine
but due to less memory of ubuntu partition i had
formatted xp & ubuntu partition
and made 2gb for swab and remaining for ubuntu10.10

this is my "sudo fdisk -l" report
please help me....

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         250     2007040   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda3             251       38912   310551553    f  W95 Ext'd (LBA)
/dev/sda5            2551        8924    51199123+   7  HPFS/NTFS
/dev/sda6            8925       15298    51199123+   7  HPFS/NTFS
/dev/sda7           15299       21672    51199123+   7  HPFS/NTFS
/dev/sda8           21673       28046    51199123+   7  HPFS/NTFS
/dev/sda9           28047       34420    51199123+   7  HPFS/NTFS
/dev/sda10          34421       38912    36081958+   7  HPFS/NTFS
/dev/sda11            251        2550    18472960   83  Linux

Partition table entries are not in disk order

---

### Post by adevrani on 2011-04-25
> **forestpiskie said:**
> Please do not hijack other people's threads - really please don't do it twice.
is this for me?
as a new member and 1st post
i don't know the rules
please tell me

---

### Post by adevrani on 2011-04-25
> **bcbc said:**
> You should generally create a new thread - since this seems to be different. 
Did you install through wubi and did you modify the default boot order and set the timeout to zero (this stops windows from booting)? 
Or did you do a normal install and now it can't find windows? Do you see the grub menu at all?
i had installed it through live cd
earlier i had installed ubuntu10.04 throgh xp as a software
and had a boot choice like this
1.OLDER VERSION OF WINDOWS(for ubuntu i had to enter here)
2.WINDOW7
3.UBUNTU(this was not working)

after selecting 1st agn 2 option
1.xp
2.ubuntu

i had formatted both ubuntu an xp patition through live cd
and made some space for swap and ubuntu

---

### Post by bcbc on 2011-04-25
> **adevrani said:**
> i had installed it through live cd
earlier i had installed ubuntu10.04 throgh xp as a software
and had a boot choice like this
1.OLDER VERSION OF WINDOWS(for ubuntu i had to enter here)
2.WINDOW7
3.UBUNTU(this was not working)

after selecting 1st agn 2 option
1.xp
2.ubuntu

i had formatted both ubuntu an xp patition through live cd
and made some space for swap and ubuntu
The problem is this: when you install Windows 7 AFTER you already have Windows XP installed, Windows 7 places it's boot files on the XP partition. This is standard Windows functionality and has nothing to do with Ubuntu. See [here]("http://www.multibooters.co.uk/system.html") or [here]("http://www.multibooters.co.uk/multiboot.html")

When you formatted the XP partition, you would have removed the Windows 7 boot files as well as XP.

So... how do you fix this? You will need to run a Windows 7 repair (using a repair CD or the original installation DVD). I'll try and find a link for this.

Edit: try this [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

PS you might get better help in a Windows forum for this.

---

