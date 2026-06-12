---
title: "Newbie problem after installation"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by jerrard on 2010-12-26
Hi forum,
 
First of all, merry xmas to you all!
 
So, i am sick and tired of windows. I had a version of ubuntu on an ASUS EEEPC and thought i would like that on my desktop.
 
I tried the test version from the cd i burnt. all was good except i couldn't get VLC to play anything but i figure i can fix that later.
 
I tried installing the latest version 10.10 [not in the test/live mode] and all went well. I clicked the options to download updates and 3rd party software and the 'erase and use the entire disc' option, then chose the HDD i wanted [i have 3].
 
everything went well etc etc and i thought i was in the clear.
 
now the problem-after the reboot/restart, i get my motherboard splash screen and then nothing. a black screen with a blinking cursor.
 
help please!
 
so, what have i done so far:
-tried installing it many times from the boot cd. when i try and do this from the live version it doesnt like it.
-checked disk for defects
-checked memory etc.
-shouted at it.
-read the forums
 
what should i do? is this a boot problem? i am pretty sure the iso i burnt was good. 
 
please help me forum, your my only hope!
 
Athlon 64X2 2710mhz
2gid ram
Amdk8 imc chipset 
3 hdd, 320gig, 120gig, 200gig
 
everything was running ok on windows xp dar edition. well, running ok is subjective when it comes to windows.....

---

### Post by wilee-nilee on 2010-12-26
Hit the power button then hold down the shift key immediately. If you see the grub menu hit e for edit then navigate with the arrow keys to quite splash and put nomodeset in front of it with a normal space in between. hold down crtl and hit x to boot. This is safe graphics per-session look for the graphics driver.

---

### Post by jerrard on 2010-12-26
Hi Wilee-nilee,
 
Many thanks for the quick reply. 
 
I saw a similar thing posted before. I tried this and nothing happened. It went from start up to splash screen to black screen of blinking cursor.
 
does this mean i have no grub menu?
 
Thanks again!

---

### Post by wilee-nilee on 2010-12-26
> **jerrard said:**
> Hi Wilee-nilee,
 
Many thanks for the quick reply. 
 
I saw a similar thing posted before. I tried this and nothing happened. It went from start up to splash screen to black screen of blinking cursor.
 
does this mean i have no grub menu?
 
Thanks again!

Easiest way for us to tell what's go on is by running the bootscript in my signature with a live cd/thumb.

Just post the generated script in code tags by opening the reply click on the # in the reply panel and paste all the text from the generated file between the code tags.

While on the live cd run this command in the terminal and post it as well. It identifies the graphic card set up.
lspci | grep VGA

---

### Post by jerrard on 2010-12-26
wow, that was a step learning curve!
OK, i am sorry about the volume of the info but i didn't understand what you wanted. i will post the graphic driver info when i figure out how to do it:

again, sorry about the volume....

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   330,933,548   330,933,486   7 HPFS/NTFS
/dev/sda2         330,934,270   390,721,535    59,787,266   5 Extended
/dev/sda5         330,934,272   388,163,583    57,229,312  83 Linux
/dev/sda6         388,165,632   390,721,535     2,555,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   230,277,119   230,275,072  83 Linux
/dev/sdb2         230,279,166   240,119,807     9,840,642   5 Extended
/dev/sdb5         230,279,168   240,119,807     9,840,640  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        262443C224439429                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        179e6ba6-c40e-43f6-937f-6db190ab099b   ext4                                     
/dev/sda6        d522568b-46b0-4f59-b488-107a712907f1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        005f3e2a-dcd7-4953-ab12-3e8a4c54e551   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5                                               swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D818D3C218D39E36                       ntfs       Shared                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=179e6ba6-c40e-43f6-937f-6db190ab099b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=179e6ba6-c40e-43f6-937f-6db190ab099b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 242c84be2c848d0c
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
UUID=179e6ba6-c40e-43f6-937f-6db190ab099b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d522568b-46b0-4f59-b488-107a712907f1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 195.3GB: boot/grub/core.img
 184.7GB: boot/grub/grub.cfg
 187.4GB: boot/initrd.img-2.6.35-22-generic
 195.3GB: boot/vmlinuz-2.6.35-22-generic
 187.4GB: initrd.img
 195.3GB: vmlinuz

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
search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=005f3e2a-dcd7-4953-ab12-3e8a4c54e551 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=005f3e2a-dcd7-4953-ab12-3e8a4c54e551 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 005f3e2a-dcd7-4953-ab12-3e8a4c54e551
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=179e6ba6-c40e-43f6-937f-6db190ab099b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 179e6ba6-c40e-43f6-937f-6db190ab099b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=179e6ba6-c40e-43f6-937f-6db190ab099b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
UUID=005f3e2a-dcd7-4953-ab12-3e8a4c54e551 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  32.3GB: boot/grub/core.img
 111.8GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  32.3GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  32.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  17 7f d5 96 9b ab de 16  53 e3 c4 24 be ca 40 ff  |........S..$..@.|
00000010  4d cb 67 2f 44 c6 36 c0  e6 d0 45 98 82 ce 38 8f  |M.g/D.6...E...8.|
00000020  c4 de aa 19 9f 6d 61 b3  52 ff a4 9c 44 f4 34 98  |.....ma.R...D.4.|
00000030  84 4b 12 e8 f8 48 54 aa  17 77 1b 6e 2f df cb bf  |.K...HT..w.n/...|
00000040  e7 79 d5 d6 22 4e 2f 03  ff 4b 07 20 59 37 14 49  |.y.."N/..K. Y7.I|
00000050  09 5e 60 4e c0 f5 9d 2f  63 7f fb a1 e9 b3 a5 24  |.^`N.../c......$|
00000060  1c 70 3f aa 31 65 fa 46  80 8e d4 a3 51 e8 1c f8  |.p?.1e.F....Q...|
00000070  8e ae 0f 47 4d aa fb 4c  ce 96 f5 bc cd f5 59 1e  |...GM..L......Y.|
00000080  59 da 88 56 08 60 f4 40  81 e5 e6 92 c5 83 27 86  |Y..V.`.@......'.|
00000090  65 b5 40 1d 9a a9 36 c6  47 7b 38 5a dc 0e 9a 41  |e.@...6.G{8Z...A|
000000a0  c8 8a 75 11 02 06 d9 2d  b7 6a 3a 6f a4 70 92 da  |..u....-.j:o.p..|
000000b0  05 93 67 50 9d ce 11 ea  2a 45 f4 ff 74 ae bb 30  |..gP....*E..t..0|
000000c0  e8 7f 2a 2a 3f f3 bd 3c  45 c9 0c a3 4c a5 7b 79  |..**?..<E...L.{y|
000000d0  c7 02 16 9c 09 fd 98 8c  2b 5a c8 dd 51 6f 1c a0  |........+Z..Qo..|
000000e0  13 0e 32 2d 9b 7a 2a 08  9e 2b 07 1b 64 dd 84 a8  |..2-.z*..+..d...|
000000f0  86 6e f1 f7 d5 74 73 54  e8 2d 8a 1f 81 e6 e0 f4  |.n...tsT.-......|
00000100  7f 8a a6 56 1a cb 17 ec  bd bd 82 b8 8a 00 35 21  |...V..........5!|
00000110  c5 2e 5a 45 2e 03 e2 ed  b3 e6 35 75 b3 6c 17 80  |..ZE......5u.l..|
00000120  84 fd dc ee 71 63 c0 fc  25 b7 a0 fc db fb b7 ca  |....qc..%.......|
00000130  2f 57 96 a0 14 08 80 30  76 d4 1e b5 64 47 57 a0  |/W.....0v...dGW.|
00000140  94 85 d2 7e 0a 00 96 0c  55 2d 7c 42 24 b1 48 9d  |...~....U-|B$.H.|
00000150  8b 1e 83 fd 8a 12 e1 02  05 6c 7f b0 71 6a c1 b7  |.........l..qj..|
00000160  ee 0b 8e ce 0a d7 b7 85  7b 7a 1a d3 e3 c1 00 97  |........{z......|
00000170  29 aa 01 73 57 6b 99 d3  cf 35 91 5e 7c 40 0c 03  |)..sWk...5.^|@..|
00000180  30 97 f4 0a 49 d4 12 06  27 f5 e9 e5 c2 4d 6f 93  |0...I...'....Mo.|
00000190  79 1e 20 50 5b 2f a6 11  c7 65 23 6b 95 15 5c e0  |y. P[/...e#k..\.|
000001a0  fc 66 20 3e 60 55 17 72  42 25 6f 06 db 5c 09 6c  |.f >`U.rB%o..\.l|
000001b0  e0 28 43 ae 16 2d 94 84  5d ab 74 87 c4 1e 00 fe  |.(C..-..].t.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 40 69 03 00 fe  |...........@i...|
000001d0  ff ff 05 fe ff ff 02 40  69 03 00 08 27 00 00 00  |.......@i...'...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  00 e5 3e c0 a8 01 44 45  7f 11 00 20 81 9a b7 e5  |..>...DE... ....|
00000010  62 09 07 01 04 02 04 02  01 01 41 42 bb c0 f0 97  |b.........AB....|
00000020  b4 26 01 63 26 05 d0 4f  0b c0 a8 01 44 45 7f 11  |.&.c&..O....DE..|
00000030  00 21 81 9a b7 e5 61 09  07 01 04 02 04 03 01 01  |.!....a.........|
00000040  41 42 bb c0 f0 97 b4 26  01 c0 a8 01 44 45 7f 5d  |AB.....&....DE.]|
00000050  76 db 07 00 b1 5b 11 00  20 81 9a b7 e5 60 09 07  |v....[.. ....`..|
00000060  01 04 02 04 02 01 01 41  42 bb c0 f0 97 b4 26 01  |.......AB.....&.|
00000070  5e 03 2d 0e 0a cf c0 a8  01 44 45 7f 06 00 21 81  |^.-......DE...!.|
00000080  9a b7 e5 5f 09 07 01 04  02 04 03 01 01 41 42 bb  |..._.........AB.|
00000090  c0 f0 97 b4 26 01 c0 a8  01 44 45 7f 55 f7 1d c8  |....&....DE.U...|
000000a0  00 e5 3e 11 00 21 81 9a  b7 e5 5e 09 07 01 04 03  |..>..!....^.....|
000000b0  04 02 01 01 41 42 bb c0  f0 97 b4 26 01 55 f7 1d  |....AB.....&.U..|
000000c0  c8 00 e5 3e c0 a8 01 44  45 7f 11 00 21 81 9a b7  |...>...DE...!...|
000000d0  e5 5d 09 07 01 04 02 04  03 01 01 41 42 bb c0 f0  |.].........AB...|
000000e0  97 b4 26 01 c0 a8 01 44  45 7f 55 f7 1d c8 00 e5  |..&....DE.U.....|
000000f0  3e 11 00 21 81 9a b7 e5  5c 09 07 01 04 03 04 02  |>..!....\.......|
00000100  01 01 41 42 bb c0 f0 97  b4 26 01 55 f7 1d c8 00  |..AB.....&.U....|
00000110  e5 3e c0 a8 01 44 45 7f  11 00 20 81 9a b7 e5 5b  |.>...DE... ....[|
00000120  09 07 01 04 02 04 02 01  01 41 42 bb c0 f0 97 b4  |.........AB.....|
00000130  26 01 c0 a8 01 44 45 7f  63 26 05 d0 4f 0b 11 00  |&....DE.c&..O...|
00000140  20 81 9a b7 e5 5a 09 07  01 04 02 04 02 01 01 41  | ....Z.........A|
00000150  42 bb c0 f0 97 b4 26 01  c0 a8 01 44 45 7f 4e 90  |B.....&....DE.N.|
00000160  d9 89 64 48 11 00 20 81  9a b7 e5 59 09 07 01 04  |..dH.. ....Y....|
00000170  02 04 02 01 01 41 42 bb  c0 f0 97 b4 26 01 63 26  |.....AB.....&.c&|
00000180  05 d0 4f 0b c0 a8 01 44  45 7f 11 00 21 81 9a b7  |..O....DE...!...|
00000190  e5 58 09 07 01 04 02 04  03 01 01 41 42 bb c0 f0  |.X.........AB...|
000001a0  97 b4 26 01 c0 a8 01 44  45 7f 5f 6b d4 7a 00 c1  |..&....DE._k.z..|
000001b0  0d 11 00 20 81 9a b7 e5  57 09 07 01 04 02 00 fe  |... ....W.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 96 00 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by jerrard on 2010-12-26
well, that was easier!
0:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)

---

### Post by wilee-nilee on 2010-12-26
Okay so I think the sdb1 is the install if this correct put it first to be read in the bios then boot the live cd of the same Ubuntu and run these two commands in the terminal.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

You have 10.10 in sda5 as well sdb1 which one is the one you want.

If sdb is correct, after running those commands boot to the Ubuntu install and run sudo update-grub. 

If your install is in sda5 then the commands letters and numbers would be different like this see the command are basically the same. the key part is having the HD first in the bios that grub, and Ubuntu is installed to.
```
sudo mount /dev/sda5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by jerrard on 2010-12-26
Hi,
 
I tried this and still no joy. The first two lines of code seemed to work but the update-grub didn't.I have been fiddling and reading and still finding the command line stuff quite baffling.
 
I dont now how i ended up with what appears to be two installations on my hard drive. I figured the best option would be to delete [the entire drive] and reinstal the entire thing [again] from the liveCD.
 
Its currently reinstalling and i will post the details of the bootscipt [with the correct code thing] if i have no joy.
 
one time, after i restarted my comp. it looked as if it loaded up correctly. however, i had the cd in the drive and it booted up from there but missed out the usual option of trying or installing the OS. ?? i dont now what that was all about but i checed my bios boot setting and it all looks normal.
 
I am just having a problem with 'grub' booting up incorrectly or is it something else?
 
many thanks,
 
Jerrard

---

### Post by jerrard on 2010-12-26
after the installion is complete and the cd has been ejected i get lots of lines of code that fills my screen. they are all fairly similar and say something like:
 
[ 1857.122328] end_request: I/0 error, dev sr0, sector 535528 
 
when i close the drive and touch any key i get a message lie 'will now restart'
 
is this normal?
 
thanks!

---

### Post by wilee-nilee on 2010-12-26
> **jerrard said:**
> Hi,
 
I tried this and still no joy. The first two lines of code seemed to work but the update-grub didn't.I have been fiddling and reading and still finding the command line stuff quite baffling.
 
I dont now how i ended up with what appears to be two installations on my hard drive. I figured the best option would be to delete [the entire drive] and reinstal the entire thing [again] from the liveCD.
 
Its currently reinstalling and i will post the details of the bootscipt [with the correct code thing] if i have no joy.
 
one time, after i restarted my comp. it looked as if it loaded up correctly. however, i had the cd in the drive and it booted up from there but missed out the usual option of trying or installing the OS. ?? i dont now what that was all about but i checed my bios boot setting and it all looks normal.
 
I am just having a problem with 'grub' booting up incorrectly or is it something else?
 
many thanks,
 
Jerrard

You don't have to reinstall anything, although it seems you have started. Really it is identifying the install you want and removing the extra and making sure that that hd where it is installed is the first read in the mbr. If you just start stuff rather then wait for help it makes things much more difficult.

---

### Post by jerrard on 2010-12-26
EH?
 
it now looks like it works! after the reinstal, it booted up perfect and again after a restart. I have no idea why this happed but i am very happy.
 
Could you please explain what was different this time? 
 
many thanks for you time and help!
 
Jerrard

---

### Post by wilee-nilee on 2010-12-26
> **jerrard said:**
> EH?
 
it now looks like it works! after the reinstal, it booted up perfect and again after a restart. I have no idea why this happed but i am very happy.
 
Could you please explain what was different this time? 
 
many thanks for you time and help!
 
Jerrard

If you post the bootscript again possibly but if it works, this may be a time for you to figure it out.

---

### Post by jerrard on 2011-01-01
Hi Wilie-Nilie,

Thank you for all your help and please excuse the fact that i get frustrated when i cant make things work.

I have been using Ubuntu for a number of days and really like it. I know i am far from utilising its potential but that will come with time.

Again, Many thanks and happy New Year.

J

---

