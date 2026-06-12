---
title: "Boot Problems - Encoder Mailbox Not Found?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by s0ysauce on 2010-12-18
Ubuntu is currently new to me. To be more precise, a week or two new to Ubuntu. I've only had experience in Windows and a tiny bit in Mac. Please be easy on me in terms of working around Ubuntu because I only know a little bit. 

I have installed Ubuntu 10.10 Maverick Meerkat Desktop Edition and do not have anything else installed on the main partition. Although I do plan on dual booting with XP in the future. 

The problem I seem to be having is that randomly on certain times when I boot up Ubuntu, and go into GRUB and edit the end of the main line by adding "noacpi," it takes me to a screen with some words and numbers with the word [OK] on the far right side. At the end of it, it says this "ivtv0:encoder mailbox not found." My computer at this point is frozen and I can not proceed any further or do anything except to forcefully shut the computer down. 
Before the words in the quote, a random string of numbers appear also and it seems to change every time. 
Luckily, sometimes I am able to log in and unfortunately, random times, I can not. If I do not add in at the end of the line in GRUB, the noacpi, then it always crashes. 

I've tried searching on Google and Ubuntu Forums but it doesnt seem as if anyone else is having this issue. I've heard from googling, that its related to MythTV? I've tried to see if its installed but its not. I've checked Synaptic and Software Center. 
I am completely at a loss. I dont know what to do. If there were solutions on google, I should have found them and fixed it by now but I couldn't. Posting on this forum is my last resort. 

Thanks![SIZE=2][FONT=Arial Black]
[/FONT][/SIZE]

---

### Post by Rubi1200 on 2010-12-19
Hi and welcome to the forums :)

In order to rule out booting problems, please start the computer with a LiveCD, choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by s0ysauce on 2010-12-19
Thank you for the help and the warm welcome. 

I did as you asked and got a RESULTS.txt file.

Here it is unedited:


                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf

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

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        daa32ee7-2393-4336-8f35-4843d07570a6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d0cf511a-778d-4d2b-906b-0ba3b6618272   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        560F-FD4E                              vfat       8GB OF SEXY                   
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr2         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdf1        /media/8GB OF SEXY       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1        /media/daa32ee7-2393-4336-8f35-4843d07570a6 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=daa32ee7-2393-4336-8f35-4843d07570a6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=daa32ee7-2393-4336-8f35-4843d07570a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa32ee7-2393-4336-8f35-4843d07570a6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
UUID=d0cf511a-778d-4d2b-906b-0ba3b6618272 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.4GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-23-generic-pae
  47.4GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.0GB: initrd.img
  47.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3f 71 f9 f4 e3 9f e0 a7  28 8c 2a 02 de 88 4e d4  |?q......(.*...N.|
00000010  8e e5 9f 13 66 10 dd 0f  11 dc 73 9f 46 df aa 59  |....f.....s.F..Y|
00000020  ca 14 f2 d4 dc a7 85 9c  d7 55 66 9a 13 e9 6d 62  |.........Uf...mb|
00000030  c3 07 a9 6f 84 49 e1 6e  80 db b6 a8 e8 18 57 1a  |...o.I.n......W.|
00000040  3d 32 17 50 ae 77 7a 52  69 fa 30 ce f2 d1 71 f7  |=2.P.wzRi.0...q.|
00000050  95 33 45 7d b2 4f 5d 43  b6 c7 ed 7a 4f 1d 9c 67  |.3E}.O]C...zO..g|
00000060  89 23 5c d4 4c 0d 63 46  03 7c 8b b0 9e 54 91 e8  |.#\.L.cF.|...T..|
00000070  a7 48 5e 54 1b 29 5d 4c  a5 cb 54 d6 4f 8e 18 55  |.H^T.)]L..T.O..U|
00000080  50 65 8a 76 c8 ba 34 61  6c a6 c3 3f 17 8a 1c 24  |Pe.v..4al..?...$|
00000090  17 72 71 9f 45 9c 50 30  1a 55 2c 21 cc ed 42 3b  |.rq.E.P0.U,!..B;|
000000a0  00 df 82 4c b2 f2 ee a6  88 da c4 e6 c4 22 10 d1  |...L........."..|
000000b0  30 39 5b b8 00 c1 69 88  e2 30 a4 f8 cc 34 49 79  |09[...i..0...4Iy|
000000c0  de f6 11 26 e8 fd 38 26  c4 50 89 42 e0 0c 1c 0e  |...&..8&.P.B....|
000000d0  9c 65 a2 a9 27 11 c6 6a  a0 cb 01 e0 52 23 e4 73  |.e..'..j....R#.s|
000000e0  d7 d2 93 99 fa 67 9c 60  e7 0b 42 6f 4f 68 f4 9e  |.....g.`..BoOh..|
000000f0  bf c4 9a e8 27 fe 06 df  f3 27 9c fa 94 1a 55 f9  |....'....'....U.|
00000100  f6 91 eb b1 3f 39 72 8a  fa 7a bb c3 91 99 c7 01  |....?9r..z......|
00000110  bf a7 a0 79 1c bb 42 4a  8a bc 07 cb e7 23 8f dc  |...y..BJ.....#..|
00000120  ef d8 55 a3 80 36 e3 cb  87 06 e4 91 11 5a 23 90  |..U..6.......Z#.|
00000130  6b 05 f2 a1 62 03 ae 6a  2a f0 bc 10 a9 55 f7 66  |k...b..j*....U.f|
00000140  37 4d 27 ab 92 e5 04 01  80 11 a6 2b be 71 7a 2f  |7M'........+.qz/|
00000150  35 a9 76 f3 8a 90 b1 85  dd 65 88 68 15 28 90 22  |5.v......e.h.(."|
00000160  37 5c 2d 59 2a 54 57 78  0a a6 4a 92 61 ac d2 ef  |7\-Y*TWx..J.a...|
00000170  37 34 ad c2 73 8d 37 be  6d e5 81 21 00 1d 83 80  |74..s.7.m..!....|
00000180  21 0c 14 cd da 08 cf 70  81 88 a3 53 d8 87 0c ae  |!......p...S....|
00000190  1d 08 85 b1 91 96 76 11  95 42 17 be f9 df 84 04  |......v..B......|
000001a0  cc bd 29 42 91 a3 84 0e  64 c6 99 1b 41 52 9b 43  |..)B....d...AR.C|
000001b0  95 6b 68 18 9d aa ab fc  a3 71 9c 62 8b 83 00 fe  |.kh......q.b....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde


```Once again, I really appreciate the help. Thanks Again!

---

### Post by Rubi1200 on 2010-12-19
Well, I don't see any obvious errors with the results.

What graphics card do you have installed and why have you been booting with the noapci parameter?

---

### Post by s0ysauce on 2010-12-19
The graphics card I have installed is an intel family chip-set. It's an integrated graphics card. Pretty crappy.


As for the noacpi parameter, I saw on some post about random freezes and crashes on ubuntu, that if you 

add that parameter, most if not all of the boot problems you would normally have would go away. So I tried it 

and it works some of the time. 

Surprisingly, today so far the computer has been booting up perfect compared to all of the other days.

Strange but awesome.

---

### Post by Rubi1200 on 2010-12-20
The next time you boot into Ubuntu, go to the terminal and post the output of the following command please:

```
lspci | grep VGA
```

Thanks.

Depending on the specific card, there are fixes that can help and would be better than the noacpi option.

---

### Post by s0ysauce on 2010-12-20
Here it is:

```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
```

---

