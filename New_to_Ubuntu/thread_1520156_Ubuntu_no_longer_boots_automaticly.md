---
title: "Ubuntu no longer boots automaticly"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by wigglestix on 2010-06-29
Ok so today i was experimenting with freebsd and decided to put a small partition on my laptop just to grasp a better understanding. I used gparted to add a 50 gb partition for freebsd and proceded to install freebsd on this partition but because i was in such a hurry i selected the boot automaticly option and now i can not boot ubuntu.I tried changing the flags in gparted to boot ubuntu but i get an error saying there is no os so i went back and checked that my ubuntu partition was still there and it was.
So i guess my questio is how would i make ubuntu back to the default os and just have freebsd as an option in GRUB.I know this is not directly related to ubuntu but i am in great need of help because i need to acess my ubuntu desktop asap.

Any help is greatly appreciated.

Kristian

---

### Post by Rubi1200 on 2010-06-29
Hi,
you need to get hold of, preferably, an Ubuntu CD so you can boot the computer.

If you have one, start the computer and choose the option to Try Ubuntu not install.

Then click on the link in my signature and follow the instructions there.

Post the results back here and don't forget to wrap the text with the # tag.

Hopefully someone will then come along and help you resolve this.

Hang in there!

:-)

---

### Post by wigglestix on 2010-06-29
Thank you very much for the quick reply.I am allready booted in a live cd version of ubuntu, heres the output from that script.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
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

/dev/sda1         102,398,310   471,363,164   368,964,855  83 Linux
/dev/sda2         471,816,190   488,396,799    16,580,610   5 Extended
/dev/sda5         471,816,192   488,396,799    16,580,608  82 Linux swap / Solaris
/dev/sda3    *             63   102,397,679   102,397,617  a5 FreeBSD


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        583e857b-3e6e-4718-a53c-233f895e00f1   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3                                               ufs                                      
/dev/sda5        ca456bb4-2ab0-4bcf-a925-e0d7ca966187   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         2CC0-AF04                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /media/2CC0-AF04         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=583e857b-3e6e-4718-a53c-233f895e00f1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=583e857b-3e6e-4718-a53c-233f895e00f1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=583e857b-3e6e-4718-a53c-233f895e00f1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=583e857b-3e6e-4718-a53c-233f895e00f1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 583e857b-3e6e-4718-a53c-233f895e00f1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=583e857b-3e6e-4718-a53c-233f895e00f1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca456bb4-2ab0-4bcf-a925-e0d7ca966187 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 192.1GB: boot/grub/core.img
 194.3GB: boot/grub/grub.cfg
 192.1GB: boot/initrd.img-2.6.32-21-generic
 192.8GB: boot/initrd.img-2.6.32-22-generic
 192.1GB: boot/vmlinuz-2.6.32-21-generic
  58.1GB: boot/vmlinuz-2.6.32-22-generic
 192.8GB: initrd.img
 192.8GB: initrd.img.old
  58.1GB: vmlinuz
  58.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 51 87 12 49 d9 9a da  f1 f1 67 f0 c3 4a 78 b6  |.Q..I.....g..Jx.|
00000010  7e 08 7a 0d 97 f9 19 66  42 ac 7a f3 fa bf 7a 6f  |~.z....fB.z...zo|
00000020  68 73 d6 f4 f7 e0 a5 10  e1 38 f4 81 f9 ba b1 a2  |hs.......8......|
00000030  14 6f 53 3c 90 f1 05 68  1c 7f 2e 3c 08 8b 22 6a  |.oS<...h...<.."j|
00000040  15 40 0b 81 4a d7 95 ae  3a a5 52 aa 0e b7 35 f9  |.@..J...:.R...5.|
00000050  5b 65 17 d5 af 35 b2 29  de 3b db 84 ab 4b 39 3f  |[e...5.).;...K9?|
00000060  ca 00 9d 57 da 5e f3 c2  98 59 19 f7 a1 63 56 9b  |...W.^...Y...cV.|
00000070  21 d2 4d 1a ca 1c 86 85  86 37 a1 6c 83 99 56 14  |!.M......7.l..V.|
00000080  80 6f b9 f9 5a 12 1e 3e  13 f6 6d fe 68 03 f9 92  |.o..Z..>..m.h...|
00000090  54 8c be 82 83 23 0b b6  0c 37 c5 e9 6c c6 35 e1  |T....#...7..l.5.|
000000a0  56 0b 69 9e 7d 8c ec d4  7f ef d9 92 f8 56 32 aa  |V.i.}........V2.|
000000b0  01 6a 38 68 30 c0 45 65  00 e4 25 1c 5c 5f 89 3e  |.j8h0.Ee..%.\_.>|
000000c0  2a 64 28 fb 17 a6 26 94  b3 5b 17 fa 45 f1 d3 ba  |*d(...&..[..E...|
000000d0  10 5b 56 b3 a2 b4 61 54  61 52 26 3d c6 c0 2d b4  |.[V...aTaR&=..-.|
000000e0  87 e5 8f 58 b3 bb ce 59  bf b5 4a c0 8d ab 5e b9  |...X...Y..J...^.|
000000f0  7e 8a 80 46 80 a4 27 d0  5e 02 10 f6 fd 76 77 39  |~..F..'.^....vw9|
00000100  b4 ff f0 13 b4 3b 32 86  4d 53 a8 3d 90 60 a3 55  |.....;2.MS.=.`.U|
00000110  1f 8d c6 04 a1 47 86 69  f5 4b f3 c5 e0 47 2b 13  |.....G.i.K...G+.|
00000120  ba 9b 5b 3b 6a b8 29 67  17 1f 86 50 51 db 3c 96  |..[;j.)g...PQ.<.|
00000130  c2 69 a2 12 16 f4 73 3b  b8 f9 6b 55 72 9b 2a a8  |.i....s;..kUr.*.|
00000140  fb 58 49 5d db de 85 e2  bf dd 1c 7e 61 95 a6 42  |.XI].......~a..B|
00000150  e1 96 46 ef 9c b2 87 aa  1f 05 ce 00 f7 06 eb 4d  |..F............M|
00000160  32 2e 5d 4c cb eb e7 61  7f ca 36 58 08 dd 20 d1  |2.]L...a..6X.. .|
00000170  15 2e 49 5f ae 62 b4 3a  fe e5 28 f5 ab 44 04 8b  |..I_.b.:..(..D..|
00000180  50 12 83 bd 9e 32 b4 62  2e 13 88 8c 8e de 57 83  |P....2.b......W.|
00000190  bc 4a 38 50 13 ca 1d d9  d1 c8 b1 c4 8b e4 74 bf  |.J8P..........t.|
000001a0  91 26 a2 2d f3 11 74 f9  3d a4 70 89 ea c4 3a 4d  |.&.-..t.=.p...:M|
000001b0  1c 57 14 37 94 b6 12 6b  ea 28 3c 27 71 40 00 fe  |.W.7...k.(<'q@..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 fd 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea 00 00  ff ff bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200


```

---

### Post by Rubi1200 on 2010-06-29
Hi Kristian,
You will have to wait for one of the core experts to come along and advise you regarding a solution. 

Normally, the solution would be to re-install GRUB2 to the MBR, but I see that FreeBSD uses a different type of file-system so I cannot tell you whether that would work. 

Also, you have Testdisk installed in the MBR and I don't know what difference that would make.

Hang in there and hopefully someone can lead you through this soon.

Good luck!

:-)

---

### Post by wigglestix on 2010-06-29
Ok well if i just want to get my ubuntu desktop working again would i just have to reinstall grub or is it just not that simple because i honestly dont care much about freebsd and am more concerned about getting my main desktop back.

---

### Post by sgosnell on 2010-06-29
Ubuntu only boots automatically if it's the only installed OS.  If there is any other OS installed, it always displays the boot menu to let you select which OS you want to boot.  You can change the default OS and the timeout before the default is booted.  There are several threads detailing how to do this.

---

### Post by wilee-nilee on 2010-06-29
Follow this link to put grub2 back in the mbr and delete the freebsd partition, all of this done from a live Ubuntu cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by wigglestix on 2010-06-29
Thank you very much everybody i will me trying your suggestions right now.

---

### Post by Jakiejake on 2010-06-29
If you are using GRUB to boot try Start-up manager

---

### Post by wigglestix on 2010-06-29
AHA!!!....I sucessfull reinstalled grub and have my ubuntu desktop back!! Im prety sure i just woke the whole neighbourhood with all the screams of excitement.

---

### Post by Jakiejake on 2010-06-29
> **wigglestix said:**
> AHA!!!....I sucessfull reinstalled grub and have my ubuntu desktop back!! Im prety sure i just woke the whole neighbourhood with all the screams of excitement.

LOL! :lolflag::lolflag::lolflag:

---

### Post by wigglestix on 2010-06-29
Ok so thanks everybody for the help its greatly appreciated you have no idea ho relived i am that i do not have to do a fresh install once again!

---

