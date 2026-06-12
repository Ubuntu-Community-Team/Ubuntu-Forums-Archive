---
title: "GRUB error: No such device"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by DMzda on 2010-07-08
I installed ubuntu, and when booting, I get " error: no such device: ", with a long number after. This leaves me at the grub rescue prompt.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065    74,316,689    74,300,625   f W95 Ext d (LBA)
/dev/sda5              16,128    74,316,689    74,300,562   7 HPFS/NTFS
/dev/sda2    *     74,316,690   156,232,124    81,915,435   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046    82,042,879    82,040,834   5 Extended
/dev/sdb5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdb6           3,907,584    82,042,879    78,135,296  83 Linux
/dev/sdb3          82,043,955   312,576,704   230,532,750   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        0404798604797B8C                       ntfs       Data                          
/dev/sda5        049C8B639C8B4E5C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb3        482EF04F5AAA4783                       ntfs                                     
/dev/sdb5        af56cbd1-0211-4a53-ad86-a88dcc3878df   swap                                     
/dev/sdb6        96f4a506-d290-4644-9799-fb567e94b736   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/96f4a506-d290-4644-9799-fb567e94b736 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=96f4a506-d290-4644-9799-fb567e94b736 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=96f4a506-d290-4644-9799-fb567e94b736 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 96f4a506-d290-4644-9799-fb567e94b736
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0404798604797b8c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=96f4a506-d290-4644-9799-fb567e94b736 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af56cbd1-0211-4a53-ad86-a88dcc3878df none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/core.img
  12.9GB: boot/grub/grub.cfg
   4.3GB: boot/initrd.img-2.6.32-21-generic
   4.2GB: boot/vmlinuz-2.6.32-21-generic
   4.3GB: initrd.img
   4.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  b8 ab ea ec 13 cb cf e2  b4 d8 5f 07 c4 cc 42 ef  |.........._...B.|
00000010  39 64 47 f0 00 b3 72 f3  8f 32 24 5a cc 58 50 1a  |9dG...r..2$Z.XP.|
00000020  a6 99 af 16 e6 45 05 72  f1 11 67 0a 63 30 fe db  |.....E.r..g.c0..|
00000030  e8 4d 87 94 57 45 a8 45  fb eb b0 bf 53 b8 87 76  |.M..WE.E....S..v|
00000040  a6 d4 a2 6d 15 ec b0 c7  ef 1f 65 a9 e2 9b 16 37  |...m......e....7|
00000050  67 5b 72 8d 0c 04 c3 f1  bf 95 cd 3f 70 06 0b 64  |g[r........?p..d|
00000060  3b 54 e1 90 db 5d 0c f2  b4 98 8d bf 68 0d 0c 71  |;T...]......h..q|
00000070  26 25 28 0b 29 c4 0c 4b  0a 2e 96 13 38 a2 cc 02  |&%(.)..K....8...|
00000080  78 6d a2 9d f3 69 4a 33  0e 80 ad 96 d1 a2 07 43  |xm...iJ3.......C|
00000090  6e f8 39 59 0d 2e 8e 96  d5 b3 bd d6 2e 48 6f 52  |n.9Y.........HoR|
000000a0  e9 ba 88 55 32 f3 ff 4f  71 69 99 76 30 47 31 89  |...U2..Oqi.v0G1.|
000000b0  19 c0 e8 68 65 78 b7 8a  62 80 ae 9b d3 8c 85 72  |...hex..b......r|
000000c0  5c b9 4e b1 e9 92 2e 33  d0 bb bf 96 1c d3 10 d4  |\.N....3........|
000000d0  0f 8b 7e de 00 e3 84 72  2a ca 26 b2 a7 7d 26 3e  |..~....r*.&..}&>|
000000e0  ca 3f 77 79 e5 9d 01 61  f4 90 75 86 13 bd b3 59  |.?wy...a..u....Y|
000000f0  66 17 33 2f 2a 0b ea 79  9f 7a 8b e7 40 62 ce e9  |f.3/*..y.z..@b..|
00000100  be d4 02 06 f9 a3 ab 78  bc 91 14 d8 23 1a 37 7a  |.......x....#.7z|
00000110  85 62 15 70 ab 42 ba 09  93 07 7e a6 0d a9 ec 2e  |.b.p.B....~.....|
00000120  1a 32 7f 35 a0 17 2d af  92 46 43 7c a3 9c 16 c8  |.2.5..-..FC|....|
00000130  37 e4 de 19 90 95 fc 73  f7 7b 9f b0 49 b3 ae 7c  |7......s.{..I..||
00000140  18 00 33 6b c8 01 dd 00  5f f5 f1 d2 70 db b4 a2  |..3k...._...p...|
00000150  25 e5 b3 f0 7f 5d d8 2c  a3 97 42 68 29 d9 d8 37  |%....].,..Bh)..7|
00000160  f9 46 da 35 3e f6 e1 2d  c4 5d 4b ae 3d aa 2c f5  |.F.5>..-.]K.=.,.|
00000170  72 a6 60 4f c7 84 c4 4e  5e 23 be 25 0b 91 4d 29  |r.`O...N^#.%..M)|
00000180  4c 8e c0 f1 2c f0 fb b0  3b 04 da 6f 09 ac b4 85  |L...,...;..o....|
00000190  f3 df 64 47 2c 7d 0e 25  5e e1 91 67 87 0c ab b7  |..dG,}.%^..g....|
000001a0  88 4d b5 92 33 14 a6 48  3e ea b5 00 7e aa ff 9c  |.M..3..H>...~...|
000001b0  79 0a a9 19 56 95 f4 e0  94 80 61 57 26 a7 00 01  |y...V.....aW&...|
000001c0  01 01 07 fe ff ff 3f 00  00 00 92 bc 6d 04 00 00  |......?.....m...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  00 11 00 00 00 39 00 39  00 31 00 00 00 48 79 00  |.....9.9.1...Hy.|
00000010  00 11 00 00 00 39 00 39  00 32 00 00 00 59 79 00  |.....9.9.2...Yy.|
00000020  00 2f 00 00 00 39 00 39  00 33 00 00 00 88 79 00  |./...9.9.3....y.|
00000030  00 11 00 00 00 39 00 39  00 34 00 00 00 99 79 00  |.....9.9.4....y.|
00000040  00 11 00 00 00 39 00 39  00 35 00 00 00 aa 79 00  |.....9.9.5....y.|
00000050  00 11 00 00 00 39 00 39  00 36 00 00 00 bb 79 00  |.....9.9.6....y.|
00000060  00 11 00 00 00 39 00 39  00 37 00 00 00 cc 79 00  |.....9.9.7....y.|
00000070  00 11 00 00 00 39 00 39  00 38 00 00 00 dd 79 00  |.....9.9.8....y.|
00000080  00 11 00 00 00 39 00 39  00 39 00 00 00 ee 79 00  |.....9.9.9....y.|
00000090  00 11 00 00 00 31 00 30  00 30 00 30 00 00 00 ff  |.....1.0.0.0....|
000000a0  79 00 00 11 00 00 00 31  00 30 00 30 00 31 00 00  |y......1.0.0.1..|
000000b0  00 10 7a 00 00 11 00 00  00 31 00 30 00 30 00 32  |..z......1.0.0.2|
000000c0  00 00 00 21 7a 00 00 11  00 00 00 31 00 30 00 30  |...!z......1.0.0|
000000d0  00 33 00 00 00 32 7a 00  00 11 00 00 00 31 00 30  |.3...2z......1.0|
000000e0  00 30 00 34 00 00 00 43  7a 00 00 11 00 00 00 31  |.0.4...Cz......1|
000000f0  00 30 00 30 00 35 00 00  00 54 7a 00 00 11 00 00  |.0.0.5...Tz.....|
00000100  00 31 00 30 00 30 00 36  00 00 00 65 7a 00 00 11  |.1.0.0.6...ez...|
00000110  00 00 00 31 00 30 00 30  00 37 00 00 00 76 7a 00  |...1.0.0.7...vz.|
00000120  00 11 00 00 00 31 00 30  00 30 00 38 00 00 00 87  |.....1.0.0.8....|
00000130  7a 00 00 11 00 00 00 31  00 30 00 30 00 39 00 00  |z......1.0.0.9..|
00000140  00 98 7a 00 00 11 00 00  00 31 00 30 00 31 00 30  |..z......1.0.1.0|
00000150  00 00 00 a9 7a 00 00 1b  00 00 00 31 00 30 00 31  |....z......1.0.1|
00000160  00 31 00 00 00 c4 7a 00  00 11 00 00 00 31 00 30  |.1....z......1.0|
00000170  00 31 00 32 00 00 00 d5  7a 00 00 11 00 00 00 31  |.1.2....z......1|
00000180  00 30 00 31 00 33 00 00  00 e6 7a 00 00 11 00 00  |.0.1.3....z.....|
00000190  00 31 00 30 00 31 00 34  00 00 00 f7 7a 00 00 11  |.1.0.1.4....z...|
000001a0  00 00 00 31 00 30 00 31  00 35 00 00 00 08 7b 00  |...1.0.1.5....{.|
000001b0  00 11 00 00 00 31 00 30  00 31 00 36 00 00 00 20  |.....1.0.1.6... |
000001c0  21 00 82 1b 28 f3 02 00  00 00 00 90 3b 00 00 1b  |!...(.......;...|
000001d0  29 f3 05 fe ff ff 02 90  3b 00 00 48 a8 04 00 00  |).......;..H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```
That is the output of the bootinfo script.
Thanks

---

### Post by clancymf on 2010-07-08
This may be of no help, but if you are anxiously sitting around waiting for a response try switching the sata connections to your hard drive so that linux is on the sda and windows is assigned sdb.

---

