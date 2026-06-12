---
title: "Windows 7 disappeared from bootloader"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Jetro on 2011-04-03
Yes, I know there are dozens of similar topics, but thing is they are like three years old, so they were with the old GRUB etc. or they always vary in some other way.

Very messy here.
I had two Ubuntus running, 10.04 and 10.10, and wanted to put Windows 7 on as well. I somehow managed to replace 10.10 with Win7 instead of splitting it, and had to use the liveUSB to get a grub back. It worked, but unfortunately Ubuntu 10.04 proved unusable otherwise. So:

I installed Windows 7, added Ubuntu 10.10 after, but Windows doesn't show up in the bootloader.

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3e4e3e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16841   135269377    5  Extended
/dev/sda2   *       16841       19458    21018624    7  HPFS/NTFS
/dev/sda5               1       10216    82057216   83  Linux
/dev/sda6           10217       14899    37608847    7  HPFS/NTFS
/dev/sda7           14899       16754    14900224   83  Linux
/dev/sda8           16754       16841      700416   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40931198

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

```

---

### Post by idoitprone on 2011-04-04
i just want to get rid of the obvious

```
sudo update-grub
```

try that command in the terminal to see if it fixes the problem


if you really want to go into detail, post the results of this boot script here. This will provide all the information anyone will need. Now its time for me to sleep kudos
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Jetro on 2011-04-04
Thanks, (all this done from the new 10.10 installation)

```
sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda5

```
Windows doesn't seem to appear.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               4,094   270,542,847   270,538,754   5 Extended
/dev/sda5               4,096   164,118,527   164,114,432  83 Linux
/dev/sda6         164,120,576   239,338,269    75,217,694   7 HPFS/NTFS
/dev/sda7         239,339,520   269,139,967    29,800,448  83 Linux
/dev/sda8         269,142,016   270,542,847     1,400,832  82 Linux swap / Solaris
/dev/sda2    *    270,542,848   312,580,095    42,037,248   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        28EF6B7158A8A24B                       ntfs       Staesj                        
/dev/sda5        6ded9daf-6cda-49e8-bb6e-7be687cc5c20   ext4       Ubuntu 10.04                  
/dev/sda6        1A2DF9F30F3157E5                       ntfs       Win7                          
/dev/sda7        5405d59d-41f3-4f64-a84c-88ec359a31f5   ext4                                     
/dev/sda8        c6342592-9b4a-4166-ac0e-848721b29694   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A42CE7D72CE7A312                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/Ubuntu 10.04      ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/A42CE7D72CE7A312  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
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
search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-30-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 ro splash quiet vga=769  quiet splash nomodeset video=uvesafb:mode_option=1600x1200-16,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 25d4e3ac-04e2-41cd-b13b-12c8ef6d143e
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=25d4e3ac-04e2-41cd-b13b-12c8ef6d143e ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

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
UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dc4f3e6b-0b2d-4fc7-9b51-9691745922fd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.2GB: boot/grub/core.img
  15.3GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.32-29-generic
  24.9GB: boot/initrd.img-2.6.32-30-generic
  28.0GB: boot/vmlinuz-2.6.32-29-generic
  23.6GB: boot/vmlinuz-2.6.32-30-generic
  24.9GB: initrd.img
  34.4GB: initrd.img.old
  23.6GB: vmlinuz
  28.0GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 ro splash quiet vga=769 quiet splash nomodeset video=uvesafb:mode_option=1600x1200-16,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.32-30-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c6342592-9b4a-4166-ac0e-848721b29694 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 133.4GB: boot/grub/core.img
 131.4GB: boot/grub/grub.cfg
 123.5GB: boot/initrd.img-2.6.35-22-generic
 133.4GB: boot/vmlinuz-2.6.35-22-generic
 123.5GB: initrd.img
 133.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  7f f9 67 03 61 0c 26 13  a6 17 e6 1a 18 1d 54 1d  |..g.a.&.......T.|
00000010  8a 1b c5 18 13 17 6a 17  28 18 04 19 6e 1a 2a 1c  |......j.(...n.*.|
00000020  68 1d 6a 1d 55 1c ba 1a  ea 18 3a 16 b9 11 4d 0a  |h.j.U.....:...M.|
00000030  47 00 82 f5 6c eb 34 e2  c8 d8 45 cf 54 c6 0d bf  |G...l.4...E.T...|
00000040  f8 b8 f3 b2 0c ae 70 ab  f2 aa 5f aa c3 a7 e9 a3  |......p..._.....|
00000050  ce a0 b8 9f f8 9f 5b 9e  98 98 f8 8d 2a 86 c6 84  |......[.....*...|
00000060  99 89 40 93 37 a1 7e b2  3f c4 85 d2 11 dc 84 e4  |..@.7.~.?.......|
00000070  2c f0 65 fe 17 0a 74 10  17 14 b0 18 2c 1f 7a 26  |,.e...t.....,.z&|
00000080  11 2c dd 2f 60 32 3d 33  2b 33 ac 32 43 33 27 34  |.,./`2=3+3.2C3'4|
00000090  4e 33 88 2f ab 28 11 20  7b 16 c4 0d b3 06 4e 00  |N3./.(. {.....N.|
000000a0  64 f9 25 f1 8c e8 3d e1  16 db 5e d3 bd ca 19 c3  |d.%...=...^.....|
000000b0  00 be e3 ba 79 b8 a6 b8  61 bb 07 c0 6a c5 55 cb  |....y...a...j.U.|
000000c0  5d d2 29 da d7 e1 69 e9  46 f1 17 f9 18 00 22 06  |].)...i.F.....".|
000000d0  69 0d 25 16 e0 1e ce 26  41 2f 2c 3a fd 45 87 50  |i.%....&A/,:.E.P|
000000e0  16 5a d9 62 32 6a c4 6f  c2 73 25 76 19 77 e5 76  |.Z.b2j.o.s%v.w.v|
000000f0  b7 75 a4 73 4f 71 dd 6e  a8 6b b0 67 b2 62 5c 5b  |.u.sOq.n.k.g.b\[|
00000100  c6 51 d9 48 6e 40 1c 38  a9 31 90 2e e9 2d 51 2e  |.Q.Hn@.8.1...-Q.|
00000110  7e 2e 3f 2e 63 30 2b 35  44 39 5e 3a 40 3c 49 3f  |~.?.c0+5D9^:@<I?|
00000120  13 41 79 40 95 3e ba 3e  9f 3d be 36 71 26 4a 0c  |.Ay@.>.>.=.6q&J.|
00000130  b4 ee ed d2 90 ba 2b a9  85 a1 45 a3 c9 a9 29 af  |......+...E...).|
00000140  3c b3 bd b8 ad c2 29 d2  04 e5 f8 f9 46 0d 72 1b  |<.....).....F.r.|
00000150  23 22 98 20 be 1b ce 16  ee 12 c6 11 85 13 dd 15  |#". ............|
00000160  99 17 c8 19 bd 1d 7c 22  09 28 c5 2d aa 33 c2 3a  |......|".(.-.3.:|
00000170  1c 40 81 42 d6 43 ea 45  09 48 41 46 ee 3f ff 38  |.@.B.C.E.HAF.?.8|
00000180  bb 2f e3 21 ca 10 69 00  2d f2 0a e5 a0 d8 49 cd  |./.!..i.-.....I.|
00000190  ea c2 7c ba da b3 c6 af  6f af 2c b3 ef ba 67 c3  |..|.....o.,...g.|
000001a0  90 cb 92 d3 ac d9 9b dc  a4 dd 8a de d8 de 25 dd  |..............%.|
000001b0  d9 db af dc 0d de 96 df  82 e2 62 e7 ee ed 00 41  |..........b....A|
000001c0  02 00 83 fe ff ff 02 00  00 00 00 30 c8 09 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff ea 35  c8 09 36 bd 7b 04 00 00  |.......5..6.{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by coffeecat on 2011-04-04
The reason update-grub is not detecting your Windows installation is that there are some boot files missing. Also, you have a rather odd Windows setup which is not really optimal. Your Windows C: partition would appear to be sda6 which is a logical partition and only about 38.5GB in size. Windows cannot boot from a logical partition and in this situation  for Windows 7 you would normally have a small primary boot partition of about 100MB. Your Windows boot partition, or at least the partition Windows boots from, seems to be sda2, which is about 21.5 GB in size. But some of the Windows boot files are missing - in particular /Boot/BCD.

It would be interesting to see what is in your sda2 "Staesj" and sda6 "Win7" partitions to see how the Windows OS files are split between the two.

I believe the way to repair the Windows boot files is to run "bootrec /FixBoot" from the Windows 7 repair disc command prompt. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Don't run 'bootrec /FixMbr' otherwise you'll write Windows code to the mbr and make the situation worse.

Once you've run FixBoot, update-grub *should* detect Windows.

---

### Post by Quackers on 2011-04-04
Windows is not being picked up because /boot/BCD is missing from your sda2 partition. I don't know where that's gone?
I would first try booting from the Windows repair/installation disc and using the repair my system option, then open up the command prompt.
It may be worth first trying the entry below.
```
bootrec.exe /fixboot
``` as this will do less damage to grub (I believe), however, I'm not certain that it will replace /boot/BCD.
If that runs without any errors, reboot and see what boots directly.
If Ubuntu boots, try running sudo update-grub again in the terminal and watch to see if the Windows Loader is picked up. 
Don't worry though, this is fixable :-)

---

### Post by Jetro on 2011-04-04
Hi again,

the sda2 &#8211; "Staesj" &#8211; is misleading. This is simlpy a NTFS partition I made back in the day to transfer files back and forth between Ununtu and Windows. :) So, there are naturally no boot files there.  I don't know why it would say "Boot sector type:  Windows Vista/7" &#8211; maybe because it's NTFS?

coffeecat: I didn't quite get that, I used GParted to create room for a Windows installation, installed Windows, and it seemed to work great. Should there be a separate partition for a boot section?

By the way, I have no CD/DVD-drive, I just grabbed the ISO and slammed it onto a USB disk. You ***may*** have heard this before (:P), but I don't have the repair disk, unless I can use the USB to repair something.

---

### Post by Quackers on 2011-04-04
Hmm, well for some reason sda2 has the boot flag set on it, and it contains one of the two necessary Windows boot files in it. Whether it was intended or not, it is currently effectively your Windows boot partition (sort of).

---

### Post by coffeecat on 2011-04-04
I'm with Quackers on this one. :) sda2 has to be your Windows boot partition because sda6 is a logical partition and Windows can't boot from a logical partition.

**EDIT**: sorry missed this. 

> **Jetro said:**
> coffeecat: I didn't quite get that, I used GParted  to create room for a Windows installation, installed Windows, and it  seemed to work great. Should there be a separate partition for a boot  section?

In effect, yes. I presume you pointed the Windows installer to sda6 for  installation. What the Windows installer does in this situation is think  to itself, "Oo-er. A logical partition. Is there a primary partition we  can grab for the boot files? Yes, there it is. We'll write the boot  files to it but we'll keep this a secret from the person running the  installer."

But in this case, it only wrote half the boot files.

Trust me! :) Windows has been doing this since XP days. It's done it to  me during some simulations I ran and it did it to me when doing an  in-earnest install for a relative. Grrr!

---

### Post by Jetro on 2011-04-04
Uh, okay, weird.
Anyhow, I tried [following your steps](http://support.microsoft.com/kb/927392), coffeecat, but instead of getting a list of OSes, it just said "Windows found problems with your computer startup options. Do you want to apply repairs and restart your computer?" I pressed **Yes**.
The next boot, it was exactly as before (GRUB 2, no Windows listed).

But anyway, what can I do to fix this problem? (I'm not even sure what the problem is :P) When I installed Win7 (when no GRUB was loaded), Windows booted and worked fine.

---

### Post by coffeecat on 2011-04-04
> **Jetro said:**
> But anyway, what can I do to fix this problem?

I'll do a bit of hunting around and get back to you. In the meantime, I added an edit to my previous post which you may have missed. It doesn't help, but adds a little background info.

---

### Post by Quackers on 2011-04-04
The Windows repair function can take up to 3 times to repair the installation - if it even finds it :-).
If you ignore that option and select the command prompt option and run the command quoted earlier, it may fix things. If not, there are other options.

---

### Post by coffeecat on 2011-04-04
Actually, yes, here's a thought. It's the BCD file(s) that is/are missing. Scroll down a bit on that link and have a look at the /RebuildBcd option. I think maybe that's what you need. The problem is getting it to write the BCD files to sda2, which is where they need to be. I'm not sure what that scanning all disks is about. I've never run bootrec /RebuildBcd.

---

### Post by Jetro on 2011-04-04
Okay, I don't know if you'll believe this, but here's what I did:

Since you mentioned that the "boot" flag was on sda2, I went into GParted, removed it, and added one to sda7 (where there was none before).

I then ran 'sudo update grub' and it detected sda2 as Win7 (which I removed?!)

When restarting, Win7/Vista showed on the GRUB menu. I chose it, it asked me to check the disk, once again referring to sda2. (Even though I installed it on sda6!)

I have no idea what I did, but Win7 now works, I am typing this from there.
Maybe it was installed in sda2 all along? It doesn't seem that way, seeing as the C drive is 35,8 GB.


I'm sorry I don't seem to listen to you, but I just wanted to give it a go before trying your options. :P Windows seem to be working again...

---

### Post by coffeecat on 2011-04-04
Whatever you've done, you've done something clever! :wink:

I *believe* grub can get Windows to boot without BCD being there, but the problem is getting grub-update to recognise the Windows OS without BCD there. Whatever, would you mind running the boot script again and posting the new RESULTS.txt? It will be interesting and educational.

Thanks! :)

---

### Post by Quackers on 2011-04-04
Lol, nice one. I would imagine, though, that somewhere there are Windows boot files which are not in a logical partition. Who knows? Not me :-)

---

### Post by Jetro on 2011-04-04
Heh, sure guys/gals. :D

I still don't get why it says "Windows Vista/7 loader (sda2)" in the GRUB, when it pretty clearly is in sda6. Anyway.

New boot script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               4,094   270,542,847   270,538,754   5 Extended
/dev/sda5               4,096   164,118,527   164,114,432  83 Linux
/dev/sda6    *    164,120,576   239,338,269    75,217,694   7 HPFS/NTFS
/dev/sda7         239,339,520   269,139,967    29,800,448  83 Linux
/dev/sda8         269,142,016   270,542,847     1,400,832  82 Linux swap / Solaris
/dev/sda2         270,542,848   312,580,095    42,037,248   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        28EF6B7158A8A24B                       ntfs       Staesj                        
/dev/sda5        6ded9daf-6cda-49e8-bb6e-7be687cc5c20   ext4       Ubuntu 10.04                  
/dev/sda6        1A2DF9F30F3157E5                       ntfs       Win7                          
/dev/sda7        5405d59d-41f3-4f64-a84c-88ec359a31f5   ext4                                     
/dev/sda8        c6342592-9b4a-4166-ac0e-848721b29694   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
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
search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-30-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 ro splash quiet vga=769  quiet splash nomodeset video=uvesafb:mode_option=1600x1200-16,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 25d4e3ac-04e2-41cd-b13b-12c8ef6d143e
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=25d4e3ac-04e2-41cd-b13b-12c8ef6d143e ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

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
UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dc4f3e6b-0b2d-4fc7-9b51-9691745922fd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.2GB: boot/grub/core.img
  15.3GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.32-29-generic
  24.9GB: boot/initrd.img-2.6.32-30-generic
  28.0GB: boot/vmlinuz-2.6.32-29-generic
  23.6GB: boot/vmlinuz-2.6.32-30-generic
  24.9GB: initrd.img
  34.4GB: initrd.img.old
  23.6GB: vmlinuz
  28.0GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5405d59d-41f3-4f64-a84c-88ec359a31f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 28ef6b7158a8a24b
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6ded9daf-6cda-49e8-bb6e-7be687cc5c20
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=6ded9daf-6cda-49e8-bb6e-7be687cc5c20 ro splash quiet vga=769 quiet splash nomodeset video=uvesafb:mode_option=1600x1200-16,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7719060e75a54a10
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=5405d59d-41f3-4f64-a84c-88ec359a31f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c6342592-9b4a-4166-ac0e-848721b29694 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 133.4GB: boot/grub/core.img
 131.4GB: boot/grub/grub.cfg
 123.5GB: boot/initrd.img-2.6.35-22-generic
 133.4GB: boot/vmlinuz-2.6.35-22-generic
 123.5GB: initrd.img
 133.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  7f f9 67 03 61 0c 26 13  a6 17 e6 1a 18 1d 54 1d  |..g.a.&.......T.|
00000010  8a 1b c5 18 13 17 6a 17  28 18 04 19 6e 1a 2a 1c  |......j.(...n.*.|
00000020  68 1d 6a 1d 55 1c ba 1a  ea 18 3a 16 b9 11 4d 0a  |h.j.U.....:...M.|
00000030  47 00 82 f5 6c eb 34 e2  c8 d8 45 cf 54 c6 0d bf  |G...l.4...E.T...|
00000040  f8 b8 f3 b2 0c ae 70 ab  f2 aa 5f aa c3 a7 e9 a3  |......p..._.....|
00000050  ce a0 b8 9f f8 9f 5b 9e  98 98 f8 8d 2a 86 c6 84  |......[.....*...|
00000060  99 89 40 93 37 a1 7e b2  3f c4 85 d2 11 dc 84 e4  |..@.7.~.?.......|
00000070  2c f0 65 fe 17 0a 74 10  17 14 b0 18 2c 1f 7a 26  |,.e...t.....,.z&|
00000080  11 2c dd 2f 60 32 3d 33  2b 33 ac 32 43 33 27 34  |.,./`2=3+3.2C3'4|
00000090  4e 33 88 2f ab 28 11 20  7b 16 c4 0d b3 06 4e 00  |N3./.(. {.....N.|
000000a0  64 f9 25 f1 8c e8 3d e1  16 db 5e d3 bd ca 19 c3  |d.%...=...^.....|
000000b0  00 be e3 ba 79 b8 a6 b8  61 bb 07 c0 6a c5 55 cb  |....y...a...j.U.|
000000c0  5d d2 29 da d7 e1 69 e9  46 f1 17 f9 18 00 22 06  |].)...i.F.....".|
000000d0  69 0d 25 16 e0 1e ce 26  41 2f 2c 3a fd 45 87 50  |i.%....&A/,:.E.P|
000000e0  16 5a d9 62 32 6a c4 6f  c2 73 25 76 19 77 e5 76  |.Z.b2j.o.s%v.w.v|
000000f0  b7 75 a4 73 4f 71 dd 6e  a8 6b b0 67 b2 62 5c 5b  |.u.sOq.n.k.g.b\[|
00000100  c6 51 d9 48 6e 40 1c 38  a9 31 90 2e e9 2d 51 2e  |.Q.Hn@.8.1...-Q.|
00000110  7e 2e 3f 2e 63 30 2b 35  44 39 5e 3a 40 3c 49 3f  |~.?.c0+5D9^:@<I?|
00000120  13 41 79 40 95 3e ba 3e  9f 3d be 36 71 26 4a 0c  |.Ay@.>.>.=.6q&J.|
00000130  b4 ee ed d2 90 ba 2b a9  85 a1 45 a3 c9 a9 29 af  |......+...E...).|
00000140  3c b3 bd b8 ad c2 29 d2  04 e5 f8 f9 46 0d 72 1b  |<.....).....F.r.|
00000150  23 22 98 20 be 1b ce 16  ee 12 c6 11 85 13 dd 15  |#". ............|
00000160  99 17 c8 19 bd 1d 7c 22  09 28 c5 2d aa 33 c2 3a  |......|".(.-.3.:|
00000170  1c 40 81 42 d6 43 ea 45  09 48 41 46 ee 3f ff 38  |.@.B.C.E.HAF.?.8|
00000180  bb 2f e3 21 ca 10 69 00  2d f2 0a e5 a0 d8 49 cd  |./.!..i.-.....I.|
00000190  ea c2 7c ba da b3 c6 af  6f af 2c b3 ef ba 67 c3  |..|.....o.,...g.|
000001a0  90 cb 92 d3 ac d9 9b dc  a4 dd 8a de d8 de 25 dd  |..............%.|
000001b0  d9 db af dc 0d de 96 df  82 e2 62 e7 ee ed 00 41  |..........b....A|
000001c0  02 00 83 fe ff ff 02 00  00 00 00 30 c8 09 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff ea 35  c8 09 36 bd 7b 04 00 00  |.......5..6.{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Quackers on 2011-04-04
Can you run the boot script again please?

---

### Post by Jetro on 2011-04-04
Done now! ;)

Thank you so much for your help :D

---

### Post by Quackers on 2011-04-04
You have moved the boot flag, but the two necessary Windows boot files are in sda2. This is why grub lists that partition. Those files obviously point to sda6 and so Windows is booting (despite your best efforts :-) )
I suspect problems may arise if ever Ubuntu (and grub) are removed. I'm not sure Windows will then boot with the boot flag where it is. I could be wrong though, it's happened before :wink:

---

### Post by coffeecat on 2011-04-04
> **Jetro said:**
> I still don't get why it says "Windows Vista/7 loader (sda2)" in the GRUB, when it pretty clearly is in sda6. Anyway.

Nope. look again :wink:

```

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr [COLOR=Red]/Boot/BCD[/COLOR]
```
Somewhere along the line you managed to restore /Boot/BCD to sda2, which is what Quackers and I were recommending. That's why it's working now. Your sda2 is now acting as a combination data store and boot partition.

By the way, the boot flag is irrelevant when grub is in control of booting. The boot flag is only needed by Windows and only when Windows code is in the mbr. The normal mbr Windows code simply looks for the partition with the boot flag and hands over the boot process to the boot files there. Grub does the handing over when it is present and the boot flag becomes superfluous.

Good luck! Glad it's working!

---

### Post by Jetro on 2011-04-04
Ahaa, so maybe it got fixed because I used "repair" from the Win7 USB, and then went to do a 'sudo update grub'? :D

[quote=Quackers]I suspect problems may arise if ever Ubuntu (and grub) are removed. I'm not sure Windows will then boot with the boot flag where it is. I could be wrong though, it's happened before [/quote]
I hopefully won't be removing Ubuntu for a while... :P

I still find it weird that the boot files somehow are in sda2, surely it must have been Windows (during the Windows installation) who put them there? :confused: Oh well, I have no knowledge of this whatsoever. I wish I could give you some extra beans or something.

---

### Post by coffeecat on 2011-04-04
> **Jetro said:**
> I still find it weird that the boot files somehow are in sda2, surely it must have been Windows (during the Windows installation) who put them there? :confused:

Indeed it was. If you missed my edit to my post at #8, there's an explanation there. But count yourself lucky! :) If you want to see the mischief that the Windows installer can get up to when it's in a *really* bad mood, have a look at my posts at #42 and #44 in this thread:

[http://ubuntuforums.org/showthread.php?t=1687873](http://ubuntuforums.org/showthread.php?t=1687873)

The Windows 7 installer will do the same as the Vista installer in the same situation. :-s

---

### Post by Jetro on 2011-04-04
I see. I did miss that edit.
So, basically, Windows is bad and if I accidentally didn't have the other NTSF partition, Windows would never be able to boot in the first place?

---

### Post by coffeecat on 2011-04-04
> **Jetro said:**
> I see. I did miss that edit.
So, basically, Windows is bad and if I accidentally didn't have the other NTSF partition, Windows would never be able to boot in the first place?

Yes. Windows cannot boot from a logical partition. Not never, not nohow. Which is why it will grab any primary partition it can find for that purpose. Whether that makes it bad or not, I really don't know! :)

But to be serious, this is why I like to create just one  partition before installing Windows, and then to install Windows first. I create the one partition, sda1 for simplicity, for Windows so that it can't argue and only get Ubuntu installed once Windows is happy - or as happy as it ever will be. :wink:

The one exception was with my relative's machine. I had set up:

sda1 - Windows C:
sda2 - shared NTFS data partition.
sda3 - extended partition with Ubuntu logical partitions.

All very tidy and easy, but something went wrong with Windows (as it does!) and we had to reinstall it. This was XP. I pointed the installer at sda1. You wouldn't think it could get it wrong, would you? But, yes it could. The ridiculous thing installed the boot files to sda2, and the rest of the system to sda1. Why? I have no idea. So now my relative has a load of Windows boot files mixed in with their personal data files. And Windows calls sda2 "C:", and its own partition "E:".

What a mess! :evil:

---

### Post by Jetro on 2011-04-04
Haha. It seems we encountered the same things, more or less.

And yes, I see we're thinking alike here, the tidiest thing be installing Windows first, on the enitre partition, and then add Ubuntu afterwards, because Ubuntu is \\:D/

Let me see if I got this right: 
I use GParted to wipe out all data on the hard drive, and then make the whole thing NTFS. Then I install Windows, and this is now a primary partition because of that? (I realise that Windows have "no choice" but to put the boot files there.) Whereas compartmentalising a drive afterwards makes whatever you create become a logical partition?

---

### Post by coffeecat on 2011-04-04
> **Jetro said:**
> Let me see if I got this right: 
I use GParted to wipe out all data on the hard drive, and then make the whole thing NTFS. Then I install Windows, and this is now a primary partition because of that? (I realise that Windows have "no choice" but to put the boot files there.) Whereas compartmentalising a drive afterwards makes whatever you create become a logical partition?

Not quite. What I would do if I was starting over fresh is to remove all partitions with Gparted (you don't have to wipe the data) and then make one primary NTFS partition large enough for Windows, but not using the whole drive. Simply leave unallocated space in the rest of the disk for use later. Install Windows to that single partition and then use Gparted from the live CD to create whatever extra partitions you need, including a NTFS data partition if you want one; Windows will pick this up when you next boot into it. Finally, you use the advanced/manual option in the installer to install Ubuntu to your pre-prepared partitions.

Straightforward. You don't have to resize the Windows partition and Windows is nicely contained in one partition because that's all it could see when you ran its installer. You have to treat it like a naughty child. What it can't see won't tempt it to get up to mischief. :wink:

---

### Post by Quackers on 2011-04-04
Very sound advice - and somewhat amusing, but correct :-)

---

### Post by QLee on 2011-04-04
[QUOTE=Jetro]...
Let me see if I got this right: 
I use GParted to wipe out all data on the hard drive, and then make the whole thing NTFS. Then I install Windows, and this is now a primary partition because of that? (I realise that Windows have "no choice" but to put the boot files there.) Whereas compartmentalising a drive afterwards makes whatever you create become a logical partition?[/QUOTE]

Well, if you're going to reinstall Windows to the entire disk there is no pressing need to delete any data first or reformat, just let Windows use the entire disk. Coffeecat has given you a sane approach for making your system a dual boot system.

When you partition, you choose whether to use a primary (if there are less than four already) or a logical in an extended partition. The number of primaries it already has determines what your choices are, not the time period of when you choose to do it (.ie. "afterwards").

---

### Post by Jetro on 2011-04-05
> **coffeecat said:**
> Not quite. What I would do if I was starting over fresh is to remove all partitions with Gparted (you don't have to wipe the data) and then make one primary NTFS partition large enough for Windows, but not using the whole drive. Simply leave unallocated space in the rest of the disk for use later. Install Windows to that single partition and then use Gparted from the live CD to create whatever extra partitions you need, including a NTFS data partition if you want one; Windows will pick this up when you next boot into it. Finally, you use the advanced/manual option in the installer to install Ubuntu to your pre-prepared partitions.

Straightforward. You don't have to resize the Windows partition and Windows is nicely contained in one partition because that's all it could see when you ran its installer. You have to treat it like a naughty child. What it can't see won't tempt it to get up to mischief. :wink:
Oh, I wouldn't do that, as I assume I have to create a memory swap partition and whatnot. Installing as I said above have (almost) always worked out for me, is there a significant benefit to installing it like you suggested?
It occurs to me that your procedure is probably safer and cleaner. But I don't feel confident enough about it, besides the Ubuntu installer seems to enjoy splitting up Windows and installing beside it. However, I'd love to learn how to do it properly, and will try to next time, if that is the best. There's bound to be a lot of guides out there.

> **QLee said:**
> When you partition, you choose whether to use a primary (if there are less than four already) or a logical in an extended partition. The number of primaries it already has determines what your choices are, not the time period of when you choose to do it (.ie. "afterwards").
So you can have more than one primary partition, but GParted by default creates logical partitions? I'm also a little lost about what exactly "extended" partition means, sorry. :(

---

### Post by coffeecat on 2011-04-05
> **Jetro said:**
> It occurs to me that your procedure is probably safer and cleaner. But I don't feel confident enough about it, besides the Ubuntu installer seems to enjoy splitting up Windows and installing beside it. However, I'd love to learn how to do it properly, and will try to next time, if that is the best. There's bound to be a lot of guides out there.

Be careful with the 10.10 installer "install alongside" option. It has a nasty design flaw that can lead to the Windows partition being erased. Manual partition isn't really that difficult, and it certainly gives you more control. Here's a good guide to start with:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

> **Jetro said:**
> So you can have more than one primary partition, but GParted by default creates logical partitions? I'm also a little lost about what exactly "extended" partition means, sorry. :(

An extended partition is simply a special type of primary partition whose sole purpose is to act as a container for a number of logical partitions. In a disc with an mbr partition table you are limited to four primary partitions only, or 3 primaries and one extended. Logical partitions are used to get around this limitation. 

Gparted doesn't create logical partitions by default. In fact if you start with an unallocated drive and want to create a partition, it will default to primary unless you tell it otherwise. You have to create an extended partition before you can create any logicals - of course.

You can distinguish logical partitions by their number. Partitions #1 to #4 can be primary (or extended) only. Logicals are numbered 5 and upwards.

---

