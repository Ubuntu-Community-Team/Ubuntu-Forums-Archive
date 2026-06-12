---
title: "Forgot to select bootable for root during install"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by mspoden on 2011-01-23
Note: I already posted this in linux mint forums, but i hear you get faster responses on this forum. So i am giving it a shot.

I humbly request audiences from the great wisdom of linux mint gurus. 

Now  that the formality is out of the way, i am pretty sure i just made the  lamest linux mistake ever. After doing a google search and searching the  forum i am pretty sure i forgot to select the bootable option when i  created the root partition. So guess what, it doesn't boot.

I  have done linux installs before but always stand alone on some old dell  that someone else was trying to throw away. This is my first dual boot  with windows 7. Actually this is my second dual boot, my first i tried I  royally messed up by trying to partition with partition magic before  putting in the install cd. Long story short only a quarter of the drive  ended up being accessible with either linux or w7. 

My impatience  on the second install led me to the current error. My question for you  erudites is this: is there anyway to go back and make it bootable  without a wipe and reinstall? I am trying to avoid this because i had to  use the UBCD for windows 7 to fix the mbr last time and it was  extremely frustrating and kept me from doing needed work for about a  day. 

A great many internets for whoever can help me out.

My rig:
AMD PHENOM II 970 X4
ASUS M4A88TD/USB3
500G WDC CAVIAR BLUE w/ window7
500G SEAGATE BARRACUDA w/ linux mint
4G RIPJAW DDR3 RAM

---

### Post by mikewhatever on 2011-01-23
All I could understand from the above is that something doesn't boot, parts of the hdd are inaccessible, and that you want to make something bootable. Are you trying to be vague?
:p

---

### Post by mspoden on 2011-01-23
Grub interface comes up. I select linux mint...blank screen for eternity.

During the install, i manually partitioned the drive. When i created the /root partition, i am pretty sure forgot to select 'bootable.' Hence the reason why it does not boot. 

Is there a way to make the root partition bootable without wiping the drive and reinstalling?

---

### Post by mikewhatever on 2011-01-23
> **mspoden said:**
> Grub interface comes up. I select linux mint...blank screen for eternity.

During the install, i manually partitioned the drive. When i created the /root partition, i am pretty sure forgot to select 'bootable.' Hence the reason why it does not boot. 

Is there a way to make the root partition bootable without wiping the drive and reinstalling?

Sure, you can set the bootable flag using Gparted from the live cd. However. I very much doubt that is the problem, since Grub doesn't care if a partition is bootable or not. The boot flag is a Windows thing.
If it works for you, fine, and if not, post the output of **sudo fdisk -l** to show the partitions layout.

---

### Post by presence1960 on 2011-01-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by mspoden on 2011-01-26
thanks for the help. i am going to try this out and get back to you on the results. 

Thanks.

---

### Post by gordintoronto on 2011-01-26
> **mspoden said:**
> Grub interface comes up. I select linux mint...blank screen for eternity.

During the install, i manually partitioned the drive. When i created the /root partition, i am pretty sure forgot to select 'bootable.' Hence the reason why it does not boot. 


Really, that's not why it doesn't boot.  Have a look at "bootoptions" in the Community docs.

Also, tell us what video card. That is the most common source of this simple issue.

---

### Post by mspoden on 2011-01-26
yeah, i learned that this was not correct and wiped and reinstalled.

---

### Post by mspoden on 2011-01-28
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,414,374   102,414,312   7 HPFS/NTFS
/dev/sda2         102,414,436   976,771,071   874,356,636   5 Extended
/dev/sda5         102,414,438   563,222,834   460,808,397   7 HPFS/NTFS
/dev/sda6         563,224,576   961,146,879   397,922,304  83 Linux
/dev/sda7         961,148,928   976,771,071    15,622,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6CCAA837CAA7FB88                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        94F0B0EEF0B0D826                       ntfs                                     
/dev/sda6        f0e71176-c3b9-4b69-8a9d-43ba27c82b1b   ext4                                     
/dev/sda7        c3373011-942c-4774-8e18-6a865002d435   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        34A2B67EA2B643E0                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /live/image              iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
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
    search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f0e71176-c3b9-4b69-8a9d-43ba27c82b1b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f0e71176-c3b9-4b69-8a9d-43ba27c82b1b ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set f0e71176-c3b9-4b69-8a9d-43ba27c82b1b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ccaa837caa7fb88
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
UUID=f0e71176-c3b9-4b69-8a9d-43ba27c82b1b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c3373011-942c-4774-8e18-6a865002d435 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 417.3GB: boot/grub/grub.cfg
 396.5GB: boot/initrd.img-2.6.35-22-generic
 417.3GB: boot/vmlinuz-2.6.35-22-generic
 396.5GB: initrd.img
 417.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  20 ad 0a 00 00 00 00 01  |........ .......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  2f 60 d9 4b a4 1d bf fc  72 2a dd 0a 8c 91 ef 7b  |/`.K....r*.....{|
00000010  94 df 17 1d a7 48 3c 8c  37 09 6d f0 dc 4b 34 0e  |.....H<.7.m..K4.|
00000020  44 68 64 02 b9 8d 01 1d  d5 6b 77 2c e2 0f 1e 1e  |Dhd......kw,....|
00000030  5a 94 ae 74 d4 9e 02 01  cd 28 2b 82 1a 17 51 c1  |Z..t.....(+...Q.|
00000040  0f a2 06 58 7c 77 20 a5  f5 94 1f 4c 2e 94 11 65  |...X|w ....L...e|
00000050  89 57 6c 72 32 fe ce a2  5c 58 9d f9 a4 b7 a1 08  |.Wlr2...\X......|
00000060  31 81 5e 41 64 ee aa cb  6a 6f 24 a6 d3 e0 d4 1a  |1.^Ad...jo$.....|
00000070  c3 1c b7 12 41 78 c2 8d  73 ee 57 a2 2e 31 20 4a  |....Ax..s.W..1 J|
00000080  bb be c5 0d 2a 54 bb 9e  cf ff 3b 85 3a 3c 6b 88  |....*T....;.:<k.|
00000090  ce df 2e e7 ce 10 ab 44  dd 0c 77 48 82 a4 f5 fa  |.......D..wH....|
000000a0  85 aa 69 1e 2d 8d ee eb  0e 99 7c 11 6a 98 a0 d5  |..i.-.....|.j...|
000000b0  b2 fa e9 00 6d 63 2e 77  f6 dd 2f 10 16 8f 6b 1a  |....mc.w../...k.|
000000c0  87 b2 0c e0 c7 37 2d fa  7f 14 3a a4 21 fe f8 65  |.....7-...:.!..e|
000000d0  8b 89 5d 59 c3 60 01 cc  cf 74 2a 5d a6 b5 b6 51  |..]Y.`...t*]...Q|
000000e0  cb df c8 62 16 09 7e b4  95 80 21 89 d6 97 30 17  |...b..~...!...0.|
000000f0  2f 27 4d 34 d8 32 b3 df  ba 3f 08 eb 01 42 33 02  |/'M4.2...?...B3.|
00000100  43 85 04 59 da a3 dd 3d  a0 ca b3 21 6f c0 09 4c  |C..Y...=...!o..L|
00000110  91 e9 3f 51 a5 2b b2 6a  e5 7c 5a 24 af a2 7d 44  |..?Q.+.j.|Z$..}D|
00000120  b6 4e 1d be 08 45 47 2d  b0 6a 0d 44 d6 a7 b1 11  |.N...EG-.j.D....|
00000130  3e 2e 0a 37 5a 52 c2 79  a1 92 f0 f6 c0 d2 bd 7c  |>..7ZR.y.......||
00000140  bc d7 ef cb 61 88 c3 b4  93 3d e1 eb e1 c9 eb 48  |....a....=.....H|
00000150  32 d2 f9 34 92 c8 02 2e  6b 89 67 b8 9c 6a 23 db  |2..4....k.g..j#.|
00000160  a6 78 97 87 19 bd 7e 5a  b8 fc c8 9b 9f 70 b8 6c  |.x....~Z.....p.l|
00000170  98 79 4d e9 57 74 f4 72  46 44 b3 93 b1 82 c6 65  |.yM.Wt.rFD.....e|
00000180  02 e2 f3 ad bf 66 da 50  59 4a 0f da 1e 21 98 a2  |.....f.PYJ...!..|
00000190  48 28 5a 91 c7 30 82 e9  b3 7c f2 81 38 60 3e bf  |H(Z..0...|..8`>.|
000001a0  00 fa d1 c9 84 30 93 a1  cf 4a 87 fe e5 00 0c e5  |.....0...J......|
000001b0  28 94 b6 bc 4c 98 ce b1  74 28 b3 24 db 3d 00 01  |(...L...t(.$.=..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 cd 60 77 1b 00 fe  |...........`w...|
000001d0  ff ff 05 fe ff ff cf 60  77 1b cd d6 b7 17 00 00  |.......`w.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by mspoden on 2011-01-28
So, this is no longer a linux mint install, it is ubuntu 10.10 and i know that the title of the thread is not the problem. but i am now on to 11 installs for this week so any help at this point is awesome. I am still getting the same problem as before. Thanks.

---

### Post by wormyblackburny on 2011-01-28
If it were me, I would blow away all of the ext3/4 partitions then use the Windows7 disk manager to "reclaim" all of the partitions. After that, use 7's disk management to "shrink" the volume and do a fresh install using this tutorial: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) I used that tutorial for all of the dual boot installs I have done and it works perfectly. Not sure why you have had such a hard time....?

---

