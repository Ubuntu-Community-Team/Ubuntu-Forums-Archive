---
title: "Wrong mount points chosen during installation. How to change without new install."
date: 2011-03-29
forum: New to Ubuntu
---

### Post by sasun on 2011-03-29
Hi there,

after being very satisfied and happy with Ubuntu 10.10 I couldn't help but tell my friends of how much better and cleverer this OS is compared to MS with the result that some of my friends gave it a try. 

Unfortunately, one of them chose a wrong mounting point during the installation process (mixed up /home with /usr) which resulted in the big problem of running out of space at /root.

As this one is no expert at all, I try to help him out (being no expert at all myself). But as I have some very good experiences using UbuntuForums here you go!

So the question would be if there is a way to manually change the mount points afterwards, so that he wouldn't need to do a complete reinstall.

I downloaded the BootScript and here are the RESULTS:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          19,533,822   625,141,759   605,607,938   5 Extended
/dev/sda5          19,533,824    27,344,895     7,811,072  82 Linux swap / Solaris
/dev/sda6          27,346,944   625,141,759   597,794,816  83 Linux


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 7864 MByte, 7864320000 Byte
256 Köpfe, 33 Sektoren/Spur, 1818 Zylinder, zusammen 15360000 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,359,999    15,359,968   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 129 MByte, 129892352 Byte
8 Köpfe, 32 Sektoren/Spur, 991 Zylinder, zusammen 253696 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             97       253,695       253,599   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        41545059-49da-48cb-9bdb-da8d5468b484   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        84dc2b71-fa45-49f0-a9f4-6a3763930c7d   swap                                     
/dev/sda6        00194eae-bdbb-4a01-9c9d-1dde74c28028   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1DE6-3173                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        10DF-8324                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /usr                     ext4       (rw,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/PENDRIVE_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 00194eae-bdbb-4a01-9c9d-1dde74c28028
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=41545059-49da-48cb-9bdb-da8d5468b484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=41545059-49da-48cb-9bdb-da8d5468b484 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41545059-49da-48cb-9bdb-da8d5468b484 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41545059-49da-48cb-9bdb-da8d5468b484 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41545059-49da-48cb-9bdb-da8d5468b484
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /usr was on /dev/sda6 during installation
UUID=00194eae-bdbb-4a01-9c9d-1dde74c28028 /usr            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=84dc2b71-fa45-49f0-a9f4-6a3763930c7d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/initrd.img-2.6.35-27-generic
   4.5GB: boot/vmlinuz-2.6.35-22-generic
   4.5GB: boot/vmlinuz-2.6.35-27-generic
   1.4GB: initrd.img
   1.3GB: initrd.img.old
   4.5GB: vmlinuz
   4.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  30 80 38 40 4e 00 09 00  0c 00 00 d2 00 9a 02 0b  |0.8@N...........|
00000010  00 0e 84 00 10 a0 6d 12  00 11 00 61 0a 07 41 0c  |......m....a..A.|
00000020  e1 08 e0 4e 00 4d 64 48  64 55 e0 6b 00 e1 7b 24  |...N.MdHdU.k..{$|
00000030  e0 06 d8 80 58 d0 41 60  00 4d 64 53 70 0b e0 01  |....X.A`.MdSp...|
00000040  4f 01 80 05 0d 0a 00 75  72 6e 3a 00 73 63 68 65  |O......urn:.sche|
00000050  6d 61 73 2d 02 6d c6 42  63 6f 6d 3a 61 73 00 6d  |mas-.m.Bcom:as.m|
00000060  2e 76 33 00 61 73 73 00  65 6d 62 6c 79 00 78 6d  |.v3.***.embly.xm|
00000070  00 6c 6e 73 00 6d 61 6e  69 10 66 65 73 74 44 53  |.lns.mani.festDS|
00000080  00 31 2e 04 30 00 c0 53  79 72 69 67 68 20 74 00  |.1..0..Syrigh t.|
00000090  43 6f 70 23 01 20 28 08  63 29 20 c6 4c 20 43 6f  |Cop#. (.c) .L Co|
000000a0  72 20 70 6f 72 61 74 80  59 2e 20 a0 41 6c 6c 20  |r porat.Y. .All |
000000b0  52 c1 05 73 81 59 00 65  72 76 65 64 2e 00 0d 88  |R..s.Y.erved....|
000000c0  0a 20 20 66 0d 49 64 65  c0 3e 30 74 79 00 6e a1  |.  f.Ide.>0ty.n.|
000000d0  40 bf 55 00 76 23 03 65  8d 3b 70 72 6f 00 65 73  |@.U.v#.e.;pro.es|
000000e0  6f 00 72 41 72 63 68 69  74 65 00 63 74 75 72 65  |o.rArchite.cture|
000000f0  00 61 6d 00 64 36 34 00  6c 61 6e 67 e0 75 61 67  |.am.d64.lang.uag|
00000100  65 00 00 51 80 54 02 54  00 54 79 70 65 00 72 65  |e..Q.T.T.Type.re|
00000110  6c c0 65 61 73 65 00 70  0b 53 6d 6d 13 65 0e 82  |l.ease.p.Smm.e..|
00000120  73 00 6e 23 39 66 69 6c  93 00 08 2c 51 00 64 e0  |s.n#9fil...,Q.d.|
00000130  25 69 6e a2 1f f0 50 61  74 68 d9 5a 63 7b 82 5f  |%in...Path.Zc{._|
00000140  43 01 d3 02 06 e0 77 69  6d 00 28 74 c4 07 b6 69  |C.....wim.(t...i|
00000150  03 a1 28 e0 28 73 65 63  75 72 69 00 74 79 44 65  |..(.(securi.tyDe|
00000160  73 63 72 69 60 70 74 6f  72 00 d3 61 bc 3f 32 01  |scri`ptor..a.?2.|
00000170  20 32 6d 76 32 00 68 61  73 00 68 00 68 74 74 70  | 2mv2.has.h.http|
00000180  3a 2f 00 2f 77 77 77 2e  77 33 2e 00 6f 72 67 2f  |:/./www.w3..org/|
00000190  32 30 30 30 6a 2f c2 42  2f e2 37 20 00 00 d5 04  |2000j/.B/.7 ....|
000001a0  30 02 39 21 05 64 73 69  67 23 00 01 a1 00 00 54  |0.9!.dsig#.....T|
000001b0  72 61 6e 73 66 70 6f 72  6d 73 66 07 20 17 00 fe  |ransfpormsf. ...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 77 00 00 fe  |...........0w...|
000001d0  ff ff 05 fe ff ff 02 30  77 00 00 a8 a1 23 00 00  |.......0w....#..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 5f ea 00 bc 74 00 00  00 00 00 00 02 00 00 00  |._...t..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 73 31 e6 1d 4e  4f 20 4e 41 4d 45 20 20  |..)s1..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 9c  e9 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 02 22 00  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 61 00 00 00  |........?...a...|
00000020  9f de 03 00 d7 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 24 83 df 10 4e  4f 20 4e 41 4d 45 20 20  |..)$...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 d2  07 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by TeoBigusGeekus on 2011-03-29
I don't know of a way to merge /usr with the rest of the / folder, so I can only suggest that your friend should leave it as it is.
The only thing I'd do, is resize the /usr partition with a live cd and gparted and create a separate /home partition.
Here's a guide for it
[http://www.ehow.com/how_6182851_create-partition-after-install-ubuntu.html]("http://www.ehow.com/how_6182851_create-partition-after-install-ubuntu.html")
I'd leave about 10gb to the /usr partition and convert the rest of it to a separate home one.

---

### Post by eriktheblu on 2011-03-29
From what I gather, you have sda2 mounted as /, and sda6 as /usr, but you want sda6 as /home.

Assuming you have adequate space on sda6:
from a live session
1. Copy /home files to sda6
2. Delete /home/ subdirectories on sda2
3. copy /usr files from sda6 to the /usr directory on sda2
4. edit /etc/fstab to reflect the new allocation
5. reboot

---

### Post by fabricator4 on 2011-03-29
> **sasun said:**
> 

Firstly, and this is just an observation, the boot drive is 10 GB in size.  This a adequate for most things, but for someone who wants to install _lots_ of programs and try them all, it's probably a bit tight.  The system will use over 1/3 of it on a fresh install, and continue to use it as programs and updates are installed.  If the user is willing to do housecleaning on the drive occasionally and deletes programs that have been tried and found unsuitable (or that don't get used) then it should be fine.

[quote]
So the question would be if there is a way to manually change the mount points afterwards, so that he wouldn't need to do a complete reinstall.


The mount points for the partitions are declared in the /etc/fstab file and indeed /dev/sda6 is mounting as /usr.  I suggest you boot off the pendrive again (which I note was still mounted in the machine when your ran the bootscript) and change the line which says:

```

UUID=00194eae-bdbb-4a01-9c9d-1dde74c28028 /usr   ext4    defaults        0

```

to be:

```

UUID=00194eae-bdbb-4a01-9c9d-1dde74c28028 /home   ext4    defaults        0

```

In other words, just change /usr to /home


While still booted off the pendrive you will also have to move the user's /home/username directory to the new /home.

The easiest way to do all of this is probably start Nautilus file manager in superuser (SU) mode.  Press <alt><F2> then type "gksu nautilus" in the box, then click the run button. When Nautilus opens it will have on the screen the root user's directory on the pendrive.  Do not confuse this with the setup that is on the hardrive.

To see sda1 (the / partition) and sda6 (the /home partition)  you will have to mount them.  Click places, and then double click both file systems you see there: one will be about 10 GB and the other will be about 300+ GB, give or take a bit.  Close both the windows that open up - they don't have superuser privileges and are of no help at this point except we got the system to mount the partitions.

Now in the SU nautilus windows double click on the 10 GB partition (it will now be in the pane at the left)  Go into /etc and then double click on fstab.  Make the changes outlined above.

Now go back one level and go into /home.  There you should see the user's directory.  Click on the view menu at the top and look in the drop-down, make sure "show hidden files" is ticked.

Open another SU nautilus window (alt-F2, gksu nautilus etc) and double click on the 300+ GB filesystem.  The window will open up and there will be Nothing in it except perhaps "lost+found".  Drag the user's directory "username" into the second window next to "lost+found".  Once it is copied, everything is in the right place.  

Make sure the original /home/username has be copied completely, including hidden files and directories.  You can then delete it to free up space for the filesystem.

This may be the last time I give GUI type instructions!  I could have done this in half a dozen lines in CLI much more clearly. :(

Edit, as per the next message, I forgot that you will have to move the data on sda6 back to /usr on the 10 GB partition, after creating the folder /usr of course

Chris.

---

### Post by fabricator4 on 2011-03-29
> **TeoBigusGeekus said:**
> I don't know of a way to merge /usr with the rest of the / folder, so I can only suggest that your friend should leave it as it is.

Oh, I forgot that step!

You can simply create /usr on the 10 GB partition and copy the contents of sda6 to it.  It's the same as the instructions for moving /home to the second partition, only in reverse.

Chris.

---

### Post by vanadium on 2011-03-29
In principle, it could be done by making an exact copy of /usr to a directory /usr on the root partition, copying /home to the /usr partition, and updating /etc/fstab.

It should be done from a system that is not using the drives, i.e. from a live session. It may also work from a recovery root prompt, but I am not sure if in that case it is allowed to unmount the /usr partition at some point.

In any case, it is not something that belongs to an Absolute Beginners forum.

---

### Post by sasun on 2011-03-29
Hi fabricator4,

thank you for your help. In fact, I don't understand either, why he runs out of space, as he did a standard ubuntu install (x64) with virtualbox extra. That's it. But everytime he's booting up, there comes a warning that the root partition has only 140 MB of space left.

Ok, it may be also because of hybernate. But it also seems odd to me how 10 GB could run out so fast.

I tried to check that out, but as I can't see exactly which data (or folders) belong to which partition I eventually gave up on that.

Perhaps I should check that one first?

P.S: Feel free to write CLI, I can handle it. :) THANKS!

---

### Post by fabricator4 on 2011-03-29
> **sasun said:**
>  That's it. But everytime he's booting up, there comes a warning that the root partition has only 140 MB of space left.


It will be data in the /home/username directory.  I think you'll find that there is about 6 GB of data in there, enough to run the boot partition out so that there's very little space.

OK, should have written CLI in the first place.  Boot off the LiveUSB and :

```

# make mount points for the partitions and mount them so that we can work on them.
sudo mkdir /media/bootdrv
sudo mkdir /media/homedrv
sudo mount /dev/sda1 /media/bootdrv
sudo mount /dev/sda6 /media/homedrv

# move the /home/username to the large partition
sudo cp -Rv /media/bootdrv/home/* /media/homedrv/

# Now delete the /home/username on the boot drive so we've got some free space:
# make sure that home directory has copied correctly to the right place first!
sudo rm -R /media/bootdrv/home/username/

# make the /correct /usr directory on the file system and move everything to it
sudo mkdir /media/bootdrv/usr
sudo cp -Rv /media/homedrv/* /media/bootdrv/usr


# Now just edit the fstab as discussed in the previous post to change it so that sda6 mounts as /home instead of /usr

sudo nano /media/bootdrv/etc/fstab


```

You can use gedit for the editor if you prefer.  Once this is done reboot and you should be good to go....

Once the system is working you should go to /home and delete everything that is not "username".  this is all the old usr stuff left over from when it was being used as /usr



Chris.

---

### Post by sasun on 2011-03-30
Hi fabricator4,

thanks for your answer. I will do as you told and come back to you later with the outcome of the enterprise!!

1000 times thank you in advance.
And: Long live the CLI :)

---

### Post by fabricator4 on 2011-03-30
> **sasun said:**
> Hi fabricator4,

thanks for your answer. I will do as you told and come back to you later with the outcome of the enterprise!!

1000 times thank you in advance.
And: Long live the CLI :)

Oops, my instructions have you copying the /media/homedrv/username data back into /media/bootdrv/username.  A slight oversight.  If theres enough room to complete the copy, just remove the unwanted data that gets copied into /media/bootdrive/username before you reboot:

```

sudo rm -Rv /media/bootdrv/username

```

However /usr may need around 1 GB.  This is one case where it might be easier to use Nautilus since you can selectect everything _except_ /media/homedrv/username with a few keystrokes.

Chris

---

### Post by vanadium on 2011-03-30
Nice elaboration. I would advise to add the -a switch to the cp command, in order to preserve all file attributes/ownerships of the copied files.
In fact, I'd rather use
rsync -aHv
in order to not only preserve attributes, but also hardlinks if any.

---

### Post by sasun on 2011-03-31
Hi there,

I tried yesterday and it didn't work out - first because there wasn't enough space and second because of a mistake of mine. So we ended up doing a reinstall.

Thanks nevertheless!

---

### Post by fabricator4 on 2011-03-31
> **sasun said:**
> Hi there,

I tried yesterday and it didn't work out - first because there wasn't enough space and second because of a mistake of mine. So we ended up doing a reinstall.

Thanks nevertheless!

That's OK.  If you take away the experience and the knowledge of how things work that is at least as important as fixing your friend's computer!

Chris

---

