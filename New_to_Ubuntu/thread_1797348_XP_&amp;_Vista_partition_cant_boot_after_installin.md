---
title: "XP &amp; Vista partition cant boot after installing Ubuntu 11.04 beta"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by bheemamahesh on 2011-07-04
[B]Hi ...
This is Mahesh...

I installed Windows Xp & Vista

upto here both OSes are worked

the i wanted to experience ubuntu 11.04

in partitions...i select manual partitions and
25 gb to / in ext4
5 gb to swap
then click install now

after some time this error msg appears

[IMG]http://img715.imageshack.us/img715/8716/error1l.jpg[/IMG]



[IMG]http://img51.imageshack.us/img51/9876/error2p.jpg[/IMG]

i tried changing the different device to install bootloader on....
but nothing works

then i select continue without a bootloader

installation completes

but now i'm unable to boot into either xp or vista
it only shows linux bootmenu

all windows partitions are visible in ubuntu except XP

please help me out from this problem
i want to run triple boot



[/B]

---

### Post by jtarin on 2011-07-04
Click on the boot info script in my signature and run then post the results.

---

### Post by bheemamahesh on 2011-07-05
ThanX for responding
> **jtarin said:**
> Click on the boot info script in my signature and run then post the results.
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos11)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    52,436,159    52,436,097   7 NTFS / exFAT / HPFS
/dev/sda2          52,436,221   976,771,071   924,334,851   f W95 Extended (LBA)
/dev/sda5          52,436,223   115,346,699    62,910,477   7 NTFS / exFAT / HPFS
/dev/sda6         115,346,763   178,257,239    62,910,477   7 NTFS / exFAT / HPFS
/dev/sda7         178,257,303   807,410,834   629,153,532   7 NTFS / exFAT / HPFS
/dev/sda8         807,410,898   912,267,089   104,856,192   7 NTFS / exFAT / HPFS
/dev/sda9         912,267,264   966,266,879    53,999,616  83 Linux
/dev/sda10        966,268,928   974,266,367     7,997,440  82 Linux swap / Solaris
/dev/sda11        974,268,416   976,771,071     2,502,656  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda10       eb14d3b2-358b-4cf6-985a-45f263e1a9b5   swap       
/dev/sda11       a3333ab3-9556-486d-af19-abcf99ac8512   ext4       
/dev/sda5        9A947830947810CD                       ntfs       New Volume
/dev/sda6        3CF87B93F87B4A62                       ntfs       New Volume
/dev/sda7        504837B148379526                       ntfs       New Volume
/dev/sda8        6C2061A72061794A                       ntfs       New Volume
/dev/sda9        0628eb0f-f7ab-4880-bd0c-11c5ae9da28c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda11       /boot                    ext4       (rw,commit=0)
/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 0628eb0f-f7ab-4880-bd0c-11c5ae9da28c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
set locale_dir=($root)/grub/locale
set lang=en_IN
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
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux    /vmlinuz-2.6.38-5-generic root=UUID=0628eb0f-f7ab-4880-bd0c-11c5ae9da28c ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /vmlinuz-2.6.38-5-generic root=UUID=0628eb0f-f7ab-4880-bd0c-11c5ae9da28c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=0628eb0f-f7ab-4880-bd0c-11c5ae9da28c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda11 during installation
UUID=a3333ab3-9556-486d-af19-abcf99ac8512 /boot           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=eb14d3b2-358b-4cf6-985a-45f263e1a9b5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 435.155197144 = 467.244335104  boot/grub/core.img                             1
 435.155319214 = 467.244466176  boot/grub/grub.cfg                             1
 435.174804688 = 467.265388544  boot/initrd.img-2.6.38-5-generic               2
 435.135532379 = 467.223220224  boot/vmlinuz-2.6.38-5-generic                  1
 435.174804688 = 467.265388544  initrd.img                                     2
 435.135532379 = 467.223220224  vmlinuz                                        1

============================= sda11/grub/grub.cfg: =============================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 0628eb0f-f7ab-4880-bd0c-11c5ae9da28c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
set locale_dir=($root)/grub/locale
set lang=en_IN
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
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux    /vmlinuz-2.6.38-5-generic root=UUID=0628eb0f-f7ab-4880-bd0c-11c5ae9da28c ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /vmlinuz-2.6.38-5-generic root=UUID=0628eb0f-f7ab-4880-bd0c-11c5ae9da28c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root a3333ab3-9556-486d-af19-abcf99ac8512
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 464.719650269 = 498.988924928  grub/core.img                                  1
 464.719772339 = 498.989056000  grub/grub.cfg                                  1
 464.739257812 = 499.009978368  initrd.img-2.6.38-5-generic                    2
 464.699985504 = 498.967810048  vmlinuz-2.6.38-5-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  88 21 f3 7f 2a cd ca 92  da c8 dd cc ed 14 62 2d  |.!..*.........b-|
00000010  ac f3 9d a8 97 10 9e ed  81 89 67 9d 28 16 d3 2b  |..........g.(..+|
00000020  54 4d b3 dc c8 27 f4 f3  71 a3 1c 38 40 aa 99 30  |TM...'..q..8@..0|
00000030  53 c3 16 e3 4d 5d b4 ba  24 a8 06 56 72 89 1e 91  |S...M]..$..Vr...|
00000040  98 b3 fd 66 07 b6 e3 f9  12 14 65 a9 d9 3a cd 0c  |...f......e..:..|
00000050  cb 77 ef 8c f7 dc e9 b2  80 03 24 c5 be 32 72 c1  |.w........$..2r.|
00000060  63 10 ad 01 58 1d 5f 2c  03 30 a8 41 81 29 87 e1  |c...X._,.0.A.)..|
00000070  b2 dc be e4 0d eb ce 37  e8 31 2e a1 af c6 26 e2  |.......7.1....&.|
00000080  b9 97 ea 52 41 28 93 21  8c 3d a6 79 56 01 7c 4a  |...RA(.!.=.yV.|J|
00000090  ac 40 10 96 6e 30 8e 76  70 26 d2 b3 46 3c aa 8d  |.@..n0.vp&..F<..|
000000a0  ad 7f d5 4e 14 50 7c fa  32 e0 9c 44 63 28 fe b7  |...N.P|.2..Dc(..|
000000b0  e0 1f 27 80 c7 83 3e 67  ab 66 82 37 76 bf 38 d2  |..'...>g.f.7v.8.|
000000c0  d1 27 28 06 83 ea d8 1a  d0 af e2 a1 ef bd 5a 1d  |.'(...........Z.|
000000d0  98 70 0b 51 41 5d af c2  17 d6 a5 f3 6e 7e c2 94  |.p.QA]......n~..|
000000e0  68 1d b8 21 f8 71 5e 44  ce e2 03 ea 41 bd 8c b4  |h..!.q^D....A...|
000000f0  d0 32 68 ba 48 36 e4 45  84 44 14 f5 f5 54 2c cd  |.2h.H6.E.D...T,.|
00000100  ff 7c fd 1f 20 86 83 d0  f6 c3 cf de cc 13 d9 96  |.|.. ...........|
00000110  16 ee 98 0e 5b a1 3f c9  aa bd 16 37 86 fe 18 86  |....[.?....7....|
00000120  6b cb 5d c2 60 45 8f bb  7a 82 f3 3d b6 3b 3e e5  |k.].`E..z..=.;>.|
00000130  c2 e9 c7 a2 b7 94 12 3b  03 e4 5d e2 43 d2 51 35  |.......;..].C.Q5|
00000140  9d 0a 47 c4 e8 1a e1 06  14 bd 5c 12 42 08 77 ea  |..G.......\.B.w.|
00000150  67 68 db 15 60 be 99 7d  64 1a f3 34 85 88 1f 99  |gh..`..}d..4....|
00000160  2a 53 1d fa a5 81 38 ca  e2 2a e6 22 4b 74 ac 04  |*S....8..*."Kt..|
00000170  e7 09 39 8f 20 78 42 61  27 5f 3a 5c 07 d8 35 dd  |..9. xBa'_:\..5.|
00000180  21 8d b9 5d f1 0b b1 08  11 a8 b3 4a a9 4d a2 9a  |!..].......J.M..|
00000190  9c ac d1 4a 19 67 e2 b6  06 d6 88 62 d7 93 5d 63  |...J.g.....b..]c|
000001a0  69 7b 8c 21 d3 d7 80 fa  2e 43 11 cb cc dc 92 91  |i{.!.....C......|
000001b0  82 a5 bf 57 21 e9 48 17  27 8f d6 33 1a 40 76 1e  |...W!.H.'..3.@v.|
000001c0  c3 34 a8 52 78 b6 78 ea  9d 28 72 de 88 66 33 c2  |.4.Rx.x..(r..f3.|
000001d0  fd 89 91 3c 29 8a 45 b1  66 34 3b 0e ec 4a 2b 4c  |...<).E.f4;..J+L|
000001e0  3e f0 8a c0 d6 69 67 9e  01 6b 0b dc a8 4b 70 03  |>....ig..k...Kp.|
000001f0  49 ba 6c 01 5b 5c 09 a0  bb 17 12 3a 3e ed f9 7e  |I.l.[\.....:>..~|
00000200

Unknown BootLoader on sda2

00000000  06 19 7c db b9 63 67 2a  41 ea 4f 6a fa 2c 3c 5b  |..|..cg*A.Oj.,<[|
00000010  81 e5 e6 78 f8 2e 58 49  9a c5 9e 69 96 3d cb f2  |...x..XI...i.=..|
00000020  9d c1 b1 93 9e 9d 7f 13  4f 7b 98 c4 e6 29 0c 65  |........O{...).e|
00000030  cb 96 24 80 30 79 ce 38  e3 a9 ae 19 51 a9 52 47  |..$.0y.8....Q.RG|
00000040  8c eb 28 40 ab f6 f3 e6  31 56 38 cf af 5a 59 67  |..(@....1V8..ZYg|
00000050  9a e5 b7 16 95 57 6e dc  67 8e fc f4 f7 ae ba 30  |.....Wn.g......0|
00000060  50 91 9f d6 5b 65 53 11  79 18 cb 99 03 64 f3 db  |P...[eS.y....d..|
00000070  f2 ab 31 da cc 17 11 95  60 48 8f 69 3d b0 79 e9  |..1.....`H.i=.y.|
00000080  f4 ef e9 ef 5e a5 7a f1  38 be b1 3a b1 34 c5 a9  |....^.z.8..:.4..|
00000090  40 9e 64 48 0a 93 ce 39  e8 3a f3 f5 ab 90 d9 46  |@.dH...9.:.....F|
000000a0  cc ae c5 55 38 2c 54 03  9c e0 fa fb 9a f3 b1 18  |...U8,T.........|
000000b0  b5 23 dd c1 53 92 45 a8  ed 3e d0 8a e0 30 40 33  |.#..S.E..>...0@3|
000000c0  f7 73 c9 fc 7e b5 74 c4  91 a9 02 36 45 c8 3c f1  |.s..~.t....6E.<.|
000000d0  d3 de bc 25 5f 9e 66 d8  b9 c9 cc a3 70 72 80 72  |...%_.f.....pr.r|
000000e0  c1 98 0c fd 4e 29 b3 41  1a b7 dd 51 19 e4 16 24  |....N).A...Q...$|
000000f0  9e fe d8 ae 95 a4 8c 1d  09 ba a3 22 85 e4 61 e5  |..........."..a.|
00000100  82 cd fd 33 f5 a4 68 24  8d 5f 7f 41 db af 38 f5  |...3..h$._.A..8.|
00000110  fc ea d2 d0 f5 32 e7 42  33 e5 a9 bf f5 b8 a8 ce  |.....2.B3.......|
00000120  60 2d e5 3b 8d ea 00 c0  ee 79 39 e3 b1 27 f0 ab  |`-.;.....y9..'..|
00000130  b2 da 49 75 6d 04 52 6e  95 51 70 9b 98 9c 7e 26  |..Ium.Rn.Qp...~&|
00000140  b8 ab 63 9c 19 a5 68 a9  4c 55 b5 29 22 a1 28 8b  |..c...h.LU.)".(.|
00000150  c9 e6 b5 9b 4e df 08 f3  21 8a 4c 9c 30 63 90 47  |....N...!.L.0c.G|
00000160  23 b8 f4 ed 5c 55 f1 37  9f 33 76 3a b1 18 55 4a  |#...\U.7.3v:..UJ|
00000170  9f 34 17 bc cb 50 d8 47  09 55 58 51 62 3d f0 40  |.4...P.G.UXQb=.@|
00000180  07 39 ed ef 9a ba 96 33  4f 24 cb b2 39 94 c7 80  |.9.....3O$..9...|
00000190  40 24 8c 60 fa fa 06 ae  3a b5 da 67 bb 96 e5 dc  |@$.`....:..g....|
000001a0  f0 f6 b5 90 e8 ec c2 0d  a5 c9 1d 0a 82 3f c3 dc  |.............?..|
000001b0  55 b5 b3 65 65 31 05 6e  bc 32 ee eb ed 8c 00 01  |U..ee1.n.2......|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 0d f0 bf 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 0f f0  bf 03 4c f0 bf 03 00 00  |..........L.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by jtarin on 2011-07-05
You've got an abnormal partition scheme. Is this a Hewlett Packard computer? You seem to have some possible disk recovery partition at the beginning. Windows is normally installed first at /dev/sda1 then Ubuntu in an extended partition normally /dev/sda5. What you will have to do is try to update Grub and see if it detects Windows in its present location. This procedure will be the easiest solution to try at this point. First you must have an Ubuntu CD.....then I will link you to some [instructions ]("https://help.ubuntu.com/community/Grub2#ChRoot")for correcting this.You will be using the CHROOT method to access your install from the Live CD.You will do all steps in the instructions **_but not #9 and #10....DO NOT DO THOSE TWO_**.Skip to #11 and continue. When your run "update-grub" you should see in the terminal whether it detects windows or not. Come back and post your results or errors when done.

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> You've got an abnormal partition scheme. Is this a Hewlett Packard computer? You seem to have some possible disk recovery partition at the beginning. Windows is normally installed first at /dev/sda1 then Ubuntu in an extended partition normally /dev/sda5. What you will have to do is try to update Grub and see if it detects Windows in its present location. This procedure will be the easiest solution to try at this point. First you must have an Ubuntu CD.....then I will link you to some [instructions ]("https://help.ubuntu.com/community/Grub2#ChRoot")for correcting this.You will be using the CHROOT method to access your install from the Live CD.You will do all steps in the instructions **_but not #9 and #10....DO NOT DO THOSE TWO_**.Skip to #11 and continue. When your run "update-grub" you should see in the terminal whether it detects windows or not. Come back and post your results or errors when done.
**Mount your normal system partition: **
[LIST]
[*]**Substitute the correct partition: sda1, sdb5, etc. **
[/LIST]
******sudo mount /dev/sdXX /mnt**[B]  Example: [I]sudo mount /dev/sda1 /mnt
[/I][/B][I]
what should i specify instead sdxx & sdyy[/I][B]

[/B]

---

### Post by jtarin on 2011-07-05
We got a problem here....you have two Grub installs....explain?

---

### Post by jtarin on 2011-07-05
Try /dev/sda9 first and if that doesn't work after reboot try /dev/sda11.

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> We got a problem here....you have two Grub installs....explain?
what problem? i dont know how many grubs installed

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> Try /dev/sda9 first and if that doesn't work after reboot try /dev/sda11.
okay i'll try
 /dev/sda9 is /
and
 /dev/sda11 is Swap

---

### Post by jtarin on 2011-07-05
Just try to mount /dev/sda9 and then reboot after your finished updating. then post back.

---

### Post by bheemamahesh on 2011-07-05
[SIZE=3]**sudo fdisk -l**[/SIZE]

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a273c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       60802   462167425+   f  W95 Ext'd (LBA)
/dev/sda5            3265        7180    31455238+   7  HPFS/NTFS
/dev/sda6            7181       11096    31455238+   7  HPFS/NTFS
/dev/sda7           11097       50259   314576766    7  HPFS/NTFS
/dev/sda8           50260       56786    52428096    7  HPFS/NTFS
/dev/sda9           56787       60148    26999808   83  Linux
/dev/sda10          60148       60646     3998720   82  Linux swap / Solaris
/dev/sda11          60646       60802     1251328   83  Linux
[SIZE=3][B]

sudo mount /dev/sd9 /mnt[/B][/SIZE]
mount: special device /dev/sd9 does not exist

**[SIZE=3]sudo mount /dev/sd11 /mnt/boot[/SIZE]**
mount: mount point /mnt/boot does not exist

---

### Post by bheemamahesh on 2011-07-05
should i continue with other steps?

---

### Post by bheemamahesh on 2011-07-05
[COLOR=Red]**for i in /dev /dec/pts /proc /sys; do sudo mount -B $i;done**[/COLOR]
mount: special device none does not exist
mount: can't find /dec/pts in /etc/fstab or /etc/mtab
mount: special device none does not exist
mount: special device none does not exist

---

### Post by jtarin on 2011-07-05
Do you think it might be that you are trying to ```
"sudo mount /dev/sd9 /mnt
mount: special device /dev/sd9 does not exist"
``` when the partition as all partitions  ```
**are /dev/sda**......**not /dev/sd**
```

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> Do you think it might be that you are trying to ```
"sudo mount /dev/sd9 /mnt
mount: special device /dev/sd9 does not exist"
``` when the partition as all partitions  ```
**are /dev/sda**......**not /dev/sd**
```
cant understood

---

### Post by jtarin on 2011-07-05
[SIZE="4"]You are typing /dev/**sd9**[/SIZE]

[SIZE="4"]It should be /dev/**sda9**[/SIZE]
See the difference?

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> [SIZE=4]You are typing /dev/**sd9**[/SIZE]

[SIZE=4]It should be /dev/**sda9**[/SIZE]
See the difference?
oops...sorry i 'll do that again

---

### Post by bheemamahesh on 2011-07-05
[COLOR=DeepSkyBlue]14: sudo umount /mnt/usr[/COLOR]
[COLOR=Red]
umount: /mnt/usr: not mounted[/COLOR]
[COLOR=DeepSkyBlue]
15: sudo umount /mnt[/COLOR]
[COLOR=Red]umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

[COLOR=Black]except these two commands remaining all are executed without errors

#9 & #10 steps are skipped as u said
[/COLOR]
[/COLOR]

---

### Post by bheemamahesh on 2011-07-05
_***total process i've done***_

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a273c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       60802   462167425+   f  W95 Ext'd (LBA)
/dev/sda5            3265        7180    31455238+   7  HPFS/NTFS
/dev/sda6            7181       11096    31455238+   7  HPFS/NTFS
/dev/sda7           11097       50259   314576766    7  HPFS/NTFS
/dev/sda8           50260       56786    52428096    7  HPFS/NTFS
/dev/sda9           56787       60148    26999808   83  Linux
/dev/sda10          60148       60646     3998720   82  Linux swap / Solaris
/dev/sda11          60646       60802     1251328   83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda9 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda11 /mnt/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-5-generic
Found initrd image: /boot/initrd.img-2.6.38-5-generic
Found memtest86+ image: /memtest86+.bin
done
root@ubuntu:/# exit
ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
ubuntu@ubuntu:~$ sudo umount /mnt/boot
ubuntu@ubuntu:~$ sudo umount /mnt/usr
umount: /mnt/usr: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by jtarin on 2011-07-05
Ok that's still not going to boot anything but Linux.
Do you have the windows install CD?

---

### Post by bheemamahesh on 2011-07-05
chroot doesnot works for us ?
then what should i do?

---

### Post by bheemamahesh on 2011-07-05
yes...i have windows installation disks

---

### Post by jtarin on 2011-07-05
> **bheemamahesh said:**
> yes...i have windows installation disksWhich ones do you have? Install disk not repair disk? Which windows was used as the boot manager for the other windows?

---

### Post by bheemamahesh on 2011-07-05
i have windows xp, vista & 7 installation disks
i used vista bootloader before installing ubuntu

---

### Post by jtarin on 2011-07-05
Does your hard drive have windows startup repair?

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> Does your hard drive have windows startup repair?
i dont know

 but, i have miniPE disk can be used as windows live cd

---

### Post by jtarin on 2011-07-05
I have to go for the day but here is a [link]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") to repair your MBR in Windows. Once you get Windows working again PM me for further instructions.....it might be some hours before I can reply as it is already evening here.

---

### Post by bheemamahesh on 2011-07-05
> **jtarin said:**
> I have to go for the day but here is a [link]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") to repair your MBR in Windows. Once you get Windows working again PM me for further instructions.....it might be some hours before I can reply as it is already evening here.
okay thanX for helping me

i'll post further updates

---

### Post by bheemamahesh on 2011-07-05
Than'Q' for spending ur Valuable time
i'm referring the sevenforum.com 

i'll PM u for further details

---

### Post by bheemamahesh on 2011-07-10
i inserted my windows vista installation disk to restore MBR...i found "no option to restore windows in that disk"

i downloaded windows vista recovery disk...and i started recovery process as it is in the link u have specified before in sevenforums.com


in this Step-7:
after typing these commands

Type: exit
and press Enter

to close Diskpart
" 
Type: G: (use the letter of your DVD drive)
and press Enter

Type: cd boot
and press Enter

Type: dir
and press Enter
"
i didnot find "bootsec.exe
"
i'm sure that i've selected the proper dvd drive in step-6

then i type exit & then restart the system

after that i was able to mount windows xp partition (which was unable to mount only that windows xp partition before inserting vista recovery disk)

Then i inserted ubuntu live cd

and i followed the CHROOT method which was suggested by you before i didnot done the two steps #9 & #10 

after that i was able to run triple boot

Than'Q' for solving my Issue...

---

