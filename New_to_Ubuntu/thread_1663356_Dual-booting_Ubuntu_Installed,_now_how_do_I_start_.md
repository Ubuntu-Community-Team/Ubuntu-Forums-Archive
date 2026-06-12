---
title: "Dual-booting Ubuntu: Installed, now how do I start Ubuntu?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Sturmdolch on 2011-01-09
Hello.

I am trying to dual-boot with Ubuntu and Windows 7 on my laptop. It only has one hard drive, so it's a bit different from when I installed both on my desktop with two separate ones.

I installed windows and set aside half of the disc. Then I restarted and installed Ubuntu on the other half. Everything looked like it went well.

But when I start up my computer, it boots into Windows 7 automatically. There is no grub or anything. It's as if Ubuntu does not exist.

What should I do? 

Thank-you.

---

### Post by wilee-nilee on 2011-01-09
> **Sturmdolch said:**
> Hello.

I am trying to dual-boot with Ubuntu and Windows 7 on my laptop. It only has one hard drive, so it's a bit different from when I installed both on my desktop with two separate ones.

I installed windows and set aside half of the disc. Then I restarted and installed Ubuntu on the other half. Everything looked like it went well.

But when I start up my computer, it boots into Windows 7 automatically. There is no grub or anything. It's as if Ubuntu does not exist.

What should I do? 

Thank-you.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between. This will give the blueprint of the whole setup we need.

---

### Post by Sturmdolch on 2011-01-09
Here goes:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   312,571,903   312,365,056   7 HPFS/NTFS
/dev/sda3         312,573,950   625,141,759   312,567,810   5 Extended
/dev/sda5         312,573,952   320,571,391     7,997,440  82 Linux swap / Solaris
/dev/sda6         320,573,440   625,141,759   304,568,320  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C94C39994C373D4                       ntfs       System Reserved               
/dev/sda2        6646CF0846CED7C7                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        459ae63a-d3a4-448d-b08a-c77d0853a52b   swap                                     
/dev/sda6        9bc49dd0-31b6-4109-a053-0cb152fa3b85   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20FC-5A7B                              vfat       HP v100w                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/HP v100w          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9bc49dd0-31b6-4109-a053-0cb152fa3b85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9bc49dd0-31b6-4109-a053-0cb152fa3b85 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9bc49dd0-31b6-4109-a053-0cb152fa3b85
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5c94c39994c373d4
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
UUID=9bc49dd0-31b6-4109-a053-0cb152fa3b85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=459ae63a-d3a4-448d-b08a-c77d0853a52b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 166.4GB: boot/grub/core.img
 303.8GB: boot/grub/grub.cfg
 304.5GB: boot/initrd.img-2.6.35-22-generic
 166.4GB: boot/vmlinuz-2.6.35-22-generic
 304.5GB: initrd.img
 166.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4e ef 4b 83 f2 a5 66 89  dd e5 79 00 00 d3 2f ab  |N.K...f...y.../.|
00000010  03 99 28 13 0d 16 f0 40  66 62 19 7e 50 10 98 18  |..(....@fb.~P...|
00000020  72 80 83 f3 0f 83 63 01  04 03 0a c3 f4 35 30 23  |r.....c......50#|
00000030  a3 39 10 30 e0 00 a1 51  8c 07 18 08 49 8e 13 19  |.9.0...Q....I...|
00000040  a8 88 58 75 17 4c a8 d8  c2 85 4c e4 d8 c2 15 cd  |..Xu.L....L.....|
00000050  9d 14 d1 0d 0c 2c 08 c3  05 8c 4d 3c cc 1d 4c 81  |.....,....M<..L.|
00000060  ec cb 19 81 d3 80 02 d3  83 41 08 9c 34 23 e3 05  |.........A..4#..|
00000070  31 4c b3 2f 55 31 d0 73  1a 6d 31 32 e3 18 67 30  |1L./U1.s.m12..g0|
00000080  60 94 43 31 04 10 e9 33  12 2e 01 32 98 48 d1 8c  |`.C1...3...2.H..|
00000090  16 18 99 b1 86 08 5c 12  f7 3d 66 34 69 8a 40 5d  |......\..=f4i.@]|
000000a0  f0 bc 23 1a 3d 0a 12 9d  7f 1b c4 a0 85 20 46 82  |..#.=........ F.|
000000b0  24 a2 5f 8c 19 70 c0 0e  31 77 91 a1 2a 5d f8 12  |$._..p..1w..*]..|
000000c0  4f 4b 8c 37 09 8c cb a8  1d 7a 49 75 0f e1 7e fe  |OK.7.....zIu..~.|
000000d0  ff b7 bb 95 3d c9 d9 7f  26 e8 ad d6 e5 bb df 87  |....=...&.......|
000000e0  7f 2e 63 ce 5f c3 7f df  de b1 ef ff fe bf ff ff  |..c._...........|
000000f0  f0 fb ba df ff ef fb 9e  b5 8e 18 67 df fc 6f 04  |...........g..o.|
00000100  00 6e 72 7d 1f 6c b8 00  0f 18 37 8c 74 a8 79 84  |.nr}.l....7.t.y.|
00000110  4f e0 30 21 8f cf 40 a0  81 2a 70 1c c0 0b 98 16  |O.0!..@..*p.....|
00000120  b0 c0 44 c3 41 a0 35 f3  1c a5 0a cc 71 02 a9 41  |..D.A.5.....q..A|
00000130  93 25 55 ec b4 2e 2c 79  d9 83 42 60 c2 19 01 66  |.%U...,y..B`...f|
00000140  c0 33 72 32 3a 0c 50 b0  00 50 56 b3 e5 10 ff c1  |.3r2:.P..PV.....|
00000150  54 66 32 29 db 10 05 c8  65 ed 08 2f 98 84 46 d0  |Tf2)....e../..F.|
00000160  c8 31 99 9b 5a 14 0e 6a  1c 18 cb a6 7d 51 b0 3e  |.1..Z..j....}Q.>|
00000170  02 7a 86 48 e2 60 50 8f  17 03 74 30 c6 87 8f 0b  |.z.H.`P...t0....|
00000180  e8 3d 19 08 09 7e 6a 80  d2 55 30 19 f2 e7 10 02  |.=...~j..U0.....|
00000190  61 84 64 aa 4c 11 8c 09  d6 68 60 a0 83 98 32 d6  |a.d.L....h`...2.|
000001a0  5b 8a ed ae 5f 89 4b ac  54 95 4b 39 6a 6f eb 57  |[..._.K.T.K9jo.W|
000001b0  ed 9f c3 59 7e 7f 96 b9  4f 85 8f c3 5b b1 00 fe  |...Y~...O...[...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 7a 00 00 fe  |............z...|
000001d0  ff ff 05 fe ff ff 02 08  7a 00 00 60 27 12 00 00  |........z..`'...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-01-09
Windows is installed in the MBR of /dev/sda

We want grub here instead, boot the Ubuntu cd and run these two commands from the terminal. 
```
sudo mount /dev/sda6 /mnt
```
then this one
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot to the Ubuntu install and run in its terminal.
```
sudo update-grub
```

---

### Post by Sturmdolch on 2011-01-09
Alright, yes, that did it! Thank-you very much.

---

### Post by wilee-nilee on 2011-01-09
> **Sturmdolch said:**
> Alright, yes, that did it! Thank-you very much.

Cool enjoy.:)

---

