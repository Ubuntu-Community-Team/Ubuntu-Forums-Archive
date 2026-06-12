---
title: "Lubuntu 10.10 Grub got rid of my Windows bootloader in Grub"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2010-10-11
I am dual booting with Windows 7 (/dev/sda2, Windows Recovery is at /dev/sda1); lubuntu 10.10 on install wont recognize my Windows loader--there is no entry in the Grub menu.

Any way to get the windows boot loader entry in Grub?

Thanks
S

---

### Post by Quackers on 2010-10-11
Try running sudo update-grub in a terminal and watch to see if Windows is there during grub.cfg
If it doesn't you will need to repair the Windows bootloader via the Windows repair disc.

---

### Post by shuttleworthwannabe on 2010-10-11
Not there I am afraid--I did the Windows repair and now Grub is gone altogether. 

any fix? I see others also go this problem on development forums but the hack is not intuitive for me.

S

---

### Post by Quackers on 2010-10-11
Does lubuntu boot up via grub or directly, or not at all?

---

### Post by shuttleworthwannabe on 2010-10-11
It boots via Grub menu. Why?

---

### Post by naht on 2010-10-13
I had exactly the same problem - also with Lubuntu Maverick


```
root@Desktop:/home/naht# update-grub
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```


```
root@Desktop:/home/naht# fdisk -l

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe11fe11f

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        6406    51455320+   7  HPFS/NTFS
/dev/sda2            6407       38913   261112415+   5  Erweiterte
/dev/sda5            7681        7744      514048+  82  Linux Swap / Solaris
/dev/sda6            7745       19127    91433916    7  HPFS/NTFS
/dev/sda7           19765       31876    97289608+   7  HPFS/NTFS
/dev/sda8           31877       38913    56524671    7  HPFS/NTFS
/dev/sda9            6407        7680    10233342   83  Linux
/dev/sda10          19128       19764     5116671   83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

I just tried executing /etc/grub.d/30_os-prober, and there is no output at all...

---

### Post by Rubi1200 on 2010-10-13
@ naht

Use a LiveCD and post the results of the boot-script linked at the bottom of my post please.

Thanks.

---

### Post by naht on 2010-10-13
Hi, I can't reboot ATM, but I ran the script from my linux.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for (,msdos9)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „“

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „“
mount: unbekannter Dateisystemtyp „“

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unbekannter Dateisystemtyp „“
mount: unbekannter Dateisystemtyp „“
mount: unbekannter Dateisystemtyp „“

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *             63   102,910,703   102,910,641   7 HPFS/NTFS
/dev/sda2         102,912,514   625,137,344   522,224,831   5 Extended
/dev/sda5         123,379,263   124,407,359     1,028,097  82 Linux swap / Solaris
/dev/sda6         124,407,423   307,275,254   182,867,832   7 HPFS/NTFS
/dev/sda7         317,508,723   512,087,939   194,579,217   7 HPFS/NTFS
/dev/sda8         512,088,003   625,137,344   113,049,342   7 HPFS/NTFS
/dev/sda9         102,912,516   123,379,199    20,466,684  83 Linux
/dev/sda10        307,275,318   317,508,659    10,233,342  83 Linux


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder, zusammen 2930277168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    97,658,879    97,656,832   7 HPFS/NTFS
/dev/sdb2          97,659,135 2,930,272,064 2,832,612,930   5 Extended
/dev/sdb5          97,659,198   976,559,219   878,900,022   7 HPFS/NTFS
/dev/sdb6         976,559,283 2,930,272,064 1,953,712,782   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 1998 MByte, 1998519808 Byte
32 Köpfe, 63 Sektoren/Spur, 1936 Zylinder, zusammen 3903359 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,902,975     3,902,913   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/truecrypt1 200074790074582C                       ntfs       BILDER                        
/dev/mapper/truecrypt2 E088AA5F88AA33C6                       ntfs       Volume                        
/dev/mapper/truecrypt3 06F4B25DF4B24EA5                       ntfs       Volume                        
/dev/sda1        00F8D4DDF8D4D250                       ntfs       Vista 64                      
/dev/sda10       f1513503-3af3-4ab2-a317-ffc76283076d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f08d93ad-4b59-4d18-a1ad-4dc50c95c35c   swap                                     
/dev/sda6        B06C1B836C1B438E                       ntfs       E                             
/dev/sda7        D2F6D9E2F6D9C6BF                       ntfs       D                             
/dev/sda9        89fe6849-511e-4c40-9347-42012cefcd6d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        36EEB775EEB72BCD                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        44A4-5AB1                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
truecrypt1
truecrypt2
truecrypt3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda10       /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/mapper/truecrypt1 /media/truecrypt1        fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)
/dev/mapper/truecrypt2 /media/truecrypt2        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/truecrypt3 /media/truecrypt3        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /NOEXECUTE=OPTIN /FASTDETECT /MAXMEM=2048 /NUMPROC=4

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=89fe6849-511e-4c40-9347-42012cefcd6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=89fe6849-511e-4c40-9347-42012cefcd6d ro single 
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
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 89fe6849-511e-4c40-9347-42012cefcd6d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# For booting Microsoft Windows
menuentry "Microsoft Windows" {
	set root=(hd0,1)
	chainloader +1
}### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=89fe6849-511e-4c40-9347-42012cefcd6d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=f1513503-3af3-4ab2-a317-ffc76283076d /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f08d93ad-4b59-4d18-a1ad-4dc50c95c35c none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/core.img
  55.7GB: boot/grub/grub.cfg
  53.9GB: boot/initrd.img-2.6.35-22-generic
  59.5GB: boot/vmlinuz-2.6.35-22-generic
  53.9GB: initrd.img
  59.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda8

00000000  b2 f4 70 63 2b a6 59 e1  7c b0 fb f0 8f 33 8c c9  |..pc+.Y.|....3..|
00000010  52 9d 9b 18 44 01 c3 c1  41 3c 5e f3 9f 02 37 47  |R...D...A<^...7G|
00000020  5d cf e5 b1 bd 2a 75 7a  70 b6 a9 bd 48 ae 4c fa  |]....*uzp...H.L.|
00000030  c3 69 35 ab d1 96 b2 fb  0a 71 e0 0e e1 58 1f ea  |.i5......q...X..|
00000040  c2 18 4b 20 90 51 ec d8  2f 78 5a 91 b6 a7 8b b7  |..K .Q../xZ.....|
00000050  b4 52 5f bd f6 20 f7 90  6f a6 26 2d bd 2a 12 5d  |.R_.. ..o.&-.*.]|
00000060  07 02 16 65 89 45 c8 f2  47 99 4d 81 87 34 c6 97  |...e.E..G.M..4..|
00000070  89 b1 b3 c1 0f 05 e1 d1  65 b9 91 1e ce 58 35 08  |........e....X5.|
00000080  db 7d 42 ea e5 44 7a e2  33 7e db 15 d8 cb e2 a3  |.}B..Dz.3~......|
00000090  2d 13 11 de e9 d5 45 86  96 df 11 56 ed c3 14 e6  |-.....E....V....|
000000a0  09 91 95 57 a3 50 65 f0  f6 47 2c 8c 94 b2 50 b1  |...W.Pe..G,...P.|
000000b0  aa cd ee 62 21 0b 00 53  28 fb d5 93 b4 54 e0 72  |...b!..S(....T.r|
000000c0  c3 23 c2 c7 3d 08 95 02  9d e3 e2 8c dd 4c c5 6d  |.#..=........L.m|
000000d0  e3 a0 e1 5d e4 3d a1 54  3f 8d 98 64 de 66 29 7d  |...].=.T?..d.f)}|
000000e0  71 a5 95 9b 95 a4 9b 20  bf fc de b4 78 c0 63 71  |q...... ....x.cq|
000000f0  d9 b6 c8 02 5a 81 29 93  8f dd c6 76 80 c5 dc 8c  |....Z.)....v....|
00000100  88 41 cd 8b 99 bb 49 48  f9 8c b9 b9 25 6f 57 bd  |.A....IH....%oW.|
00000110  b8 7e 35 1b bc e4 ab 57  25 ab f8 42 f5 16 df 57  |.~5....W%..B...W|
00000120  7a f1 65 a0 6b 47 57 6e  91 a9 89 e5 08 8a d9 ad  |z.e.kGWn........|
00000130  33 56 d7 32 eb 39 9b e7  4e 67 1a d6 cb dd 2e 8d  |3V.2.9..Ng......|
00000140  34 b2 49 86 f9 d1 7b db  c7 3a b1 b5 86 1f 6c 9a  |4.I...{..:....l.|
00000150  18 0f fa f1 a3 dc 62 7c  87 b9 64 03 83 90 69 bd  |......b|..d...i.|
00000160  48 43 13 1f bb dc 78 a3  5e ae 00 f7 3a 7e f4 10  |HC....x.^...:~..|
00000170  25 14 89 26 8f 75 ea 6b  cd 22 d6 11 74 23 3e 72  |%..&.u.k."..t#>r|
00000180  d9 87 6c 3a 7c 75 75 07  5e 92 a7 09 57 a2 fb dd  |..l:|uu.^...W...|
00000190  ad 9d 9b 66 90 8c e0 23  fd 7a ab 78 cc 50 ce b1  |...f...#.z.x.P..|
000001a0  13 52 4b 76 f2 98 23 c6  73 72 83 a8 46 81 28 70  |.RKv..#.sr..F.(p|
000001b0  d0 41 67 54 a7 a8 c0 06  b1 35 27 f7 51 00 20 68  |.AgT.....5'.Q. h|
000001c0  57 f6 f3 30 85 b0 70 13  24 46 06 d2 5e 71 c1 a4  |W..0..p.$F..^q..|
000001d0  4d 57 32 87 4c 44 d9 06  64 ae 34 97 ef c3 9c e8  |MW2.LD..d.4.....|
000001e0  15 ee 7b 17 a3 53 ad d1  51 84 f9 f0 80 4d 33 35  |..{..S..Q....M35|
000001f0  04 b2 c2 d2 ba 37 27 b1  e5 07 72 02 9f 5a fd f5  |.....7'...r..Z..|
00000200

Unknown BootLoader  on sdb5

00000000  08 7b 77 40 50 d4 92 eb  7d 96 8a 5b f3 9c 76 95  |.{w@P...}..[..v.|
00000010  c0 ce 74 26 8a af 01 40  56 c1 1d 11 ce fd 74 b9  |..t&...@V.....t.|
00000020  af dd 76 af 98 29 b3 1a  a8 da 42 a9 37 48 b3 cd  |..v..)....B.7H..|
00000030  4f 1a 78 86 1b 06 44 3b  6a 94 f3 d5 ae ab 9e da  |O.x...D;j.......|
00000040  92 ee 60 c0 7f d5 b6 ee  9d 00 1a ca 1a 60 69 d4  |..`..........`i.|
00000050  52 ee ba cd e0 52 52 c3  8d 14 a1 42 99 4e 1e 65  |R....RR....B.N.e|
00000060  c2 40 77 40 15 2f d5 38  52 52 4d 85 ee c0 13 88  |.@w@./.8RRM.....|
00000070  83 0e 26 d4 76 7c 52 5c  35 1c ae c3 00 a5 a4 da  |..&.v|R\5.......|
00000080  7a bb 9b 0d ae 6f 54 7e  e3 51 ca 48 c6 57 2c 3e  |z....oT~.Q.H.W,>|
00000090  1a 20 66 58 5c 2d 18 79  98 cf 70 45 84 c3 ba 81  |. fX\-.y..pE....|
000000a0  ee 3c 2b 27 91 5a 49 e9  fb f4 2b 10 9a 63 d6 13  |.<+'.ZI...+..c..|
000000b0  29 bd eb 50 16 de 38 c7  a2 b1 d4 3f 9d f9 9e 58  |)..P..8....?...X|
000000c0  c9 e7 12 c1 85 bd 69 10  1d e7 ab 8c 25 77 54 e1  |......i.....%wT.|
000000d0  95 bf 3c f8 1b ec ab 0f  5e 1d 0a ef f1 0b dd 36  |..<.....^......6|
000000e0  36 24 f4 85 b1 2c 0d 16  1d d6 c9 10 71 6c ee aa  |6$...,......ql..|
000000f0  9f af f5 d2 7a 0c fd f7  ed c3 ec d0 ce 21 a1 1a  |....z........!..|
00000100  bb 8f 8e b8 c5 5e 0b 32  fc 66 5c c8 c1 83 54 69  |.....^.2.f\...Ti|
00000110  47 29 55 ad 8f 9d 15 1f  53 46 0c dc c4 b6 17 0f  |G)U.....SF......|
00000120  4b f4 41 68 ab dc 57 0e  e8 eb d8 4e ac 21 02 1a  |K.Ah..W....N.!..|
00000130  0d c3 92 b3 9c b7 2c 50  28 61 2f 31 22 ef 81 3a  |......,P(a/1"..:|
00000140  1b 32 68 3d 34 71 ba 5b  3e 68 87 24 d6 09 e7 dd  |.2h=4q.[>h.$....|
00000150  02 5d d5 9b e1 43 be cc  79 70 23 e4 dd f7 e0 f2  |.]...C..yp#.....|
00000160  4e ea 69 ad 5c 72 7f e0  20 a2 83 e2 bf 28 cb 85  |N.i.\r.. ....(..|
00000170  d1 89 d4 f3 f8 ed 48 1e  a8 f6 f3 74 46 f2 10 8c  |......H....tF...|
00000180  d3 fe 3c 66 40 0b 7c f0  20 9b 62 81 73 04 be 08  |..<f@.|. .b.s...|
00000190  81 0e 23 25 90 3f 9a 51  60 c8 9d 9c de c5 f1 d7  |..#%.?.Q`.......|
000001a0  47 aa 2e fa c2 f6 40 ee  53 5f 58 6d 57 01 17 bb  |G.....@.S_XmW...|
000001b0  1f 16 c4 cc c0 ae 63 5d  2a 6b cd 8c 9a ce ea d1  |......c]*k......|
000001c0  8f 4f 4d 39 d7 ad 52 7a  55 cb c0 e7 d5 19 bf 27  |.OM9..RzU......'|
000001d0  0a 52 d1 03 2e 65 74 7e  33 3e a9 49 82 a6 ef 73  |.R...et~3>.I...s|
000001e0  44 f9 f4 fb 58 37 cb 5b  23 b8 55 d8 28 e5 a9 70  |D...X7.[#.U.(..p|
000001f0  d4 c1 57 29 66 c5 05 26  08 fb f8 1d 48 28 63 97  |..W)f..&....H(c.|
00000200

Unknown BootLoader  on sdb6

00000000  6c 03 ef 18 f6 11 d5 0e  2b 52 e6 79 30 ba 5e 9e  |l.......+R.y0.^.|
00000010  7f 33 de f3 1a af 74 f1  ec bf a0 81 a9 1e 2e 05  |.3....t.........|
00000020  84 1d 2d 23 31 54 13 e6  75 78 d7 ee 87 2f 5b 9c  |..-#1T..ux.../[.|
00000030  fd 3d 23 6d db fe 07 1b  04 71 34 7d e8 0d 5f 1b  |.=#m.....q4}.._.|
00000040  b9 49 25 ca c8 6d 64 7e  ea 92 83 95 84 dd bc 93  |.I%..md~........|
00000050  57 e3 ae e1 78 df 37 8b  23 1e 53 71 67 69 8f 2c  |W...x.7.#.Sqgi.,|
00000060  0b 16 33 bf fa af 86 cf  ec c2 a1 29 bc d9 74 e1  |..3........)..t.|
00000070  36 a4 25 6d 76 3a 19 d8  c9 1e 1c f4 b2 c9 d4 aa  |6.%mv:..........|
00000080  aa 21 f0 66 52 27 fb 5b  38 9a dd 6c 88 aa 51 85  |.!.fR'.[8..l..Q.|
00000090  15 3e 8f d0 c2 d3 b8 f3  1b 9f ad 60 22 09 bb db  |.>.........`"...|
000000a0  b3 41 6a 93 4e 71 19 49  6e 3a f7 ba 37 99 e9 1f  |.Aj.Nq.In:..7...|
000000b0  aa d8 7e 09 b3 e9 23 6f  e4 a9 5a 7a c1 31 c5 88  |..~...#o..Zz.1..|
000000c0  4d d9 cc 82 02 2d 34 bd  71 c2 09 f4 3a e2 74 f7  |M....-4.q...:.t.|
000000d0  ed 6a 7c f4 27 43 51 a7  29 7c e1 c8 29 2a de 13  |.j|.'CQ.)|..)*..|
000000e0  c7 b2 ee 8d 58 07 94 b1  2c f5 5d 70 2f 79 e9 38  |....X...,.]p/y.8|
000000f0  87 e2 8f c9 48 57 95 1a  53 ff 7b 3d a1 33 a3 4b  |....HW..S.{=.3.K|
00000100  c0 a5 61 ba dc 66 90 0d  74 61 3a 08 7e 8e cf c2  |..a..f..ta:.~...|
00000110  2a 92 e3 47 f7 e9 6f cd  a5 27 3f cf 18 a2 4f a5  |*..G..o..'?...O.|
00000120  b2 9e 3a 6a 2d 7c ba 2d  0c ed 4e 96 33 fd 77 64  |..:j-|.-..N.3.wd|
00000130  7c df ea c4 ec a6 08 3a  34 3d 11 9c 1a 36 ca 2f  ||......:4=...6./|
00000140  5e 51 a1 72 68 dc 59 17  36 22 9a 99 4b 31 6d 7b  |^Q.rh.Y.6"..K1m{|
00000150  bc 3a 1d 8b 95 46 32 85  9f 36 21 c4 d8 d2 4b 50  |.:...F2..6!...KP|
00000160  59 9c d8 43 25 ba cf 99  54 a4 f6 89 37 39 09 7d  |Y..C%...T...79.}|
00000170  51 b0 a5 d3 b7 5c 34 bd  c6 10 c6 16 68 5c 8c a3  |Q....\4.....h\..|
00000180  09 36 39 d4 b3 51 8a 7f  9b 18 34 fc 5d 9f e9 99  |.69..Q....4.]...|
00000190  04 f5 53 20 44 1e 4f 27  36 66 02 8a ac 4b 41 f4  |..S D.O'6f...KA.|
000001a0  14 5d 99 ef 7b 6a 76 de  40 d0 05 9a f6 e2 d0 7e  |.]..{jv.@......~|
000001b0  b7 80 9e 83 30 37 06 40  5a 7c 76 84 56 88 15 bc  |....07.@Z|v.V...|
000001c0  9c f3 7c b1 39 a5 e6 f8  a1 17 db 27 13 24 98 60  |..|.9......'.$.`|
000001d0  a6 18 e9 ee f5 05 0c 09  d2 17 a9 5d 4d 3f 58 b8  |...........]M?X.|
000001e0  15 a7 05 cc f7 4a 20 75  32 7b 65 72 31 bc c5 22  |.....J u2{er1.."|
000001f0  46 bb 96 3f 43 67 50 34  b5 90 bf 9e b4 4d a8 00  |F..?CgP4.....M..|
00000200
```

I created a windows entry in 40_custom to be able to use win, I know it will be gone soon...
As you can see, I have a truecrypt partition on /dev/sda. I didn't have that very long, maybe a week or two. Never had any such problems before, either.

---

### Post by Rubi1200 on 2010-10-13
Thanks for posting the results; much appreciated.

Well, I am a bit concerned that some of your partitions are marked as having an unknown file system 
> unbekannter DateisystemtypMoreover, the script points this out as a problem:
> Warning: Boot.ini is used on Windows XP and earlier operating systems. ;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. As far as Truecrypt is concerned, I cannot comment on that as I have never used it. I will ask some of the more experienced members to take a look and offer a perspective on your options.

Thanks for understanding.

---

### Post by oldfred on 2010-10-13
I have never used nor know anything about Truecrypt,

You have a minimal chainload to windows in sda1 that looks like it should work. Did your windows boot before? You do have Several windows. The install in sda shows vista or  win7 & XP files, but the XP boot.ini still refers to drive 0 partition 1 which is now your vista/win7. Script does not know details of BCD which may also contain your boot to windows in sdb1??

You might try the full win7 chainload, but once grub passes booting to windows, the issue is almost always with windows.

This was my XP stanza You would have to change UUID:

sudo blkid

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

---

### Post by drs305 on 2010-10-13
@ *shuttleworthwannabe  	*
When you repaired your Windows install it did two things. It recreated some necessary Windows folders/files, and most likely overwrote the MBR. Thus the MBR no longer points to the Grub files. It boots directly to Windows. 

If you reinstall grub from the LiveCD, Grub will again be placed in the MBR and point to the Grub files, which can boot both your Lubuntu and Windows OSs. The Windows files in the partition won't be affected, so now both OS's should be happy.

To reinstall Grub2 from the Live CD:
```
sudo mount /dev/sd[COLOR="Red"]XY[/COLOR] /mnt  # Use your Lubuntu partition - sda5, sdb1, etc
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]X[/COLOR] # Only the drive, sda, sdb, etc
```


@ naht,

EDIT ADDED: Looks like *oldfred* has given you a workable custom menu as I composed my post....

Insert these into your custom menu to load the correct modules, and add the drivemap line as well:
> insmod part_msdos
insmod ntfs
So it looks like:
> 
menuentry "Microsoft Windows" {
insmod part_msdos
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}
chainloader +1
}


---

### Post by shuttleworthwannabe on 2010-10-13
Thanx guys.

When I repaired using Windows 7 OS, it got rid of GRUB and went straight to Windows boot without showing the boot menu. However, when I tried reinstalling GRUB using Lubuntu Live-CD, it installed GRUB alright, but no Windows 7 (loader) on the menu.

I suspect when it installs GRUB, it does not "see" other OS on the hard disc. This has happened to me in Peppermint Ice as well. 

As a compromise, I installed the main Ubuntu Gnome full install, and then added Lubuntu-desktop to this. GRUB that comes with Ubuntu can see my Windows partition and boots into it fine. Although I have Ubuntu packages in this install (that are not needed in Lubuntu), I can live with workaround until this matter is fixed.

Thanks,

S

---

### Post by Glenn nl on 2010-10-15
I fixed this easily:

Install the os-prober package
Run ```
sudo os-prober
```
And now run ```
sudo update-grub
```

---

### Post by shuttleworthwannabe on 2010-10-17
You mean the vanilla lubuntu lacks this essential app? os-prober? I saw it being removed during the installtion sequence. Could this be the reason?

Thanks I will give this a try.
S

---

### Post by Glenn nl on 2010-10-17
> **shuttleworthwannabe said:**
> You mean the vanilla lubuntu lacks this essential app? os-prober? I saw it being removed during the installtion sequence. Could this be the reason?

Thanks I will give this a try.
S

Did it work?

---

### Post by bailout on 2010-10-19
Had the same problem myself with Lubuntu 10.10. Fixed it following the above instructions to install os-prober.

thanks

---

### Post by rafita on 2010-10-19
> **bailout said:**
> Had the same problem myself with Lubuntu 10.10. Fixed it following the above instructions to install os-prober.

thanks

thanks also, @Glenn, it worked beautifully for me too

---

### Post by shuttleworthwannabe on 2010-12-07
> **Glenn nl said:**
> Did it work?

Worked perfectly--sorry had to go out on long tour. Am back now and did a reinstall of the Lubuntu on my notebook---worked like a charm,

Thank you!
S

---

