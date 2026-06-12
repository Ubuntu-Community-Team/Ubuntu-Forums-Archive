---
title: "Errors booting Ubuntu"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by SlightlyChaotic on 2011-07-24
A while ago (i.e. in march) I was having issues when booting ubuntu; namely, /home wouldn't mount (among other things.) The first thing I was told was to run a script to collect data about booting ubuntu, which I put off and put off until I finally forgot all about the issue.

Well, out of necessity (and the fact that I want to try Ubuntu 11) I have to get ubuntu working again. I installed the new iso over top of the old one, hoping that would solve the issue. 

It didn't. Currently, when I try to run ubuntu, I get this error dialog: 
```

"There is a problem with the configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
```So, I downloaded and ran the aforementioned script. Here's the result.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /Boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdc7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdc8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    23,005,079    23,005,017   7 NTFS / exFAT / HPFS
/dev/sda2    *     23,005,080   976,768,064   953,762,985   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156373504 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    36,251,647    36,249,600  83 Linux
/dev/sdc2          36,253,694 1,465,147,391 1,428,893,698   5 Extended
/dev/sdc5          48,830,464    72,265,727    23,435,264  82 Linux swap / Solaris
/dev/sdc6          72,267,776   111,327,231    39,059,456  83 Linux
/dev/sdc7         111,329,280 1,465,147,391 1,353,818,112   7 NTFS / exFAT / HPFS
/dev/sdc8          36,253,696    48,830,463    12,576,768  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D0D08E21D08E0DC2                       ntfs       RECOVERY
/dev/sda2        B03A27DC3A279DFA                       ntfs       
/dev/sdb1        8A302A0E302A01B5                       ntfs       
/dev/sdc1        6e754605-2cfd-4538-a8f0-8cd6ec63ee5b   ext4       
/dev/sdc5        e1893035-5f3d-43c3-9c29-58fb49e48c2d   swap       
/dev/sdc6        23ee94da-6bbc-4c2d-8bae-a91411c91443   ext4       
/dev/sdc7        D2F8F272F8F253E7                       ntfs       WeArePortableDrive
/dev/sdc8        5b983498-5e63-4d08-89c1-42617976cfa9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/B03A27DC3A279DFA  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc7        /media/WeArePortableDrive fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6e754605-2cfd-4538-a8f0-8cd6ec63ee5b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6e754605-2cfd-4538-a8f0-8cd6ec63ee5b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 6e754605-2cfd-4538-a8f0-8cd6ec63ee5b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root D0D08E21D08E0DC2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root B03A27DC3A279DFA
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
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=6e754605-2cfd-4538-a8f0-8cd6ec63ee5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc8 during installation
UUID=5b983498-5e63-4d08-89c1-42617976cfa9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   5.499206543 = 5.904728064    boot/grub/core.img                             1
   6.290248871 = 6.754103296    boot/grub/grub.cfg                             1
   0.080238342 = 0.086155264    boot/initrd.img-2.6.38-8-generic               1
   4.256080627 = 4.569931776    boot/vmlinuz-2.6.38-8-generic                  1
   0.080238342 = 0.086155264    initrd.img                                     1
   4.256080627 = 4.569931776    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  48 90 2b 37 68 ec 48 5c  aa 0c 2e 23 d7 d9 9d b3  |H.+7h.H\...#....|
00000010  03 c5 61 91 2d cd 97 82  03 93 e7 5e d1 19 99 5e  |..a.-......^...^|
00000020  44 99 40 93 dd 3c b7 ac  b9 db 0e 2c fa c5 c5 32  |D.@..<.....,...2|
00000030  db ee 80 62 ac 6c a3 51  ed ee 8f 41 6d 66 cc 8b  |...b.l.Q...Amf..|
00000040  36 a8 a8 13 e8 79 85 75  00 d2 00 e5 ad 6c 9b a6  |6....y.u.....l..|
00000050  4a 18 80 93 ae b8 f3 3b  01 33 05 54 71 92 e7 bc  |J......;.3.Tq...|
00000060  24 57 b7 d3 5f 59 21 8e  75 1e 41 15 a5 1a e2 7f  |$W.._Y!.u.A.....|
00000070  03 46 fe 39 4a e2 a9 ef  cf b6 68 ee 65 85 87 05  |.F.9J.....h.e...|
00000080  19 7b a1 cb 90 72 7b 78  92 b6 af 69 12 93 61 1b  |.{...r{x...i..a.|
00000090  86 c4 ad 56 d0 60 e8 c0  02 26 48 bd 9e 78 4c fb  |...V.`...&H..xL.|
000000a0  27 ab 16 65 c1 b6 ca ce  09 b2 11 f2 2b 15 65 7f  |'..e........+.e.|
000000b0  37 73 3b 40 71 4a fc 8f  b1 d0 42 22 3a 95 88 5e  |7s;@qJ....B":..^|
000000c0  82 c0 c9 0d cb f1 bf 11  9f 6d a3 fc b2 bf 5d 00  |.........m....].|
000000d0  c3 7f 84 7e 3f c5 5a 29  f9 4b 0e 78 ef 6e 3b 2c  |...~?.Z).K.x.n;,|
000000e0  d0 48 94 37 c9 c8 a1 bf  4c 48 01 7f 0b de 79 69  |.H.7....LH....yi|
000000f0  c4 25 62 81 e5 b1 cd 8e  f6 79 c7 67 ce dd f3 f8  |.%b......y.g....|
00000100  90 4b 74 0e ce 73 59 43  52 8a 88 83 97 03 9f 08  |.Kt..sYCR.......|
00000110  e4 6a 56 da c4 3a f2 cd  08 48 92 3b 19 bc 65 94  |.jV..:...H.;..e.|
00000120  9c 57 4d 64 db 30 25 94  ca 12 0e 27 4a cc 86 5e  |.WMd.0%....'J..^|
00000130  1b a8 d0 f2 28 54 0b 43  23 ed 8f 13 9c cf 58 cd  |....(T.C#.....X.|
00000140  da 15 27 b2 72 49 9e cf  69 37 0e 36 3d b8 88 9c  |..'.rI..i7.6=...|
00000150  e4 f6 4e 84 a5 a7 5b 68  4c aa 54 1a c2 be 98 6c  |..N...[hL.T....l|
00000160  9a 96 b5 e8 37 9a db 8f  49 df 7e bd e9 26 3a 71  |....7...I.~..&:q|
00000170  a9 12 20 90 98 7c cf 80  9e 65 22 34 ca d6 79 b3  |.. ..|...e"4..y.|
00000180  04 ad 19 e6 56 5f 64 0d  80 19 17 a6 1b a2 ac b1  |....V_d.........|
00000190  d1 83 8c 39 d7 d1 7e 6e  63 3a 13 cf c2 3a d6 61  |...9..~nc:...:.a|
000001a0  fa 18 f8 84 21 da cd 1f  15 1d 2f 77 e9 70 fb 15  |....!...../w.p..|
000001b0  fc da 11 7a fc 10 4e 9c  80 4b 5b 2b 84 fb 00 fe  |...z..N..K[+....|
000001c0  ff ff 82 fe ff ff 02 e8  bf 00 00 98 65 01 00 fe  |............e...|
000001d0  ff ff 05 fe ff ff 02 80  25 02 00 08 54 02 00 00  |........%...T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```Does anyone have any ideas on what the issue is, and how to fix it? Thanks a ton!

---

### Post by drs305 on 2011-07-24
I did a search on:
> "gconf-sanity-check-2 exited with status 256" natty
and also looked at previous releases as well.

The issue normally appears to be either a missing folder or a permission problem. Unfortunately, which particular item needs changing seems to vary with each system. 

I can't give you a specific thread to look at but as you read through them concentrate on posts within the past year or so.

---

