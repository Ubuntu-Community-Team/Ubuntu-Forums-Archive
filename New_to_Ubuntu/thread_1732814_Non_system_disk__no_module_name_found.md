---
title: "Non system disk / no module name found"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by worlestone on 2011-04-18
I have been running lubuntu and XP on a Compaq nc6320 for the last few weeks.

A couple of days ago I could not see XP in the boot menu, so with help ran the following

sudo apt-get install os-prober
sudo update-grub

This reincluded XP in the boot list.

XP ran this morning, but this evening I'm getting the following message and not able to boot up the PC - only with a live CD...

Non system disk or disk error
replace and strike any key when ready

if I do this, then get the following message...

no module name found
Aborted. Press any key to exit

this then returns to " Non system disk..." and so on

help!

Thanks

---

### Post by Leppie on 2011-04-18
are you able to boot into the live environment?

---

### Post by worlestone on 2011-04-18
Yes, I can boot a live CD, using xubuntu now

---

### Post by Leppie on 2011-04-18
could you download and run the boot info script and post the generated results.txt: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Draggem on 2011-04-18
i have the same issue last 3 months but i fixed it by just redoing(removing then putting the disk back)the system disk..

hope it works!!

---

### Post by worlestone on 2011-04-18
The result is:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   148,104,428   148,104,366   7 HPFS/NTFS
/dev/sda2    *    211,740,480   234,435,599    22,695,120   c W95 FAT32 (LBA)
/dev/sda3         148,105,214   211,738,623    63,633,410   5 Extended
/dev/sda5         148,105,216   209,027,071    60,921,856  83 Linux
/dev/sda6         209,029,120   211,738,623     2,709,504  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2503235E05308670                       ntfs                                     
/dev/sda2        6AC8-572D                              vfat       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        be0c3db4-c4ab-4df5-a355-c9832a41633a   ext4                                     
/dev/sda6        3730adca-409d-49e4-9b96-981531e1c3b3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect




================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\wubildr.mbr = "Ubuntu"


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
search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=be0c3db4-c4ab-4df5-a355-c9832a41633a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=be0c3db4-c4ab-4df5-a355-c9832a41633a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=be0c3db4-c4ab-4df5-a355-c9832a41633a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=be0c3db4-c4ab-4df5-a355-c9832a41633a ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be0c3db4-c4ab-4df5-a355-c9832a41633a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2503235e05308670
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 6ac8-572d
	drivemap -s (hd0) ${root}
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
UUID=be0c3db4-c4ab-4df5-a355-c9832a41633a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3730adca-409d-49e4-9b96-981531e1c3b3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.2GB: boot/grub/core.img
  97.6GB: boot/grub/grub.cfg
 101.8GB: boot/initrd.img-2.6.35-22-generic
 102.0GB: boot/initrd.img-2.6.35-28-generic
  80.3GB: boot/vmlinuz-2.6.35-22-generic
  80.4GB: boot/vmlinuz-2.6.35-28-generic
 102.0GB: initrd.img
 101.8GB: initrd.img.old
  80.4GB: vmlinuz
  80.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  b5 ae 2b 5d d7 b8 39 de  bb 3b 3a d0 c4 83 52 ff  |..+]..9..;:...R.|
00000010  66 9b ed 8a 3e 1d ed f2  2f 32 bc b2 ba 85 1d 54  |f...>.../2.....T|
00000020  a6 e6 9a 2b ee a3 96 cd  1d f4 1d c4 bc 1f 03 d1  |...+............|
00000030  3e fb 7e 0c 54 6a fc 7e  0c 44 4e 46 d7 f4 d1 75  |>.~.Tj.~.DNF...u|
00000040  ea 84 66 e8 4a bd ed 74  9d 01 3c 6e 46 d7 39 eb  |..f.J..t..<nF.9.|
00000050  0c 44 43 f9 89 e2 92 66  eb c9 fa c1 e5 e9 de 76  |.DC....f.......v|
00000060  cc 48 56 15 c3 48 56 97  d5 b0 f3 b0 22 f3 df 45  |.HV..HV....."..E|
00000070  24 ab c6 3e 59 a5 9e 0b  27 a5 d2 65 b3 f3 a0 3f  |$..>Y...'..e...?|
00000080  5c 0f 8d a6 ee 0b 17 9d  9d b2 75 50 65 5c f9 19  |\.........uPe\..|
00000090  46 bb fc 91 ec d4 e4 be  a3 80 55 65 7e a4 6a 22  |F.........Ue~.j"|
000000a0  95 45 c0 aa 66 48 4d 21  52 a7 ee e7 6b 01 2b 76  |.E..fHM!R...k.+v|
000000b0  b4 51 3b 05 e2 6c 33 a4  ce 6b a7 80 35 94 8f 14  |.Q;..l3..k..5...|
000000c0  c7 7e e5 fe d0 0a ee 91  d7 29 db 6e c4 dc 0f af  |.~.......).n....|
000000d0  cf 43 a1 12 55 9c b7 40  af ad d0 95 f5 18 ab f3  |.C..U..@........|
000000e0  e9 5a 9b 7f a9 51 fc 92  f8 84 68 4b 84 27 f6 82  |.Z...Q....hK.'..|
000000f0  e1 41 2e 46 f7 0c 6c eb  fe c4 ba f1 2c bf 5d 41  |.A.F..l.....,.]A|
00000100  4d ab 88 5c 2a 73 6d f5  ed 3b d3 0f 8d 3e 65 6d  |M..\*sm..;...>em|
00000110  75 e6 51 b2 79 b8 bf 67  f3 65 f2 f8 b3 a7 0b 1b  |u.Q.y..g.e......|
00000120  5e ff c5 9e ae b1 a2 ea  73 9f ed e4 e1 7f 0f 0f  |^.......s.......|
00000130  57 4c d1 c3 65 e0 97 ff  4b 3d 5b 69 01 cf 76 6d  |WL..e...K=[i..vm|
00000140  75 0b 35 fa e4 97 6c f1  5f d6 56 3b 5d fc e3 e0  |u.5...l._.V;]...|
00000150  ff 03 50 4b 01 02 14 03  14 00 00 00 08 00 52 a2  |..PK..........R.|
00000160  51 3e 85 5e 56 3f 42 2b  00 00 91 f7 01 00 07 00  |Q>.^V?B+........|
00000170  00 00 00 00 00 00 00 00  00 00 80 01 00 00 00 00  |................|
00000180  64 6f 63 2e 6b 6d 6c 50  4b 05 06 00 00 00 00 01  |doc.kmlPK.......|
00000190  00 01 00 35 00 00 00 67  2b 00 00 00 00 00 e1 94  |...5...g+.......|
000001a0  05 af 79 17 00 4d 07 db  00 08 07 08 2f 28 2d 10  |..y..M....../(-.|
000001b0  20 74 21 15 00 00 00 82  0a 8c 21 60 00 73 00 fe  | t!.......!`.s..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 a1 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  a1 03 00 60 29 00 00 00  |...........`)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Leppie on 2011-04-18
issue the following commands in a terminal:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

then reboot, grub should load properly now.

---

### Post by worlestone on 2011-04-18
Thanks, this worked and I was able to see all installed OS on boot and access XP, great stuff, but when I shut windows down to boot back into xubuntu the error message was back!:(

Any ideas?

---

### Post by Leppie on 2011-04-18
this is a known problem, you may want to have a read through this page: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

