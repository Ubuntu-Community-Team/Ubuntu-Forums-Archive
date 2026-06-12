---
title: "DOS and Ubuntu"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by machdohvah on 2011-06-19
OK... I did not check to see if this specific problem has been addressed. I have attached a cropped screen shot from the root terminal. The thing is that I burned an image of a DOS 6.22 CD designed to install the operating system. I erased all partitions (after backing up everything) and proceeded to install the thing from CD. It mounted correctly from boot, but it did not recognize the CD that it was running off of. I proceeded to FDISK a primary partition for DOS. Formatted the partition with the /s switch and was able to access C: from there. I then installed Ubuntu 10.10 in the next three partition in the usual way. After going though all that. I mounted the DOS partition while in Ubuntu and copied the boot disk for DOS into the first partition. But, when I went to boot, no menu presented itself to allow me to choose to boot on to the DOS partition, it simply went to Ubuntu instead. What did I do wrong? How can I fix it? More information... I have configured the C: drive the way I always do it so it is ready to boot correctly if and when it does. I am only able to access the drive with DOS if I use the CD and transferring COMSPEC to the C: drive. I am not able to access the CD drive while in that state. Everything is in place, but it just won't boot into DOS 6.22. I am familiar with dosbox and use it all the time. It is just that I would like to have the full use of DOS in its native state. Any help is appreciated.

-- Michael Flower

---

### Post by jtarin on 2011-06-19
I would suggest make a Win 98 floppy (image to USB flash if you have no floppy) then boot with that and use fdisk to set up and make your partition bootable then I think the command when back at the USB/Floppy prompt would be "sys:A".....but I don't know your "image" file your working with, but my suspicions are you don't have the system files on the partition yet for it to be able to boot.It's been awhile, so my memory is not up to snuff. :)

Edit: you might also try a bootable USB with the SYS files copied to it rather than the 98 image, but then you would have no tools. [Here's]("http://www.bootdisk.com/pendrive.htm") a really good site for all things bootable from the early-present.Look around the site there is more than just the one page.

---

### Post by mastablasta on 2011-06-20
so you want to have bootable DOS on first drive (C:) that has access to CD drive? if so then yes doing it from win98 might be easier. Also i think you need a programme to access CD form it and also you will have to modify autoexec.bat a bit and possibly config.sys for it to load on start. 
 
do you have a floppy drive?
 
i am a bit rusty with DOs at the moment sine i haven't used it for quite some time :-D
but i used to do this kind of configurations all the time. i remember first attemt at linux was Win98 first partition then second had to be linux and then windows again. so i had to split the first partition and cretae new one. it was alot more difficult then than is is now.
 
edit: i found it. i knew it was something mscdex.... have a look here: [http://support.microsoft.com/kb/135174](http://support.microsoft.com/kb/135174)

---

### Post by lisati on 2011-06-20
It has been a while since I've done anything Win98 or DOS, but concur that you'll need to make the partition bootable, and using mscdex will help make the CD accessible.

---

### Post by machdohvah on 2011-06-21
First of all, I do not have a floppy drive... The flash drive would be better if I could only remember where I stashed the flash drive... But, how would I run FORMAT /s to the flash drive or should I have to load an image directly? If I were to burn a CD with a boot image, how would I create the right parameters in the two files CONFIG.SYS and AUTOEXEC.BAT so that it would make the first partition resident? If the first partition is already marked as bootable (see my first entry) as it is, then why does it not boot in the partition in the first place? <dazed and confused>

---

### Post by oldfred on 2011-06-21
Bootscript was modified to see win98 partition.

```
sdb1: _____________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

```

Since win98 is DOS based it may see your partition.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jtarin on 2011-06-21
> **machdohvah said:**
> First of all, I do not have a floppy drive... The flash drive would be better if I could only remember where I stashed the flash drive... But, how would I run FORMAT /s to the flash drive or should I have to load an image directly? If I were to burn a CD with a boot image, how would I create the right parameters in the two files CONFIG.SYS and AUTOEXEC.BAT so that it would make the first partition resident? If the first partition is already marked as bootable (see my first entry) as it is, then why does it not boot in the partition in the first place? <dazed and confused>[Some answers here.]("http://www.bootdisk.com/pendrive.htm")  And at the bottom of this [page]("http://www.bootdisk.com/") some links for answers to your other questions. Remember as in windows DOS expects C:\ drive to be the first partition. If your other partitions are not formatted it should not recognize them. I can't remember if DOS has a cylinder limitation to install to. It's been awhile. :) I used to have DOS setup for mail, web browsing and Yahoo chat all with dial-up. I think it's possible to do it with broadband now.

---

### Post by machdohvah on 2011-06-22
> **oldfred said:**
> Bootscript was modified to see win98 partition.

```
sdb1: _____________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

```Since win98 is DOS based it may see your partition.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

OK... Did that and here is the result file:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  MS-DOS 6.22
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     4,192,964     4,192,902   6 FAT16
/dev/sda2           4,194,304 1,953,329,151 1,949,134,848  83 Linux
/dev/sda3       1,953,331,198 1,953,523,711       192,514   5 Extended
/dev/sda5       1,953,331,200 1,953,523,711       192,512  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,127 1,953,520,065   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2258-07E7                              vfat       MYDOS
/dev/sda2        da7bd8eb-d593-4cf8-ad6a-007a09e10d29   ext4       
/dev/sda5        811fb15a-8918-4f2e-85c9-95c9dc08c89b   swap       
/dev/sdb1        3028919728915D22                       ntfs       Expansion Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=da7bd8eb-d593-4cf8-ad6a-007a09e10d29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=da7bd8eb-d593-4cf8-ad6a-007a09e10d29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set da7bd8eb-d593-4cf8-ad6a-007a09e10d29
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=da7bd8eb-d593-4cf8-ad6a-007a09e10d29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=811fb15a-8918-4f2e-85c9-95c9dc08c89b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 144.138664246 = 154.767712256  boot/grub/core.img                             1
 858.216606140 = 921.503064064  boot/grub/grub.cfg                             1
   3.017818451 = 3.240357888    boot/initrd.img-2.6.35-28-generic-pae          1
 144.136005402 = 154.764857344  boot/vmlinuz-2.6.35-28-generic-pae             1
   3.017818451 = 3.240357888    initrd.img                                     1
 144.136005402 = 154.764857344  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 01 00  |.<.MSDOS5.0..@..|
00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  86 fa 3f 00 80 00 29 e7  07 58 22 4d 59 44 4f 53  |..?...)..X"MYDOS|
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |      FAT16   .3|
00000040  c0 8e d0 bc 00 7c 16 07  bb 78 00 36 c5 37 1e 56  |.....|...x.6.7.V|
00000050  16 53 bf 3e 7c b9 0b 00  fc f3 a4 06 1f c6 45 fe  |.S.>|.........E.|
00000060  0f 8b 0e 18 7c 88 4d f9  89 47 02 c7 07 3e 7c fb  |....|.M..G...>|.|
00000070  cd 13 72 79 33 c0 39 06  13 7c 74 08 8b 0e 13 7c  |..ry3.9..|t....||
00000080  89 0e 20 7c a0 10 7c f7  26 16 7c 03 06 1c 7c 13  |.. |..|.&.|...|.|
00000090  16 1e 7c 03 06 0e 7c 83  d2 00 a3 50 7c 89 16 52  |..|...|....P|..R|
000000a0  7c a3 49 7c 89 16 4b 7c  b8 20 00 f7 26 11 7c 8b  ||.I|..K|. ..&.|.|
000000b0  1e 0b 7c 03 c3 48 f7 f3  01 06 49 7c 83 16 4b 7c  |..|..H....I|..K||
000000c0  00 bb 00 05 8b 16 52 7c  a1 50 7c e8 92 00 72 1d  |......R|.P|...r.|
000000d0  b0 01 e8 ac 00 72 16 8b  fb b9 0b 00 be e6 7d f3  |.....r........}.|
000000e0  a6 75 0a 8d 7f 20 b9 0b  00 f3 a6 74 18 be 9e 7d  |.u... .....t...}|
000000f0  e8 5f 00 33 c0 cd 16 5e  1f 8f 04 8f 44 02 cd 19  |._.3...^....D...|
00000100  58 58 58 eb e8 8b 47 1a  48 48 8a 1e 0d 7c 32 ff  |XXX...G.HH...|2.|
00000110  f7 e3 03 06 49 7c 13 16  4b 7c bb 00 07 b9 03 00  |....I|..K|......|
00000120  50 52 51 e8 3a 00 72 d8  b0 01 e8 54 00 59 5a 58  |PRQ.:.r....T.YZX|
00000130  72 bb 05 01 00 83 d2 00  03 1e 0b 7c e2 e2 8a 2e  |r..........|....|
00000140  15 7c 8a 16 24 7c 8b 1e  49 7c a1 4b 7c ea 00 00  |.|..$|..I|.K|...|
00000150  70 00 ac 0a c0 74 29 b4  0e bb 07 00 cd 10 eb f2  |p....t).........|
00000160  3b 16 18 7c 73 19 f7 36  18 7c fe c2 88 16 4f 7c  |;..|s..6.|....O||
00000170  33 d2 f7 36 1a 7c 88 16  25 7c a3 4d 7c f8 c3 f9  |3..6.|..%|.M|...|
00000180  c3 b4 02 8b 16 4d 7c b1  06 d2 e6 0a 36 4f 7c 8b  |.....M|.....6O|.|
00000190  ca 86 e9 8a 16 24 7c 8a  36 25 7c cd 13 c3 0d 0a  |.....$|.6%|.....|
000001a0  4e 6f 6e 2d 53 79 73 74  65 6d 20 64 69 73 6b 20  |Non-System disk |
000001b0  6f 72 20 64 69 73 6b 20  65 72 72 6f 72 0d 0a 52  |or disk error..R|
000001c0  65 70 6c 61 63 65 20 61  6e 64 20 70 72 65 73 73  |eplace and press|
000001d0  20 61 6e 79 20 6b 65 79  20 77 68 65 6e 20 72 65  | any key when re|
000001e0  61 64 79 0d 0a 00 49 4f  20 20 20 20 20 20 53 59  |ady...IO      SY|
000001f0  53 4d 53 44 4f 53 20 20  20 53 59 53 00 00 55 aa  |SMSDOS   SYS..U.|
00000200

Unknown BootLoader on sda3

00000000  87 4a ed f7 26 73 ca 8c  5d 01 50 13 d6 4b 4e 2f  |.J..&s..].P..KN/|
00000010  5c 48 59 65 45 22 d4 7b  cc d0 bc be 87 9a f6 c1  |\HYeE".{........|
00000020  f8 ac 4a 72 ee 45 09 c5  58 31 03 63 8f e9 4e ab  |..Jr.E..X1.c..N.|
00000030  e9 f8 59 60 d4 48 d2 bb  b8 d2 8a dc 55 54 b1 51  |..Y`.H......UT.Q|
00000040  e3 96 b6 9c 20 75 09 5f  72 c1 dd 96 62 0c 2c 69  |.... u._r...b.,i|
00000050  c2 dc d5 a9 49 67 d3 df  5c 06 90 ad 90 64 be bd  |....Ig..\....d..|
00000060  fa 7f 4d 2c b0 dc 72 24  37 b3 1c 29 e4 4f b0 49  |..M,..r$7..).O.I|
00000070  c7 c1 c3 79 9e 03 22 26  12 3d 11 f8 4b b2 bb 12  |...y.."&.=..K...|
00000080  58 8a 08 80 1f f5 b2 53  d0 a4 dd 97 fc 41 91 15  |X......S.....A..|
00000090  92 dc 06 82 08 7e a8 11  fa c6 43 27 7f 4c ed 0c  |.....~....C'.L..|
000000a0  c4 04 4a 9e e4 de 98 ce  14 23 60 e1 6f dc 37 f1  |..J......#`.o.7.|
000000b0  d5 26 3a 57 6c 34 a8 25  4f 32 4f 52 56 4f f8 08  |.&:Wl4.%O2ORVO..|
000000c0  8d 58 53 59 d7 bd d6 97  82 16 76 bd e4 39 a7 ab  |.XSY......v..9..|
000000d0  09 db 8e 95 1c 9b 1b f1  b7 1f 98 75 81 e4 e5 f2  |...........u....|
000000e0  13 24 da ee 8c d0 53 df  db b2 36 a5 fa b9 d0 78  |.$....S...6....x|
000000f0  28 91 14 3c df 40 b7 e7  72 bb ec dd a9 dc d5 8d  |(..<.@..r.......|
00000100  9b ed aa f3 91 bc 9f 7f  80 b6 a5 28 a8 f6 6c 6f  |...........(..lo|
00000110  de cc 46 80 de 4a 49 21  ec 64 f9 36 99 c4 f7 83  |..F..JI!.d.6....|
00000120  24 d3 ad 86 fb 41 a3 0a  5f 2c 29 da 7b 91 42 82  |$....A.._,).{.B.|
00000130  78 33 f4 2a ec 67 c8 d5  0d 9a 36 d0 f9 cb 97 14  |x3.*.g....6.....|
00000140  8f bd 40 1f a0 59 69 d9  d8 f2 eb 3b eb e1 17 65  |..@..Yi....;...e|
00000150  92 92 ef 5d 29 06 2a fa  8d d3 4e 5b 36 d2 b5 03  |...]).*...N[6...|
00000160  2d 4f 2b a9 54 5c 27 c6  9e a0 cf d7 4f 15 c7 3e  |-O+.T\'.....O..>|
00000170  66 2f a9 03 53 25 a2 c5  59 44 bc d9 a2 f6 58 de  |f/..S%..YD....X.|
00000180  b4 0f b9 90 ba f4 a5 c5  80 55 dd 5f f6 3e e9 50  |.........U._.>.P|
00000190  73 cd 1e 4e 4a dd 2c 7e  1f 18 d6 64 3b 2f 19 7c  |s..NJ.,~...d;/.||
000001a0  80 af 56 52 3d ec 36 fd  24 31 15 19 29 75 67 d5  |..VR=.6.$1..)ug.|
000001b0  6f 07 49 ea 67 55 51 0c  ef 85 18 07 72 b6 00 fe  |o.I.gUQ.....r...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 02 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

So, What do I do now? :)

---

### Post by dFlyer on 2011-06-22
Have you looked into freedos?

---

### Post by mastablasta on 2011-06-22
> **dFlyer said:**
> Have you looked into freedos?
 
 
although not exactly the same as original dos this might be a solution you could try. they even have a liveCD ;-)

---

### Post by wep940 on 2011-06-22
I'd like to offer another alternative:  Use virtualbox and install your DOS to it.  If you can make or have a copy of DOS as an ISO image it would be great.

BTW - if you'd like to try Windows 98SE (again, could be stand-alone, but I would suggest a virtual machine) and are in need of the disks to do so, just let me know.

---

### Post by jtarin on 2011-06-22
> **wep940 said:**
> I'd like to offer another alternative:  Use virtualbox and install your DOS to it.  If you can make or have a copy of DOS as an ISO image it would be great.

BTW - if you'd like to try Windows 98SE (again, could be stand-alone, but I would suggest a virtual machine) and are in need of the disks to do so, just let me know.If you have a link to that PM me.:p I can't read my old CD.

---

### Post by grahammechanical on 2011-06-22
I have noticed this comment:

> I mounted the DOS partition while in Ubuntu and **copied** the boot disk for DOS into the first partition.Should you not have **installed** DOS on to the C:\?

There is another point that I would like to make. By installing Ubuntu you put GRUB into the MBR. This is why it is loading into Ubuntu and as GRUB is not aware of any other operating system it will not show you a boot menu. You will need to run the sudo update-grub2 command to see if GRUB recognizes DOS as an operating system and places a reference to it in the boot menu.

Regards.

---

### Post by oldfred on 2011-06-22
All windows and I do not remember but DOS have to have a proper boot sector. Not sure if you have correct boot sector of if boot script just does not check one's that old.

> Boot sector type:  Unknown

I would try using testdisk. I know it will bebuild NTFS but not sure about FAT.


download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by psusi on 2011-06-22
Why are you trying to run DOS?  It has been dead for well over a decade ( damn, now I feel old ).  If you have an ancient dos based game or something that you want to run, install dosemu and run it under there.  At least that way you don't have to worry about hardware incompatibility, partitions, and shutting down Ubuntu to reboot into DOS.

---

### Post by jtarin on 2011-06-22
> **psusi said:**
> Why are you trying to run DOS?  It has been dead for well over a decade ( damn, now I feel old ).  If you have an ancient dos based game or something that you want to run, install dosemu and run it under there.  At least that way you don't have to worry about hardware incompatibility, partitions, and shutting down Ubuntu to reboot into DOS.
You don't get it.:P

---

### Post by lkraemer on 2011-06-23
machdohvah,
I went to my basement and fired up my old DOS machine to get the
information I had been using years ago....

Config.sys
```

device=c:\TEAC\TEAC-CDI.sys /D:TEAC-CDI
device=c:\dos\himem.sys
device=c:\dos\emm386.exe ram x=cb00-cbff
device=ansi.sys
dos=high,umb
LASTDRIVE=Z
files=30
buffers=30

```

Autoexec.bat
```

c:\dos\mscdex.exe /D:TEAC-CDI /M:15
Prompt $p$g
cls

```

That should allow you to do acces the cdrom drive and all the files.

If it doesn't boot from the Hard Drive's first Partition,
you can use:
```

sys c:

```
to copy the boot info to C:

If you do that you'll most likely have to reinstall grub, to get 
Ubuntu to boot.

If you want a copy of the TEAC Drivers PM me with an Email address.

Larry

---

### Post by machdohvah on 2011-06-23
> **grahammechanical said:**
> I have noticed this comment:

Should you not have **installed** DOS on to the C:\?

There is another point that I would like to make. By installing Ubuntu you put GRUB into the MBR. This is why it is loading into Ubuntu and as GRUB is not aware of any other operating system it will not show you a boot menu. You will need to run the sudo update-grub2 command to see if GRUB recognizes DOS as an operating system and places a reference to it in the boot menu.

Regards.

Yes, I installed it.

I just tried from the root terminal: update-grub2 and it did not change the fact that Ubuntu is the only thing that is allowed to boot on this machine. Nice try for you are on the right track. I just need grub to present a menu as to which of the two operating systems the user chooses to boot.

---

### Post by jtarin on 2011-06-23
According to Grub2 docs it should recognize DOS. Then there is [this.]("https://gna.org/projects/grub4dos").....a little dated but still workable I'm sure it's Grub1.Do you have the boot-flag on, on that partition?

---

### Post by jtarin on 2011-06-24
Try formatting your DOS partition using Linux fdisk and use the DOS flag for the filesystem and try flagging it bootable.

---

### Post by oldfred on 2011-06-24
Boot flag/active partition is used by the DOS/Windows boot loaders (and Lilo) to know what partition to jump to to continue booting. But the rest of the boot code has to be in the partition boot sector (PBR). So even with DOS you have to have a proper PBR.

When grub or grub2 chainloads to windows it is just skipping the MBR boot of windows and jumping into the partition (PBR) to continue booting.

---

### Post by machdohvah on 2011-06-24
> **wep940 said:**
> I'd like to offer another alternative:  Use virtualbox and install your DOS to it.  If you can make or have a copy of DOS as an ISO image it would be great.

OK, I tried this suggestion and it intrigues me. So, Here is an update... I deleted the first partition and therefore this thread is a moot point, but this virtual machine worked. It is just that the ISO on the disk is actually incomplete. I need now an actual full ISO image of DOS 6.20. I have the installation disks and would be happy to convert them into an ISO image on a CD if it could be done. One problem is that I need to use another computer to load the disks for I have no 3 1/2 reader. Actually I do, but so far it has not been tested on the virtual system. I will look into that.

---

### Post by machdohvah on 2011-06-24
Update: I tried to get the virtual machine to recognize my USB floppy drive. It did not do so. This is an old issue. Therefore I need a way to get the actual image of DOS 6.20 installation disks onto a CD. Then the virtual disk idea will work. I am throwing away the other DOS 6.22 image for it is incomplete.

On second thought, I will try to combine the ( sys c: ) from the DOS 6.22 installation disk generated from an image file and create ZIP file of the installed DOS files from another computer using DOS 6.20 installation disks. Then burn the information to a CD and go from there into the virtual box.

---

### Post by machdohvah on 2011-06-24
> **psusi said:**
> Why are you trying to run DOS?  It has been dead for well over a decade ( damn, now I feel old ).  If you have an ancient dos based game or something that you want to run, install dosemu and run it under there.  At least that way you don't have to worry about hardware incompatibility, partitions, and shutting down Ubuntu to reboot into DOS.

OK, I give up... virtualbox stinks for it never gets out of its tiny window. I have settled on dosbox which I have had great success before. I just need to accept the little querks it has.

I mean I even took the time to pull out the old computer and format the hard drive with DOS 6.20, zip the DOS directory, install Windows 98, email the zip to my own mail, reconnect the new computer, download the zip, burn the zip contents onto a CD, start the virtual box and surgically forced the CD to be read by the virutalbox, copied all the files and many of the files simply said that it was the wrong version.

This thread is terminated.

---

### Post by mister_p_1998 on 2011-06-24
Did you try fdisk /mbr on your dos install?

---

### Post by lkraemer on 2011-06-24
machdohvah,
You are giving up to quickly!

Your VirtualBox USB problem is one of the two following issues!
1.  If you did not install the PUEL Version from their website, you did not get the version that
has USB Support.  The OSE Version that is normally in the repo's doesn't have USB Support.

2.  If you installed the version from VirtualBox (PUEL), then you just need to create a FILTER in
the right half of the VirtualBox opening Screen.  You may want to create two filters, in case you
want to use more than one USB device.  Once the filters are created you can Right Click on the
USB Icon in the Lower Right Toolbar, and Enable/Disable the USB Device.

Another thing you needed to do was to Install the Guest Additions to be able to get the small
window to enlarge and work properly.  I am wondering if you have Guest Additions Installed.
It is located under the DEVICES Menu or use HOST+D key.  You should have defined the HOST key
or used the DEFAULT.

Also, you can insert your existing DOS 6.22 CD in your CDROM Drive and
create an image of it (ISO file) in Ubuntu.  Once you have the ISO file,
install ISOMASTER in Ubuntu, from the repo's, and then you can add any
other files you want to the original DOS CD's Image.  Once you have the
drivers, and other files on the image, just use Brasero to burn the ISO
Image back to a CDRW.  Now when you boot your DOS 6.22 CDRW, you will have
access to these new files.

Another Option is to go to [www.Bootdisk.com](www.Bootdisk.com) and download the 5.25"
1.2 Meg Floppy inage and try booting from it.  Once you have a bootable 5.25" Floppy,
you can format a 3.5" drive, use sys B: to copy the system, then copy all the files
to the 3.5" Floppy.  You may even want to try just creating this image on a 3.5" 1.44 Meg Drive.

So, you still have lots of options......Don't give up so soon!

Larry

---

### Post by zirkoni on 2011-06-25
> **machdohvah said:**
> I have settled on dosbox which I have had great success before. I just need to accept the little querks it has.
What quirks?

I have Windows 3.11 installed in DOSBox with 1024x768 resolution, 256 colours and Sound Blaster drivers. And I have added some DOS programs like EDIT.COM and XCOPY.EXE in a path environment variable. It's as if I was running a real DOS/Win3 machine. 99.9% of all DOS and 16-bit Windows programs can be installed and run without any problems.

---

### Post by gmargo on 2011-06-25
A very late suggestion: there is also FreeDos [http://www.freedos.org/](http://www.freedos.org/) which may be easier to install.

I have only used it from a USB stick in order to flash the bios on my laptop, but it worked for me.

---

### Post by machdohvah on 2011-07-01
> **machdohvah said:**
> OK, I give up... virtualbox stinks for it never gets out of its tiny window. I have settled on dosbox which I have had great success before. I just need to accept the little querks it has.

I mean I even took the time to pull out the old computer and format the hard drive with DOS 6.20, zip the DOS directory, install Windows 98, email the zip to my own mail, reconnect the new computer, download the zip, burn the zip contents onto a CD, start the virtual box and surgically forced the CD to be read by the virutalbox, copied all the files and many of the files simply said that it was the wrong version.

This thread is terminated.
I threw out the old computer and do not have the need to install DOS in a seperate partition any longer. I use dosbox instead and am quite happy with the results. Here is a screen shot of an analog clock that I would have liked to be on a screen saver. The code can be provided upon request.

---

