---
title: "Windows gone..."
date: 2011-04-07
forum: New to Ubuntu
---

### Post by gupti on 2011-04-07
I installed ubuntu 10.10 on my friends pc, formatting 30gb for ubuntu. Once installed, windows disappered along with its files. There is a backed up ghost copy on another drive. What can I do to get windows back.

---

### Post by Mark Phelps on 2011-04-07
I presume when you say "ghost", you mean Symantec/Norton Ghost, right?

Been a while since I used that (I'm a Macrium Reflect fan), but it used to come with a boot CD, and maybe today, a boot USB.

Either way, you boot using it, select the Ghost image you want to restore (from the backup drive), and do a restore.

If you don't have Ghost boot media, that's a major problem -- and you may have to end up buying it to restore the image.

Sorry, but one of the first things you do when imaging any PC is ensure that you have a way of restoring the image should the machine's OS get totally wiped out.

---

### Post by natravis on 2011-04-07
Start by following the directions in this post:

[http://ubuntuforums.org/showpost.php?p=10579411&postcount=2](http://ubuntuforums.org/showpost.php?p=10579411&postcount=2)

---

### Post by gupti on 2011-04-07
This is a bit long but:
```
[FONT=monospace]     
 Boot Info Script 0.55    dated February 15th, 2010                    
  
============================= Boot Info Summary: ==============================
  
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
  
sda1: _________________________________________________________________________
  
    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM
  
sda2: _________________________________________________________________________
  
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
  
sda3: _________________________________________________________________________
  
    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM
  
sda4: _________________________________________________________________________
  
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
  
sda5: _________________________________________________________________________
  
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
  
sdb1: _________________________________________________________________________
  
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
  
sdb5: _________________________________________________________________________
  
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
  
=========================== Drive/Partition Info: =============================
  
Drive: sda ___________________ _____________________________________________________
  
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
  
Partition  Boot         Start           End          Size  Id System
  
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   139,569,596   139,489,272  83 Linux
/dev/sda3         149,340,240   156,232,124     6,891,885  db CP/M / CTOS / ...
/dev/sda4         147,386,366   149,340,159     1,953,794   5 Extended
/dev/sda5         147,386,368   149,340,159     1,953,792  82 Linux swap / Solaris
  
  
Drive: sdb ___________________ _____________________________________________________
  
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
  
Partition  Boot         Start           End          Size  Id System
  
/dev/sdb1              16,065   390,716,864   390,700,800   f W95 Ext d (LBA)
/dev/sdb5              16,128   390,716,864   390,700,737   7 HPFS/NTFS
  
  
blkid -c /dev/null: ____________________________________________________________
  
Device           UUID                                   TYPE       LABEL                         
  
/dev/loop0                                              squashfs                                 
/dev/sda1        07D6-0908                              vfat       DellUtility                   
/dev/sda2        457da2bd-101d-4e68-b95c-281af84e8495   ext4                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        41dfcccb-d94e-476b-89fc-da77adeacf6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        D06CB7CA6CB7A99C                       ntfs       DATA                          
/dev/sdb: PTTYPE="dos" 
  
============================ "mount | grep ^/dev  output: ===========================
  
Device           Mount_Point              Type       Options
  
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
  
  
=========================== sda2/boot/grub/grub.cfg: ===========================
  
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=457da2bd-101d-4e68-b95c-281af84e8495 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=457da2bd-101d-4e68-b95c-281af84e8495 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 457da2bd-101d-4e68-b95c-281af84e8495
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
  
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 07d6-0908
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
  
=============================== sda2/etc/fstab: ===============================
  
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=41dfcccb-d94e-476b-89fc-da77adeacf6f none            swap    sw              0       0
  
=================== sda2: Location of files loaded by Grub: ===================
  
  
  21.6GB: boot/grub/core.img
  69.0GB: boot/grub/grub.cfg
   4.7GB: boot/initrd.img-2.6.35-22-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
   4.7GB: initrd.img
    .4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
  
Unknown BootLoader  on sda4
  
00000000  7a 0e 4f fc 5d 0b f3 fc  7f 08 55 fd 89 05 d2 fd  |z.O.].....U.....|
00000010  29 01 0b fd ea fd 45 fc  82 fc 2f fb 68 fd d1 f9  |).....E.../.h...|
00000020  55 fe 82 f8 17 fe 75 f7  e0 fd 43 f8 64 fc 3e f9  |U.....u...C.d.>.|
00000030  fd f9 40 fa 75 f8 b6 fa  1d f8 90 fb 26 f9 fc fc  |..@.u.......&...|
00000040  98 fa 33 fd 44 fc ab fc  ca fc 08 fc c5 fc d7 fa  |..3.D...........|
00000050  51 fe 73 f9 d3 ff d8 fa  a7 ff ea fd 15 ff c6 01  |Q.s.............|
00000060  28 fe cf 04 c4 fb cc 06  6e f9 03 08 0f f9 69 08  |(.......n.....i.|
00000070  3f f9 d1 09 19 fa 56 0b  7c fb 7d 0c b8 fb 8b 0d  |?.....V.|.}.....|
00000080  d1 fa c3 0e 5c fa 1d 0f  60 f9 b8 0d 26 fa 47 0c  |....\...`...&.G.|
00000090  5c fb 35 0a 09 fd 6a 08  01 ff 8d 06 e5 fe ad 04  |\.5...j.........|
000000a0  56 fc 77 03 59 fb 7e 02  26 fd 36 01 5a fd a5 ff  |V.w.Y.~.&.6.Z...|
000000b0  2d fb 93 fd 45 f8 b3 fb  b4 f4 55 fa 47 f2 d8 f9  |-...E.....U.G...|
000000c0  9f f1 a9 f9 e3 f0 25 fa  97 f1 11 fb d6 f2 0f fb  |......%.........|
000000d0  6d f3 5d fb d2 f3 1e fb  86 f4 a4 f9 d4 f3 24 f7  |m.]...........$.|
000000e0  1e f4 ca f4 7f f4 a3 f2  70 f4 e7 f2 97 f4 69 f3  |........p.....i.|
000000f0  b1 f4 44 f4 5b f4 8f f4  e5 f3 bd f5 9b f2 34 f6  |..D.[.........4.|
00000100  ca ef ca f6 69 ee 26 f7  23 ed 6a f6 51 ec e8 f5  |....i.&.#.j.Q...|
00000110  6d ec 2d f4 19 ec 56 f2  79 eb ff ef 34 ea 03 ef  |m.-...V.y...4...|
00000120  f4 e8 dd ee 70 e8 3d ef  2a e9 2f ef 58 e9 64 ef  |....p.=.*./.X.d.|
00000130  01 ea 62 ef 28 ea c1 ef  da e8 0d f0 ff e7 46 ef  |..b.(.........F.|
00000140  69 e7 ea ee e5 e4 c7 ed  8e e2 7d eb 1c e2 ef e8  |i.........}.....|
00000150  de e2 59 e7 79 e4 6c e6  ee e6 32 e6 0c ea 2b e7  |..Y.y.l...2...+.|
00000160  00 ec a7 e7 93 ec b6 e7  af ed 9d e8 59 ee bf e9  |............Y...|
00000170  10 ee a6 ea d6 ed 29 ea  8b ef fb e9 17 f2 5f e9  |......)......._.|
00000180  d0 f4 b2 e7 00 f8 37 e7  8e f9 42 e8 6a fb af ea  |......7...B.j...|
00000190  ce fb 65 ec a7 fa 33 ed  43 fb d3 ee 94 fb 22 f1  |..e...3.C.....".|
000001a0  f7 fb e9 f4 86 fc e0 f7  95 fc d1 fa 1c fd a1 fc  |................|
000001b0  1b 00 5c fe a2 01 8d 00  18 01 b0 03 e3 00 00 fe  |..\.............|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
  
Unknown BootLoader  on sdb1
  
00000000  1e fb 0e 80 6f 03 51 dc  fd de c9 18 56 ce 46 b7  |....o.Q.....V.F.|
00000010  4f 5f 75 ed 71 b3 1c 45  82 16 c6 30 0c a2 85 3b  |O_u.q..E...0...;|
00000020  1b 2a 0f 5b 09 36 6d f3  b8 70 11 83 c7 5c 0d 73  |.*.[.6m..p...\.s|
00000030  8d 15 5c 59 4b ec fd c3  ec c5 e1 8b 75 f9 f1 46  |..\YK.......u..F|
00000040  9e f2 28 49 16 c7 a1 ed  88 44 21 9b 0f f5 01 88  |..(I.....D!.....|
00000050  e8 65 9f 10 c2 99 6c e2  6a df 6c 7f cd 52 7f 76  |.e....l.j.l..R.v|
00000060  dd c8 e4 ea 72 36 c7 59  4f 6c c7 b0 5d 79 78 6b  |....r6.YOl..]yxk|
00000070  f6 60 f7 aa e0 5f 9a d3  86 e6 3a 36 f8 70 7c d2  |.`..._....:6.p|.|
00000080  69 1a f4 06 a0 9e 03 ea  14 10 b5 4a 1b 84 2a 64  |i..........J..*d|
00000090  14 f9 cd a5 ba bf 7b 56  6b 62 6a 57 b6 67 13 30  |......{VkbjW.g.0|
000000a0  18 19 97 fb b0 a5 d5 f2  86 2f 9e 3e b4 86 5f ea  |........./.>.._.|
000000b0  23 1d 09 7f 98 f6 00 ea  48 52 ee e2 fb f5 34 c7  |#.......HR....4.|
000000c0  1b 9c c6 01 a4 a9 29 99  f3 38 e3 e2 6b 66 60 eb  |......)..8..kf`.|
000000d0  46 13 e9 3b 5b 1a 70 7d  3b bb 8e 1c 45 94 7a f3  |F..;[.p};...E.z.|
000000e0  45 8f 58 73 c8 2c 0d 8f  86 71 24 7b 2d f9 fe 3f  |E.Xs.,...q${-..?|
000000f0  30 b6 1c 64 bf 28 c8 b6  c3 e1 fe cc b0 ed 0c b5  |0..d.(..........|
00000100  9b 6c 77 51 a6 99 c8 12  14 81 8b fc 8e c2 62 b7  |.lwQ..........b.|
00000110  3e ac 31 8d e7 8f 02 34  ed f2 cc 14 79 1a d0 b0  |>.1....4....y...|
00000120  16 5a ec 2f 72 7d 59 5b  33 8e 23 d7 16 43 41 09  |.Z./r}Y[3.#..CA.|
00000130  7f e5 70 16 45 00 21 25  a7 6c e2 68 d9 4e ba f2  |..p.E.!%.l.h.N..|
00000140  72 3f 59 3d ef 10 62 1f  18 45 80 0d b9 16 20 30  |r?Y=..b..E.... 0|
00000150  fb ec bb 38 cd d6 aa d2  9f ba d6 4f a1 1b 27 2a  |...8.......O..'*|
00000160  f4 24 85 cf e7 00 77 5c  1a 57 5a f3 58 c3 50 ac  |.$....w\.WZ.X.P.|
00000170  be c6 da 08 61 8f 24 17  ff c3 87 ae a2 68 63 6b  |....a.$......hck|
00000180  d8 1a 87 59 9c fa e2 ff  ca 5f 23 59 0b 0c cd c5  |...Y....._#Y....|
00000190  1a f6 82 c9 8c b6 b3 47  01 6d d0 5a 38 8b b0 ac  |.......G.m.Z8...|
000001a0  b3 ea 48 45 72 fe 3f b1  e3 88 b3 94 19 d3 cc c1  |..HEr.?.........|
000001b0  da cc 4c 60 cc a3 4c 9a  7b 1c 1c 40 84 65 00 01  |..L`..L.{..@.e..|
000001c0  01 01 07 fe ff ff 3f 00  00 00 c1 9e 49 17 00 00  |......?.....I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
  
[/FONT]
```

---

### Post by sydbat on 2011-04-07
Reinstall GRUB via the LiveCD. Follow directions here - [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Razorback on 2011-04-07
And it looks like Windows is still there, don't panic.

---

### Post by Dutch70 on 2011-04-07
It looks to me like windows is installed in a logical partition(sdb5). 
Unless I'm missing something.

Did you previously have another version of windows installed where Ubuntu is now?

---

### Post by gupti on 2011-04-07
The sdb was a extended partition with Norton Ghost on it, Windows was on sda. Does this help?

---

### Post by Dutch70 on 2011-04-07
> **gupti said:**
> The sdb was a extended partition with Norton Ghost on it, Windows was on sda. Does this help?

Well, it's def a good thing. :)
Hopefully the directions you've got will work.

---

### Post by gupti on 2011-04-07
It says that Windows is installed on /dev/sdb, but it was installed on /dev/sda, so what does this mean?:```
[FONT=monospace] Windows is installed in the MBR of /dev/sdb
[/FONT]
```

---

### Post by LawrenceVern on 2011-04-07
Hi all! Well I'm guptis friend. So as I understand it the windows is still on my hard drive, it just cant be acceseed. So what exactly should i be doing to get my files back? 
btw, the ghost was an image of like 4 years ago when i first installed windows, I want my files back :)

---

### Post by Dutch70 on 2011-04-07
Hi and welcome to UF

 You should be able to boot up the live cd/usb and access your files with Nautilus. The list on the left should show your windows file system. I'll include a pic, even though mine is a little more complicated. You can see by where my pointer is, that is my windows partition. That's if you just want to back up your files for now.

---

### Post by Quackers on 2011-04-07
It also seems that you may have a recovery partition (either sda1 or sda3 - or both). If you can find out how to access that partition (probably by pressing a key at boot (Windows boot, that is) you can probably get Windows back - but not your files. If the recovery utility works it will restore your system back to how it was the day you got it. This will almost certainly over-write Ubuntu, but you can put that back afterwards - but not the same way it was done the first time! :-)
Don't use the "install alongside other operating system" option in the 10.10 installer! It eats Windows!

---

### Post by gupti on 2011-04-07
I see... I used the 'along side' option, then used the advanced feature to take 30gb out of the /dev/sda HD... I wasn't used to that installer since I used the 9.10 for my PC, and I thought it was a good built in feature...

---

### Post by Quackers on 2011-04-07
Yes, it should be. In fact it was a good option in the 10.04 installer, however the 10.10 installer dropped the ball somewhat. It has been changed for 11.04, but care still needs to be taken in 10.10

---

### Post by Sef on 2011-04-07
Drive: sda ___________________ _____________________________________________________
  
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
  
Partition  Boot         Start           End          Size  Id System
  
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   139,569,596   139,489,272  83 Linux
/dev/sda3         149,340,240   156,232,124     6,891,885  db CP/M / CTOS / ...
/dev/sda4         147,386,366   149,340,159     1,953,794   5 Extended
/dev/sda5         147,386,368   149,340,159     1,953,792  82 Linux swap / Solaris
  
  
```
Drive: sdb ___________________ _____________________________________________________
  
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
  
Partition  Boot         Start           End          Size  Id System
  
/dev/sdb1              16,065   390,716,864   390,700,800   f W95 Ext d (LBA)
/dev/sdb5              16,128   390,716,864   390,700,737   7 HPFS/NTFS
```

I believe that the problem is that Windows should be one the first primary partition.

---

### Post by LawrenceVern on 2011-04-09
any idea on how to make it the primary partion?

---

### Post by Dutch70 on 2011-04-09
What he is referring to is the same thing I mentioned in post# 7. 

gupti said [I]"The sdb was a extended partition with Norton Ghost on it, Windows was on sda. 
[/I]
(according to oldfred) 
If you have windows installed into a primary partition, it's possible to boot another version of windows from a logical partition, but when you delete windows from the primary prtn, the one in the logical prt. won't boot anymore.

Unfortunately there is no way to change a logical partition to a primary AFAIK.

My suggestion...
Recover your files according to post# 12, then refer to post# 13.

---

