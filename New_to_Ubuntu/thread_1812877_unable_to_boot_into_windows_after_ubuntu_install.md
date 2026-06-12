---
title: "unable to boot into windows after ubuntu install"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by primal woman on 2011-07-26
I installed ubuntu 11.04 onto emachine desktop. I used the third option titled 'something else' and partitioned almost half my hard drive for ubuntu. I must have done something wrong. It does not give me an option for boot up at all, just goes right into ubuntu. Works fine, but I wanted the option to boot up in windows. 

I had installed 10.04 onto acer laptop and did first option (next to windows or something) and I was not given any option at the time to give any bigger partition to ubuntu which is why I chose the third option for desktop. 

Anyone can help me change this? do I have to go into ubuntu somewhere and change boot sequence? Meanwhile I'll keep trying/hunting for the answer as well. 

Thanks.

---

### Post by primal woman on 2011-07-27
I think I should ad that first of all..I may have posted this in the wrong place.

And upon searching for the answer, I may have found different options, BUT I don't understand them. I am not familiar enough with ubuntu to just 'run' something...do I go to terminal? I found that once! (is that the same as 'run' and msconfig?)

So if anyone has the answer, please be specific if you can. 

Thanks.

---

### Post by wildmanne39 on 2011-07-27
Hi, post the information from this script so we can see where everything is located: You will need to use the livecd to do this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

If you do not understand something post back here and someone will help you.

---

### Post by amjjawad on 2011-07-27
Hello and Welcome :)

Please check the previous post from wildmanne39 and post back as explained:

> **wildmanne39 said:**
> Hi, post the information from this script so we can see where everything is located: You will need to use the livecd to do this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.



> If you do not understand something post back here and someone will help you.

I second that :)

Don't worry, we all have been through exactly the same.

Welcome to Linux World ;)

---

### Post by primal woman on 2011-07-27
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 233369446 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/grub on this drive. No errors found in 
                       the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *      8,723,295   233,332,669   224,609,375   7 NTFS / exFAT / HPFS
/dev/sda2                  63     8,723,294     8,723,232   b W95 FAT32
/dev/sda3         233,332,736   233,527,295       194,560  83 Linux
/dev/sda4         233,529,342   390,721,535   157,192,194   5 Extended
/dev/sda5         233,529,344   238,409,727     4,880,384  82 Linux swap / Solaris
/dev/sda6         238,411,776   248,174,591     9,762,816  83 Linux
/dev/sda7         248,176,640   390,721,535   142,544,896  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 13.7 GB, 13701316608 bytes
240 heads, 63 sectors/track, 1769 cylinders, total 26760384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    26,747,279    26,747,217   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9E2CEC972CEC6C29                       ntfs       
/dev/sda2        423B-2BDF                              vfat       RECOVERY
/dev/sda3        3563c5b4-c1c8-4204-bea4-873af0fe7054   ext4       
/dev/sda5        2ee08420-660e-4e57-bbac-ce03a6638587   swap       
/dev/sda6        439f4c37-0bd0-44e0-9d7d-f622afd8bb5c   ext4       
/dev/sda7        01c4e535-1452-40e3-8839-8ae2babed324   ext4       
/dev/sdb1        3869-21F6                              vfat       SLAVE DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sda3/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 439f4c37-0bd0-44e0-9d7d-f622afd8bb5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 3563c5b4-c1c8-4204-bea4-873af0fe7054
set locale_dir=($root)/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3563c5b4-c1c8-4204-bea4-873af0fe7054
    linux    /vmlinuz-2.6.38-8-generic root=UUID=439f4c37-0bd0-44e0-9d7d-f622afd8bb5c ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3563c5b4-c1c8-4204-bea4-873af0fe7054
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=439f4c37-0bd0-44e0-9d7d-f622afd8bb5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3563c5b4-c1c8-4204-bea4-873af0fe7054
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3563c5b4-c1c8-4204-bea4-873af0fe7054
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9E2CEC972CEC6C29
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 423b-2bdf
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
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 111.279247284 = 119.485181952  grub/core.img                                  1
 111.277838707 = 119.483669504  grub/grub.cfg                                  1
 111.330592155 = 119.540313088  initrd.img-2.6.38-8-generic                    2
 111.277651787 = 119.483468800  vmlinuz-2.6.38-8-generic                       1

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=439f4c37-0bd0-44e0-9d7d-f622afd8bb5c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=3563c5b4-c1c8-4204-bea4-873af0fe7054 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=01c4e535-1452-40e3-8839-8ae2babed324 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=2ee08420-660e-4e57-bbac-ce03a6638587 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  1e 1b 85 00 37 21 00 00  00 00 00 00 02 00 00 00  |....7!..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 2b 3b 42 20  20 20 20 20 20 20 20 20  |..).+;B         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  cc 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 53 54 4c 44 52 20 20  |.f..f.F..STLDR  |
000001b0  20 20 20 20 0d 0a 49 6e  76 61 6c 69 64 20 53 79  |    ..Invalid Sy|
000001c0  73 74 65 6d 20 44 69 73  6b 20 6f 72 0d 0a 44 69  |stem Disk or..Di|
000001d0  73 6b 20 49 2f 4f 20 65  72 72 6f 72 0d 0a 50 72  |sk I/O error..Pr|
000001e0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 73  |ess a key to res|
000001f0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 55 aa  |tart..........U.|
00000200

Unknown BootLoader on sda4

00000000  01 0b 05 b7 45 fe 99 6a  0a 59 00 f7 f9 33 c9 8a  |....E..j.Y...3..|
00000010  6d f8 0f d0 b7 c9 0f b6  e0 06 fc c2 05 a0 08 62  |m..............b|
00000020  fa 81 06 ff 25 28 80 2b  c3 1b 2c bb 20 01 21 14  |....%(.+..,. .!.|
00000030  59 c2 1a 2e 14 20 25 0b  44 19 09 82 1f f7 d8 22  |Y.... %.D......"|
00000040  19 51 51 81 7d c2 08 42  4f 2c 8d 45 f8 c0 56 21  |.QQ.}..BO,.E..V!|
00000050  dd 58 ff 15 34 40 15 00  2a 18 61 02 6a da 00 e0  |.X..4@..*.a.j...|
00000060  50 75 80 3e 04 28 38 60  03 e2 15 7b 6c 07 7d 02  |Pu.>.(8`...{l.}.|
00000070  2c 33 04 00 05 f0 0f a0  38 0c 1d 20 10 30 b2 03  |,3......8.. .0..|
00000080  00 0b 14 2a 70 17 5d 33  d1 05 a0 3b 68 f1 e0 54  |...*p.]3...;h..T|
00000090  10 02 54 18 08 5d 00 c3  0d 02 6a 00 68 f0 31 e8  |..T..]....j.h.1.|
000000a0  01 56 8b 35 87 03 b0 02  10 ff da d6 90 03 dc b6  |.V.5............|
000000b0  04 26 01 c4 20 01 44 25  82 5c 32 3d 83 65 a4 00  |.&.. .D%.\2=.e..|
000000c0  83 00 0f 01 80 3d 74 52  6a 52 8d 45 a8 05 93 3a  |.....=tRjR.E...:|
000000d0  6c 80 02 85 c0 7e 3f 80  80 7d a8 00 74 39 6a 01  |l....~?..}..t9j.|
000000e0  81 01 00 8d 45 a4 50 e8  fe 5a ff 04 ff 83 c1 2b  |....E.P..Z.....+|
000000f0  74 23 8b 55 a4 00 3b 55  0c 7c 1b 39 55 10 60 7e  |t#.U..;U.|.9U.`~|
00000100  16 8b 4d 14 f0 22 c0 6b  02 64 89 11 41 3d 56 1f  |..M..".k.d..A=V.|
00000110  41 3d 50 4d f2 0d 10 1f  53 c0 4a 34 0a 57 53 68  |A=PM....S.J4.WSh|
00000120  22 08 04 00 00 10 2d ff  d6 8b 3d 81 f1 08 50 ff  |".....-...=...P.|
00000130  d7 53 68 41 35 01 d5 d2  00 80 da 00 42 da 00 81  |.ShA5.......B...|
00000140  d8 00 90 4e 01 42 1b 83  7d 0c 0a 75 06 83 80 7d  |...N.B..}..u...}|
00000150  10 00 74 1a ff 75 e0 32  43 42 1b 20 1a 35 f0 77  |..t..u.2CB. .5.w|
00000160  5e 40 1e 68 a1 d0 0c eb  0d 6a 01 51 07 15 31 07  |^@.h.....j.Q..1.|
00000170  40 33 c0 5d c2 10 00 b1  28 7d 00 0c 53 74 44 81  |@3.]....(}..StD.|
00000180  7d 0c 10 29 f0 3a 74 1b  80 00 9d f0 05 75 2e 00  |}..).:t......u..|
00000190  8b 45 14 0f b7 48 08 81  20 c9 00 00 02 05 a0 55  |.E...H.. ......U|
000001a0  eb 2d 94 6a ec d2 03 f4  a0 04 0d 00 30 02 7a 50  |.-.j........0.zP|
000001b0  04 01 b4 00 01 60 0e 10  07 61 3a e8 c0 2d 00 fe  |.....`...a:..-..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 4a 00 00 fe  |...........xJ...|
000001d0  ff ff 05 fe ff ff 02 78  4a 00 00 00 95 00 00 00  |.......xJ.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by primal woman on 2011-07-27
I think I did this the way you requested me to. While it may look like I know what I am doing, I do not! Ha. 

So I appreciate very much the detailed help instructions. 
FYI: I found another post where someone asked the person to do a "sudo update-grub" under a Code: thingy. His problem was solved, so I thought maybe the code thingy/place was terminal and it did not work for me. So if this is something I should try, inform me where/what this Code place is. 

Also FYI: I posted my question via laptop which runs windows and ubuntu 10.04. I installed 11.04 onto desktop and it works, but will not give option to boot windows (original posted problem). So I booted with ubuntu CD as requested above to get this info for you in my last post. (even though ubuntu does work on this desktop) I am on desktop as we speak with my laptop directions in this post next to me. No, I am not a geek. I ride horses for a hobby!

---

### Post by primal woman on 2011-07-27
One more thing that could be important. Before I did the result.txt stuff above with my boot up live CD, I hit F2 to look at BIOS settings, went into boot settings from there and saw 'fourth boot device' was disabled. I wrote it down AND changed it to 'hard disk'. Since it did not cure my problem (I don't think), I will be moving it back to disabled upon next boot up. I write this stuff down as a layman can screw up a computer big time I'm sure. Hence I don't let just anyone mess with my computer either, but I am not above messing up something! 
 (so the above results show that the fourth boot device is hard disk when in reality it should be/was disabled.)

I appreciate your help.

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> One more thing that could be important. Before I did the result.txt stuff above with my boot up live CD, I hit F2 to look at BIOS settings, went into boot settings from there and saw 'fourth boot device' was disabled. I wrote it down AND changed it to 'hard disk'. Since it did not cure my problem (I don't think), I will be moving it back to disabled upon next boot up. I write this stuff down as a layman can screw up a computer big time I'm sure. Hence I don't let just anyone mess with my computer either, but I am not above messing up something! 
 (so the above results show that the fourth boot device is hard disk when in reality it should be/was disabled.)

I appreciate your help.

Please make sure NOT to change your BIOS settings if you don't know what these settings are.

Boot Settings in BIOS should look like this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


Third and Forth Boot Devices will be used ONLY when needed. Above, is all what you need by default.

There are two things in Boot Settings in BIOS.

A- There is Boot Device
B- There is Hard Disk Boot Priority

Please don't be confused about these two.

Example for Hard Disk Boot Priority: 

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

You use that when you have TWO Hard Disk Drives and you want your BIOS to boot from HDD1 BEFORE it boots from HDD2.

Another Example:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

You see such a thing or similar to that when you want your BIOS to boot first from USB Drives.


It's very important to have some **basic knowledge** about BIOS, booting, etc.

I suggest to do some search on Google whenever you have some time OR you can ask her and we/I will be very glad to help :)

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> I think I did this the way you requested me to. While it may look like I know what I am doing, I do not! Ha. 

Yes, thanks a lot, you did it exactly the way we wanted :)

This Boot Script helps us to find out what is going on in similar cases. Unfortunately, we are not in front of your machine nor we can access it remotely so we can not do anything unless you be our eyes that see things clearly :)

With the result you posted in the previous post, we'll guide you through the steps you need to follow so that you can fix/solve your issue.

>  So I appreciate very much the detailed help instructions. 
That is exactly why I care to explain what is going on BEFORE guiding you through the steps to fix your issue.
It's very important to understand what is going on. I'm against to give instructions and ask the other person sitting some where to do this and that. I'm sure after this, you'll gain a great experience and you can avoid similar scenarios in the future.

Please don't hesitate to ask if you have any question :)

> FYI: I found another post where someone asked the person to do a "sudo update-grub" under a Code: thingy. His problem was solved, so I thought maybe the code thingy/place was terminal and it did not work for me. So if this is something I should try, inform me where/what this Code place is. 


```
sudo update-grub

```
is very important command. However, it's usually used when needed and in your case, this shouldn't be your first step. Why? because your GRUB2 which is Ubuntu's Boot Loader is NOT installed in the MBR of your main HDD (sda).

I know this must be a bit confusing so I'll go slowly.

First of all, you need to understand some basic stuff:

[B]GRUB2
[/B][https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[B]Booting
[/B][http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://en.wikipedia.org/wiki/Booting#Boot_loader](http://en.wikipedia.org/wiki/Booting#Boot_loader)

[B]MBR
[/B][http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

[B]Dual Booting
[/B][http://en.wikipedia.org/wiki/Dual_booting](http://en.wikipedia.org/wiki/Dual_booting)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

You can use: [www.google.com](www.google.com)
OR 
You can use: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

These are some basic info that you need to be aware of. Don't worry, you don't have to be an expert advanced user about these stuff I posted, but it's so good to know these things.


Now ...

In order to fix the issue, you need to re-install GRUB2 to the MBR of your sda (main HDD).

How can we do that?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

GRUB2 must be installed in [COLOR=Red]**sda **[/COLOR]*NOT ***sda1**

Once done, you'll be given the option at startup to choose which Operating System to boot into, Windows or Ubuntu.

Please ask if you have any question.

---

### Post by wildmanne39 on 2011-07-27
Hi amjjawad, very good instructions and explaining.

---

### Post by redbikemaster on 2011-07-27
Yes, I was learning things. Way to go, amjjawad.

---

### Post by primal woman on 2011-07-27
No kidding: amjjawad is good. 

But (ha!) I am not sure of my next move, hence another post. 
First I did change back that boot thing we talked about. I disabled it again. Not sure really if ubuntu is even booting up any more as I'm using my liveCD to boot it. I have followed your instructions to the methods of reinstalling Grub2 via Copy LiveCD Files. I typed in sudo fdisk -l and was too confused, so did the next option if user wasn't sure... sudo blkid. I save screen shot and will post it below to show what I found. I went NO further as I was too unsure. 
FYI: I saw the slave drive I have in there..it is about 13 G if I recall. I'm sure you see it. And my windows was alloted 115G and I gave my linux boot 1 G, swap 2500MB, ext4 / 5000MB and hard drive 72,982. I hope that info helps you to help me. So here is the screen shot I spoke of.

OK, nix that..can't copy a screen shot. There has to be a way I can insert this screen shot. I'll post this and go to my profile to see if I have a place I can 'load' downloads.

---

### Post by primal woman on 2011-07-27
[http://ubuntuforums.org/album.php?albumid=2387](http://ubuntuforums.org/album.php?albumid=2387)

I don't think it worked. But the picture is now in my profile and for public view. Thought I could put it right in here, but don't know how. 
[IMG]http://ubuntuforums.org/album.php?albumid=2387[/IMG]

---

### Post by wildmanne39 on 2011-07-27
Hi, look at my screenshot this is how you add one. Click the paper clip.

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> No kidding: amjjawad is good. 

At your service but I did not even start yet ;)


> But (ha!) I am not sure of my next move, hence another post.

Always ask if you are in doubt :) 


> First I did change back that boot thing we talked about. I disabled it again. Not sure really if ubuntu is even booting up any more as I'm using my liveCD to boot it. 

Best way to make sure everything is ok and as I explained before in my previous post, is to reboot and enter BIOS. 

Your CD/DVD Drive MUST be the first device to boot from.
Then, your Hard Disk Drive (HDD) must be the second device to boot from.
Same attached picture in my previous post.

It's very easy, you just need to know what are you looking for and what exactly you're doing.


> I have followed your instructions to the methods of reinstalling Grub2 via Copy LiveCD Files. I typed in sudo fdisk -l and was too confused, so did the next option if user wasn't sure... sudo blkid. I save screen shot and will post it below to show what I found. I went NO further as I was too unsure. 


[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

You can try this: Use Boot-Repair Graphical Tool

If it did not help then:

Copy LiveCD Files

Please read the instructions carefully and follow each one step by step.

Tell me where exactly you are confused and can't go further?


> FYI: I saw the slave drive I have in there..it is about 13 G if I recall. I'm sure you see it. And my windows was alloted 115G and I gave my linux boot 1 G, swap 2500MB, ext4 / 5000MB and hard drive 72,982. I hope that info helps you to help me. So here is the screen shot I spoke of.

Yes, I have seen it but quite honestly your partition scheme is a bit complicated for you. You can go much easier.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning)

First of all, you don't need /boot partition. This became history now.

You need 3 main partitions or you can go with 2 only.

You need:

Root Partition (/) and it must be ext4.
Home Partition (/home) - recommended - and it must be ext4 too.
SWAP Partition (Linux-Swap).

If you have 1GB RAM then make your swap 1-2GB of RAM. If you have more, just set your swap to the same size of your RAM.
If your RAM is 3GB for example, set swap partition to 3GB too.

I recommend to read the links I posted about partitioning ... these are very helpful :)

Sorry, I know I'm posting too much links but it's for your own good and you'll need them.

> 
OK, nix that..can't copy a screen shot. There has to be a way I can insert this screen shot. I'll post this and go to my profile to see if I have a place I can 'load' downloads.

Scroll down, you'll see "Additional Options". Scroll down a little bit and you'll see "Attach Files". There you go ;)

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> [http://ubuntuforums.org/album.php?albumid=2387](http://ubuntuforums.org/album.php?albumid=2387)

I don't think it worked. But the picture is now in my profile and for public view. Thought I could put it right in here, but don't know how. 
[IMG]http://ubuntuforums.org/album.php?albumid=2387[/IMG]

No, it's not clear, I'm afraid.
Please check my other post, I explained to you how to upload one :)

---

### Post by primal woman on 2011-07-27
:confused:
Anyone have a huge magnifying glass? I can't seem to figure out how to show you the picture of the screen shot big enough to see it. Can't even get it in here. I need chocolate. Sigh

While I believe you need/want more info, here is some of what I can see in that screen shot that I don't know what to do with/what info to retrieve from it to go on to the next instruction:
dev/sda1   is NTFS
       sda2  is FAT32
       sda3  is Linux
      sda4 is extended    78596097
      sda5 is linux swap / solaris   2440192
     sda6 is linux   4881408
      sda7 is linux    71272448

I added 'some' blocks as it looked like it may tell what size something is and give someone an answer! 

Thanks so much.

---

### Post by amjjawad on 2011-07-27
There you go ... attached is how to do it ;)

---

### Post by primal woman on 2011-07-27
Yep...am I all that and a bag of chips?

I think this will work....I've attached the file.

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> :confused:
Anyone have a huge magnifying glass? I can't seem to figure out how to show you the picture of the screen shot big enough to see it. Can't even get it in here. I need chocolate. Sigh

While I believe you need/want more info, here is some of what I can see in that screen shot that I don't know what to do with/what info to retrieve from it to go on to the next instruction:
dev/sda1   is NTFS
       sda2  is FAT32
       sda3  is Linux
      sda4 is extended    78596097
      sda5 is linux swap / solaris   2440192
     sda6 is linux   4881408
      sda7 is linux    71272448

I added 'some' blocks as it looked like it may tell what size something is and give someone an answer! 

Thanks so much.

I already have that info in the previous post ... the Boot Script Result :)

Thank you so much.

---

### Post by amjjawad on 2011-07-27
> **primal woman said:**
> Yep...am I all that and a bag of chips?

I think this will work....I've attached the file.

Ok, great job :D

Now, do me a favor and type

```
sudo gparted

```

In terminal.
Once GParted is up and running, make sure it shows "sda" on the right window of gparted.

Take a screenshot and upload it please.


By the way, is this a fresh new installation?
I'm thinking why not re-install all over again?

It's not a must, just a thought :)
I just don't like the Partitioning Scheme of yours. I want it to be much easier for you :)

---

### Post by oldfred on 2011-07-27
One more thing to fix to get windows working. Windows has to have its boot loader in the partition boot sector. But when you installed grub2's boot loader to sda1 not sda you overwrote the windows boot loader. Windows keeps a backup so you can just restore the backup with testdisk.

```
sda1: ________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   [COLOR=Red]Grub2 (v1.99) is installed in the boot sector[/COLOR] of sda1 
                       and looks at sector 233369446 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/grub on this drive. No errors found in 
                       the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
  If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use a windows XP disk and use its repair command line to run fixBoot. More info here:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by YesWeCan on 2011-07-27
Hi there.
The reason you cant boot XP is because you installed the grub boot code inside the XP partition and overwrote the XP boot code. You will need to repair your XP boot code. have you got an XP CD?

Before you repair XP, 
You have two disks. I recommend installing grub to the MBR of sdb so that it never clashes with the MBR on sda that Windows expects to see. Then set your bios to boot first from sdb.
Boot into ubuntu as usual. Then run
sudo grub-install /dev/sdb

Then do the XP repair. Then set the bios to boot sdb first. Then boot into ubuntu and run
sudo update-grub
To add XP to the grub boot menu

I don't see any need to reinstall ubuntu. But you have to repair XP.

---

### Post by primal woman on 2011-07-27
You mentioned ...."You can try this: Use Boot-Repair Graphical Tool". I opted to go what seemed easier as I have the bootable CD. 

And I read the instructions, but of course even though I wished I was more versed on this stuff, I am not and have a plate full of life in other areas. I can't wait until this is done! Seems it would be so easy to just do it on the phone with someone. Bet it would take 10 minutes or less and I have devoted hours as well as you having done so likely! 


"Tell me where exactly you are confused and can't go further?"

I am not sure of the partition to look for. Not even sure of the approximate size I'm looking for. I'm getting too confused! Ha. Like overload...my eyes are glazed. If you have ever been a teacher, you'll know what I'm talking about. 
So size...to move onto the next instruction which would be foreign language to me unless I master the last instruction...I need to know what size I'm looking for. Then it asks to mount the partition sudo mount /dev/???/mnt. I am guessing once I know what to put in place of my question marks, I'll be on my way again! Sigh. 

And yes, when it gets to be so many links and stuff for someone not familiar enough, it is too overwhelming. Have 14 pages open on laptop for instructions while working on desktop. 

Oh..and on my boot sequence. I did not change anything and not sure I should. I'll check that post in more detail from you at some other time if I need to. I'll get frazzled if I delve into something else. At least I think this is an unrelated problem anyway.

---

### Post by primal woman on 2011-07-27
> **amjjawad said:**
> Ok, great job :D

Now, do me a favor and type

```
sudo gparted

```In terminal.
Once GParted is up and running, make sure it shows "sda" on the right window of gparted.

Take a screenshot and upload it please.


By the way, is this a fresh new installation?
I'm thinking why not re-install all over again?

It's not a must, just a thought :)
I just don't like the Partitioning Scheme of yours. I want it to be much easier for you :)


Posts are coming in fast here. Not had time to read them and I end up submitting answer too slow. But just read your post here. YES, it is so new I have only booted onto it once. When I booted and found it did not give me a windows option, I called my daughter, skyped with her on her phone and my laptop, skyped with other daugher while she is in Japan skyping with someone in states...holy smoley..I'm too old for this! Ha   Anyway, if only those two were closer. I'd go eat chocolate and let you guys talk to them. Bet they could do it.

So I can re install OVER top of my current brand new linux? OK. sounds great. So...sending this off for now. Going back to make sure I've read all posts. Then will re install ONLY after you are able to make sure I'm doing it right. 

Also, you asked for another terminal screen shot. I'll go do that now.

---

### Post by amjjawad on 2011-07-27
I'm so sorry, I know I must SLOW DOWN but it's a bad habit of me and I really need to get rid of it.

I suggest to take a break from that. 
If you feel that way, then you will not be able to focus and do things correctly. 

Take my advice, have some rest and we can do it later.

If you want, take a short break and come back but please let me know if you want to do it now. It's 3:30am here and I'm so tired but can't sleep and leave all this :) yes, yet another habit.

There are many steps you need to do. I missed something, thanks to oldfred to highlight it for us. 

You need to fix Windows Boot Loader First

Then

You need to re-install GRUB2.

Also, I'm not sure whether it's good idea to change your partition scheme or leave it as it's?

I think it's better to delete these partitions and start all over but I'm not sure if this is a good idea, specially you're getting too confused.

---

### Post by primal woman on 2011-07-27
here is my gparted screenshot.

---

### Post by YesWeCan on 2011-07-27
> **amjjawad said:**
> I'm so sorry, I know I must SLOW DOWN but it's a bad habit of me and I really need to get rid of it.

I suggest to take a break from that. 
If you feel that way, then you will not be able to focus and do things correctly. 

Take my advice, have some rest and we can do it later.

If you want, take a short break and come back but please let me know if you want to do it now. It's 3:30am here and I'm so tired but can't sleep and leave all this :) yes, yet another habit.

There are many steps you need to do. I missed something, thanks to oldfred to highlight it for us. 

You need to fix Windows Boot Loader First

Then

You need to re-install GRUB2.

Also, I'm not sure whether it's good idea to change your partition scheme or leave it as it's?

I think it's better to delete these partitions and start all over but I'm not sure if this is a good idea, specially you're getting too confused.
The ubuntu installation is more complex than it needs to be but it works fine so no need to add the complication of a reinstall.
Grub2 is easier to reinstall from within the working ubntu. Once XP is repaired the working ubntu wont be bootable. So reinstall grub before fixing XP.
There will be future problems if grub is installed to sda. There will be clashes with XP. So install grub to sdb and have the bios boot off sdb. This also means ubuntu will boot ok after xpis fixed.

---

### Post by primal woman on 2011-07-27
> **amjjawad said:**
> I'm so sorry, I know I must SLOW DOWN but it's a bad habit of me and I really need to get rid of it.

I suggest to take a break from that. 
If you feel that way, then you will not be able to focus and do things correctly. 

Take my advice, have some rest and we can do it later.

If you want, take a short break and come back but please let me know if you want to do it now. It's 3:30am here and I'm so tired but can't sleep and leave all this :) yes, yet another habit.

There are many steps you need to do. I missed something, thanks to oldfred to highlight it for us. 

You need to fix Windows Boot Loader First

Then

You need to re-install GRUB2.

Also, I'm not sure whether it's good idea to change your partition scheme or leave it as it's?

I think it's better to delete these partitions and start all over but I'm not sure if this is a good idea, specially you're getting too confused.


Well, I had no idea I was talking with someone when it is so late for you. Wow, hey, we can wait. 
UM, I'll go through the posts for sure. You can go if you wish. I can reload this linux as once my daughter gave me a web site, it turned out to be relatively easy...um...and maybe wrong? (sheepish grin here) 
let me see if I can find the site...
[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

So with that said. This is the link I used when I got so confused and called daughter.

---

### Post by amjjawad on 2011-07-27
> **YesWeCan said:**
> The ubuntu installation is more complex than it needs to be but it works fine so no need to add the complication of a reinstall.
Grub2 is easier to reinstall from within the working ubntu. Once XP is repaired the working ubntu wont be bootable. So reinstall grub before fixing XP.
There will be future problems if grub is installed to sda. There will be clashes with XP. So install grub to sdb and have the bios boot off sdb. This also means ubuntu will boot ok after xpis fixed.

Yes and your post added more complications to the complicated issue so thank you :D

---

### Post by wildmanne39 on 2011-07-27
Hi, oldfred is very good with these problems if you want to fix the issue instead of reinstalling, I would do what he said, it will be the shortest and least painful way to do it.

I agree with my friend amjjawad it might be best to take a short break and then come back to it.

---

### Post by amjjawad on 2011-07-27
> **wildmanne39 said:**
> Hi, oldfred is very good with these problems if you want to fix the issue I would do what he said, it will be the shortest and least painful way to do it.

I agree with my friend amjjawad it might be best to take a short break and then come back to it.

I feel good when oldfred steps in :) NO ONE here is better than him in this, with all due respect to all my friends and posters here :)

I think it's better to take a break from this.
The Original Poster is having hard time to just read our posts because we are posting TOO FAST and now, we have more than 3-4 posters at the same time so better to take a break and slow down.

No offense to anyone ... I just want to help the lady as much as I could.

---

### Post by YesWeCan on 2011-07-27
@primal woman
This is a very simple problem to fix. The most complicated part is repairing XP. Its easiest if you have an XP CD but you can do it as per oldfred's post.
When you repair XP only XP will boot unless you reinstall grub first, as i have described.

---

### Post by primal woman on 2011-07-28
New options: ??

I am wondering; Can I simply start all over and reformat xp, then load  ubuntu all over again? Would it be easier/better to do that? I have no  important stuff I'll lose on windows. I keep all my personal on an  external. I just reformatted it in January and while loading div x,  skype, google earth etc etc is not fun; it won't be as bad maybe as  messing with this other problem. By the way, it won't boot up at all  now. Not sure why that would be when it has done it once or maybe twice  before. (then it was always with the CD with you guys.) 

Ha, and people ask me why I have to have a laptop AND  a desktop! I should ask them why they need a right shoe AND a left shoe. 

If you think that reformatting is best, perhaps I could have one link  from you that tells the Correct way to partition and load ubuntu. OR  maybe I should try the first option (load ubuntu next to windows) and  this time it may give me the option to cut some partitioning off for  ubuntu? (this is why I chose that third option called 'something else';  because when I loaded ubuntu 10.04 onto laptop, it did not give me  options to partition and gave ubuntu a small space. SO with that asked,  now I wonder; AFTER I get desktop fixed, can I fix my laptop? Can I load  this CD of 11.04 onto laptop and give it a partition? I would guess so.  Just would want to know the best way. After seeing 11.04 is so  different than 10.04, no need of having different ones on both  computers. I'd rather have the same versions.

I'll be back in about nine hours to see what you guys think. I have to go for now. Once this is done and I no longer have to worry about it, I am anxious to peruse this web site and have a look around. I had never seen it before I had a problem as is likely for many people! Since I love coffee :) and I have really liked ubuntu on my laptop :P, it is such a good combination! 

Thanks for all your help.

---

### Post by amjjawad on 2011-07-28
> **primal woman said:**
> I am wondering; Can I simply start all over and reformat xp, then load  ubuntu all over again? Would it be easier/better to do that? I have no  important stuff I'll lose on windows. I keep all my personal on an  external. I just reformatted it in January and while loading div x,  skype, google earth etc etc is not fun


If you really don't need XP, then definitely it would be much easier for YOU to wipe your HDD and start all over again.

For me, it's fun in any possible scenario ;)


> By the way, it won't boot up at all  now. Not sure why that would be when it has done it once or maybe twice  before. (then it was always with the CD with you guys.) 

We'll fix that either by fixing MBR and re-installing GRUB2 (the long way we discussed yesterday) OR but formatting the whole HDD and start all over again with ONLY Ubuntu to be installed :)



> Ha, and people ask me why I have to have a laptop AND  a desktop! I should ask them why they need a right shoe AND a left shoe. 

+1
Totally agreed.


> If you think that reformatting is best, perhaps I could have one link  from you that tells the Correct way to partition and load ubuntu. OR  maybe I should try the first option (load ubuntu next to windows) 

It's not what we think, it's what you think and want. Again, either ways, I'm more than ready and I guess same goes with others here.


> [COLOR="Red"]Can I load  this CD of 11.04 onto laptop and give it a partition? I would guess so.  Just would want to know the best way. After seeing 11.04 is so  different than 10.04, no need of having different ones on both  computers. I'd rather have the same versions.[/COLOR]

This is totally different story. Basically, you can but if you really want my advice, I'd recommend NOT to do that. It's much better to keep one machine with 10.04 and the other with 11.04.
Why? let's talk about it later ;)

> I'll be back in about nine hours

As agreed, just let me know :)

---

### Post by YesWeCan on 2011-07-28
> **primal woman said:**
> I am wondering; Can I simply start all over and reformat xp, then load  ubuntu all over again? Would it be easier/better to do that?
Reinstalling XP and Ubuntu will take 2 or 3 hours. Probably longer with downloads and app reinstalls and so on.
Repairing XP's boot and Grub will take 10-20 minutes.

Your choice. ;)


It's very easy. You have to do two things. Stick Grub on the MBR of sdb and repair XP's boot. You do the former with a one-liner in Ubuntu (or via live CD if you cannot boot Ubuntu now). You fix XP by booting its CD and selecting repair (see oldfreds link).

I'd say it is a good idea that you learn how to repair XP because you are likely to encounter this problem again.


On the subject of starting from scratch. You end up with a significantly easier system to maintain if Ubuntu and Windows are installed on separate disks. This way there is no conflict between their boot-loaders and MBRs. Is this an option for you?

---

### Post by primal woman on 2011-07-28
Hi yeswecan. If it were only that easy. Sounds easy. I'm game, but amjjawad just tried helping me and we could not get this computer to even boot up unless it was a linuxCD. It won't boot by itself now and it won't boot with reformat xp disc. Went to boot sector and could not move items around. But I never moved those to start with, so not sure what happened. 

Anyway, I then did a shut down out of live cd and it gave me a page full of white lettering on black screen! Way too many words to write down with 'ok' on the very right side of page. So I wrote down the last sentence: 'hecking for running unattended upgrades: init: plymouth-splash main process (4367) killed by TERM signal' Oh yes, that makes a lot of sense to me, how about anyone else? I hit enter and it shut down. 

Sigh. Well, I hate to reformat the whole thing again due to time it will take. But it takes so much time to try to figure out what oldfred and yeswecan mean to do those things.

---

### Post by YesWeCan on 2011-07-28
Do you have your Windows XP CD? Im not sure what you mean by "reformat xp disc".
If so, boot it and choose the repair option. Do what it says here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) in the section "How to restore the Windows XP bootloader". There are just three things to type.

If you can do this you should be able to boot XP again.

Then you just have to boot the Ubuntu CD to reinstall grub. This is very easy and anyone can guide you.

BTW you can just ignore the text spew when you shutdown the live CD.

[edit] Hey I made a mistake! I thought you had two disks but you only have one. D'oh. I mistook sdb for a HD instead of your live Ubuntu disk. Pretty basic goof. Anyhow, it makes no difference, you just need to install Grub to sda after you have repaired XP. :)

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Do you have your Windows XP CD? Im not sure what you mean by "reformat xp disc".
If so, boot it and choose the repair option. Do what it says here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) in the section "How to restore the Windows XP bootloader". There are just three things to type.

If you can do this you should be able to boot XP again.

Then you just have to boot the Ubuntu CD to reinstall grub. This is very easy and anyone can guide you.

BTW you can just ignore the text spew when you shutdown the live CD.

[edit] Hey I made a mistake! I thought you had two disks but you only have one. D'oh. I mistook sdb for a HD instead of your live Ubuntu disk. Pretty basic goof. Anyhow, it makes no difference, you just need to install Grub to sda after you have repaired XP. :)


Hi, 


(this next paragraph could be what you were referring to in your last post and clarified, so nix it if so.)
You stated in your other post: "On the subject of starting from scratch. You end up with a significantly  easier system to maintain if Ubuntu and Windows are installed on  separate disks. This way there is no conflict between their boot-loaders  and MBRs. Is this an option for you?"
I am not sure what you mean 'separate disks'. Disks could be CD's. If that is what you mean, of course I have both the CD's. If you mean on the computer, yes, I installed ubuntu next to windows not inside of windows. But of course with that being said...something went awry. I either did something wrong, followed the advice from a web site that was wrong and/or who knows. Here is the site I used to install it: 
[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

What is a reformat xp disc? I have my emachine XP media center CD/DVD that I have used to reformat my computer like it was purchased right off the shelf! Ha, well, I am aware it holds all of your old stuff in there too! I'm sure you know what it is, it likely is just that I worded it wrong for you to know what I meant. 

I tried to boot from that to enable AJ and I to fix it as you instruct, BUT it would not boot from it. I tried both the DVD slot as well as my CD slot. Neither would boot. BUT then put my ubuntu CD in and it did boot. The emachine CD/DVD is not likely faulty. Not sure what is wrong. I used that to reformat this computer in January of this year. 

New: It worked this time...to boot from DVD drive; my emachine xp CD/DVD, BUT hitting 'r' brought me to another request to hit R so I did. It took me to where it was giving options of two different restores; not what we want. So I 'quit' then it went back and I hit 'r'. It gives me 'pres R for standard emachine system recovery options. 
Press Q to quit and boot the OS on hard disk 

and instead I thought maybe I am just supposed to type in 'fixboot' but it says please confirm with 'y' to format drive and install new. 
Well, that is not what I am trying to do! Trying to follow the instructions on your page you gave me above.

---

### Post by primal woman on 2011-07-29
I think you may ask if I have just a xp windows CD. 
NO, all I have is the emachine xp media center edition restore CD/DVD. 

It has everything in there to reinstall. (seemingly except repair, ha)

---

### Post by amjjawad on 2011-07-29
> **primal woman said:**
> I think you may ask if I have just a xp windows CD. 
NO, all I have is the emachine xp media center edition restore CD/DVD. 

It has everything in there to reinstall. (seemingly except repair, ha)

Hi again,

When you say "emachine" so do you mean this: [http://www.emachines.com/](http://www.emachines.com/)

Because we don't have such a thing where I live so I was wondering what was that?!

It might has a restore function/program/whatever but does it has the repair function, the same that exist in Windows XP CD? I'm not sure about that.

The ability of reformatting and re-installing XP from that CD doesn't really mean it has the ability to restore the MBR using fixboot and fixmbr. I'm just guessing here because I never heard of that CD which you have. But apparently, that CD has no such function, otherwise you would have found it some where. 

I'm searching on google now to find a way to get around that.

Will get back to you hopefully shortly :)

---

### Post by YesWeCan on 2011-07-29
Hmm. I'm trying to think of a way to fix this that doesn't require reinstalling everything from scratch. If you had a regular XP CD you could. The CD you have may only do complete reinstalls but I am not familiar with it. What is the model number of your PC - I'll look it up?

The problem here is that a tiny piece of code, less than 512 bytes, has been overwritten. The solution oldfred posted is a means to restore that code from an existing backup of it inside the XP partition itself. I have never done this myself. It is actually easy to do but hard to describe! Let me try and you can try it if you want...it will just take a few minutes and may save the day:

[COLOR=DarkGreen]Boot into Ubuntu on your hard disk OR live CD and open a command terminal
Resize the terminal so it is about twice as big as normal.
then run
**sudo apt-get install testdisk**  and say y to any questions
**sudo testdisk**
Now you are in the testdisk program. Use the arrow keys to move up and down, or right and left among the menu items and enter to select.
On the first screen select 'No Log'
On the next screen select your hard disk (should be /dev/sda) Press enter to proceed to the next screen
Now select 'Intel'
Now select 'Advanced'

You should now be on a screen that lists your partitions. The first in the list is probably the one you want to select: it should say something like 'P FAT32 LBA...' (see my image below). Use the up/down arrows to select this partition. Then use the right/left keys to select the 'Boot' item at the bottom of the screen. Press enter.

Now you have a screen that describes the XP partition and the boot sector and backup boot sector conditions. Hopefully the 'Backup boot sector' shows 'OK'. If so, use the right arrow key to select 'Backup BS' at the bottom. Press enter. It will ask you to confirm so press Y. This should cause it to restore the XP boot sector. Now you quit testdisk by pressing 'q' several times or just closing the command terminal.

Now you can try rebooting.[/COLOR]

---

### Post by YesWeCan on 2011-07-29
> **primal woman said:**
> You stated in your other post: "On the subject of starting from scratch. You end up with a significantly  easier system to maintain if Ubuntu and Windows are installed on  separate disks. This way there is no conflict between their boot-loaders  and MBRs. Is this an option for you?"
I am not sure what you mean 'separate disks'. 
I meant hard disk drives. I am not sure whether you have a laptop or a desktop PC. Sometimes people have more than one hard disk and usually any hard disk can be used for Grub, even if it is not the same HD that Ubuntu is on. I gather you only have one HD so it is not relevant and you must install Grub to the MBR of that one disk.

---

### Post by YesWeCan on 2011-07-29
> **amjjawad said:**
> The ability of reformatting and re-installing XP from that CD doesn't really mean it has the ability to restore the MBR using fixboot and fixmbr. I'm just guessing here because I never heard of that CD which you have. But apparently, that CD has no such function, otherwise you would have found it some where. 

I'm searching on google now to find a way to get around that.
Yes, it would be useful to know whether the recovery CD can fix the boot record. I have never used one of these CDs so I have no idea.

---

### Post by amjjawad on 2011-07-29
> **YesWeCan said:**
> I have never used one of these CDs so I have no idea.

... Plus I never heard about that :)

---

### Post by amjjawad on 2011-07-29
Since I haven't heard and never used emachine Windows XP Media Center CD, I have consulted a friend here on the forum and he suggested the following:

As long as the whole issue is about to fix the MBR then, this can be done from Ubuntu LiveCD.

This is how:

1- Insert Ubuntu LiveCD into your CD/DVD Drive

2- Restart your machine

3- Choose "Try Ubuntu without installation"

4-From Terminal, please run this command:

```

sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```5- After you run the second command "sudo lilo -M /dev/sda mbr", you will be advised that more  commands need be run to complete the lilo installation. Those should **NOT**  be run; they are not needed.

6- Restart your machine.

7- Windows should boot fine "if' Windows system files are fine and not damaged.


If the above is done successfully, then that would be our first step to fix the issue.

The next step would be of course to re-install GRUB2.

---

### Post by primal woman on 2011-07-29
p { margin-bottom: 0.08in; }  Yes, that link for emachines is the kind of computer this is.  
  And yes, my restore CD/DVD evidently has EVERYTHING on it to restore except fixing stuff!  
 [COLOR=Black]
[/COLOR] 
 [COLOR=Black]Model number of my PC: T6524[/COLOR]
 [COLOR=Black]
[/COLOR] 
 [COLOR=Black]yeswecan: I just did this in terminal: sudo apt-get install testdisk and this was the answer: 
[/COLOR]
[COLOR=Black]reading package lists...done[/COLOR]
 [COLOR=Black]building dependency tree[/COLOR]
 [COLOR=Black]reading state information..done[/COLOR]
 [COLOR=Black]E: unable to locate package testdisk[/COLOR]
 

 [COLOR=Black]Concerning hard discs: maybe you mean hard drives C and D on this desktop with problems. XP is on C and D is, I think a restore area.[/COLOR]


[COLOR=Black]Have we done everything? Sure seems like it. buy a new computer? Haven't done that yet. This is crazy. 
[/COLOR]


[COLOR=Black]Unless I can get someone on a telephone to walk me through the CORRECT things to do, then my next option is to reformat and start all over. BUT I don't know if completely reformatting my emachine with my CD/DVD will wipe out this ubuntu too. I would want it to so I can start all over or give up and just have windows. I've about had enough. 
 [/COLOR]

---

### Post by YesWeCan on 2011-07-29
> **amjjawad said:**
> 7- Windows should boot fine "if' Windows system files are fine and not damaged.
Good idea, but unfortunately, the existing MBR is fine and the sda1 PBR is corrupted. So fixing the MBR with lilo won't help.

The way it works is that every disk has an MBR at the very front, in the first 512 bytes (usually 1 sector). This has boot code and a partition table that points to a "Partition Boot Record" of an active partition. The PBR is also 512 bytes and has more code for booting the proper boot-loader for the OS, in this case XP. The PBR is in sda1 and it is this that has been overwritten by Grub.

Grub does not comply with the MBR system otherwise the Ubuntu partition's PBR would be booted directly in the same way as XP. Instead, Grub replaces the MBR code completely and ignores the partition table and boots the Grub boot-loader only.

In this case, the Grub MBR replacement code was put in place of the sda1 PBR rather than in place of the MBR.

The whole thing is complicated and prone to screw-ups. It would be much better IMO if Grub used PBR code rather than overwriting things. But that's unlikely to change any time soon.

---

### Post by amjjawad on 2011-07-29
> **primal woman said:**
> Yes, that link for emachines is the kind of computer this is.  
  And yes, my restore CD/DVD evidently has EVERYTHING on it to restore except fixing stuff!  

Apparently, it can't fix MBR.

 > [COLOR=Black]reading package lists...done[/COLOR]
 [COLOR=Black]building dependency tree[/COLOR]
 [COLOR=Black]reading state information..done[/COLOR]
 [COLOR=Black]E: unable to locate package testdisk[/COLOR]
 
Were you connected to the internet while doing so?


 > [COLOR=Black]Concerning hard discs: maybe you mean hard drives C and D on this desktop with problems. XP is on C and D is, I think a restore area.[/COLOR]

Hard Disk Drive (HDD) is the storage device where your Operating System and Personal Files are stored. Even if you turn your machine off, these files won't disappear. Unlike RAM, once you turn your machine OFF, all the files in RAM will be gone.


> Have we done everything? Sure seems like it. 

[COLOR=Black]Not yet. Check my previous post please!


[/COLOR]> buy a new computer? Haven't done that yet. This is crazy. 
Too early for that.


> 
[COLOR=Black]Unless I can get someone on a telephone to walk me through the CORRECT things to do, then my next option is to reformat and start all over. BUT I don't know if completely reformatting my emachine with my CD/DVD will wipe out this ubuntu too. I would want it to so I can start all over or give up and just have windows. I've about had enough. 
 [/COLOR]

I'm ready if you're :)

IF that would be your decision, as explained before, using Ubuntu LiveCD, you can wipe the whole thing and install Ubuntu ONLY.

OR

You can wipe everything and install XP - using that recovery CD and then install Ubuntu.

Note that, the first choice will take MAX 45mins while the second might take longer.

The third option is to try one more time with Lilo Method and see how things will go from there.

The fourth option is to try testdisk.

---

### Post by oldfred on 2011-07-29
To be able to download testdisk you have to enable universe as a source of software.

enable the "universe" repository to download testdisk
(Not sure of exact procedure with 11.04).
System, Administration, Update Manager, Settings, Ubuntu Software Tab, add check for Universe
Older version
System>Administration>Software Sources>Ubuntu Software.

Edit - also in synaptic:
system, Administration, synaptic. Click on settings on top menu bar and choose repositories. Add check 
Then choose testdisk

If you are using a windows repair CD, it is not just fixMBR but also fixBoot as fixboot is the one that repairs the partition boot sector.

---

### Post by YesWeCan on 2011-07-29
> yeswecan: I just did this in terminal: sudo apt-get install testdisk and this was the answer: 

reading package lists...done
building dependency tree
reading state information..done
E: unable to locate package testdisk
Did you do this using the live CD? If so try again using the Ubuntu that is installed. The problem may be be that testdisk is not listed in software sources that come as standard with the CD. It will work if you try it using the installed Ubuntu.

---

### Post by primal woman on 2011-07-29
yeswecan:
First off, I am not sure I posted that I tried oldfred's advice in ubuntu and it did not work. 

Anyway, next subject. I posted above and found your new post. I've done the first command, figured I was to hit enter as there is no way that I know of to get the second command done without hitting enter. I feel stupid, but hey, trying to follow directions exactly! 

sudo apt-get install lilo 
sudo lilo -M /dev/sda mbrSo did the first and it says packages will be installed mbr (this is not verbatum as it is a lot of writing)
suggested packages: 
lilo-doc
new packages
lilo mbr
I hit y to continue....
more stuff now...I'm going to post this and then get onto this forum on my desktop in case I can copy/paste some of this stuff....

---

### Post by amjjawad on 2011-07-29
> **primal woman said:**
> Anyway, next subject. I posted above and found your new post. I've done the first command, figured I was to hit enter as there is no way that I know of to get the second command done without hitting enter. I feel stupid, but hey, trying to follow directions exactly! 

sudo apt-get install lilo 
sudo lilo -M /dev/sda mbrSo did the first and it says packages will be installed mbr (this is not verbatum as it is a lot of writing)
suggested packages: 
lilo-doc
new packages
lilo mbr
I hit y to continue....
more stuff now...I'm going to post this and then get onto this forum on my desktop in case I can copy/paste some of this stuff....

Run the first command

then

Run the second one

HOWEVER, this method might NOT work ... check YesWeCan's post.

---

### Post by YesWeCan on 2011-07-29
Yes, when I write a command like
[COLOR="Navy"]sudo testdisk[/COLOR]
I also mean press enter afterwards.

The lilo program won't help because it repairs the wrong thing. Otherwise oldfred or I would have suggested this as the first thing to do.

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Did you do this using the live CD? If so try again using the Ubuntu that is installed. The problem may be be that testdisk is not listed in software sources that come as standard with the CD. It will work if you try it using the installed Ubuntu.

Yes, I did this with the live CD as my installed ubuntu quit loading/booting after only the first or second boot....what now....3 days ago! 

OK, I have this...
LILO configuration                                                        &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It seems to be your first LILO installation. It is absolutely necessary   &#9474; 
 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474; 
 &#9474; /sbin/lilo after this.                                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; LILO won't work if you don't do this.   

so just how do I run liloconfig(8) etc? 
I know how to run in windows, but not ubuntu yet.

---

### Post by YesWeCan on 2011-07-29
> **primal woman said:**
> Yes, I did this with the live CD as my installed ubuntu quit loading/booting after only the first or second boot....what now....3 days ago!
Well, nobody said linux was easy! :p
Actually, some people say that but I think linux is quite tricky in places unless you are a geek.

oldfred's last post says how to enable the "universal" source so you can find testdisk using the live CD. Otherwise you have to try to boot your installed Ubuntu and do it. I hope you can make this work because the testdisk method will save some time.

(Just exit from your lilo install. It really wont help)

---

### Post by amjjawad on 2011-07-29
> **YesWeCan said:**
> Good idea, but unfortunately, the existing MBR is fine and the sda1 PBR is corrupted. So fixing the MBR with lilo won't help.

The way it works is that every disk has an MBR at the very front, in the first 512 bytes (usually 1 sector). This has boot code and a partition table that points to a "Partition Boot Record" of an active partition. The PBR is also 512 bytes and has more code for booting the proper boot-loader for the OS, in this case XP. The PBR is in sda1 and it is this that has been overwritten by Grub.

Grub does not comply with the MBR system otherwise the Ubuntu partition's PBR would be booted directly in the same way as XP. Instead, Grub replaces the MBR code completely and ignores the partition table and boots the Grub boot-loader only.

In this case, the Grub MBR replacement code was put in place of the sda1 PBR rather than in place of the MBR.


Totally understood ;)


> The whole thing is complicated and prone to screw-ups. It would be much better IMO if Grub used PBR code rather than overwriting things. But that's unlikely to change any time soon.
IMHO, there must be some explanation during the Installation so users will be aware and informed. Some few lines telling the user what will happen if GRUB2 will be installed in MBR and what will happen if GRUB2 will be installed in a partition. Not everyone knows that.

I had to do many tests in the past to understand that but for new comers, how would they know? definitely they won't UNLESS things will be broken.

---

### Post by primal woman on 2011-07-29
> **oldfred said:**
> To be able to download testdisk you have to enable universe as a source of software.

enable the "universe" repository to download testdisk
(Not sure of exact procedure with 11.04).
System, Administration, Update Manager, Settings, Ubuntu Software Tab, add check for Universe
Older version
System>Administration>Software Sources>Ubuntu Software.

Edit - also in synaptic:
system, Administration, synaptic. Click on settings on top menu bar and choose repositories. Add check 
Then choose testdisk

If you are using a windows repair CD, it is not just fixMBR but also fixBoot as fixboot is the one that repairs the partition boot sector.


Just found this post and others that were all posted as I was working on posting! Missing too much perhaps. 
I take it the above directions are for the installed ubuntu? I can't use my installed ubuntu or my installed windows. they won't boot.

---

### Post by YesWeCan on 2011-07-29
> **primal woman said:**
> Just found this post and others that were all posted as I was working on posting! Missing too much perhaps. 
I take it the above directions are for the installed ubuntu? I can't use my installed ubuntu or my installed windows. they won't boot.
These instructions will work in the live CD Ubuntu too.
You need to tick the "universe" source (see image). Then close those windows

Then in a console:
[COLOR="Navy"]sudo apt-get update[/COLOR]

Then the testdisk install commands.

---

### Post by primal woman on 2011-07-29
how do I find 'software sources'?

---

### Post by YesWeCan on 2011-07-29
Sorry. You need to click on "System" at the top left of your screen. Then on the menu move your mouse over the word "Administration" and then click on "Update Manager".
This will give you a window which has a "Settings..." button bottom left. Click this.
Then make sure you have selected the first tab on the left.

---

### Post by primal woman on 2011-07-29
AT the top left of my screen I have the ubuntu circle that does not bring up 'system', I haver file, edit and stuff if my mouse is up there, I have on left column install, home folder, firefox and etc on down the line. WHERE is system?

---

### Post by YesWeCan on 2011-07-29
> **amjjawad said:**
> IMHO, there must be some explanation during the Installation so users will be aware and informed. Some few lines telling the user what will happen if GRUB2 will be installed in MBR and what will happen if GRUB2 will be installed in a partition. Not everyone knows that.

I had to do many tests in the past to understand that but for new comers, how would they know? definitely they won't UNLESS things will be broken.
You are absolutely right. Especially for Windows users who have not used linux. Windows mercifully hides all this machinery from the user so how would they know what to expect? They certainly don't expect it to break anything.

---

### Post by drs305 on 2011-07-29
> **YesWeCan said:**
> You are absolutely right. Especially for Windows users who have not used linux. Windows mercifully hides all this machinery from the user so how would they know what to expect? They certainly don't expect it to break anything.

The Grub 2 devs have taken steps to avoid this. Initially they issued a warning, and later even removed the option to install G2 to a partition in during G2's installation via command line. Unfortunately Ubuntu hasn't quite caught up in some cases.

BTW, I had initially replied to 'ajjawad' via PM without seeing the post and was responsible for the 'lilo' suggestion. Apologies to all.

---

### Post by YesWeCan on 2011-07-29
> **primal woman said:**
> AT the top left of my screen I have the ubuntu circle that does not bring up 'system', I haver file, edit and stuff if my mouse is up there, I have on left column install, home folder, firefox and etc on down the line. WHERE is system?
Oh, you are using 11.04 with the new Unity desktop, aren't you?

Ok, you need to click on the circle with a short line throu the top of it at the far top right. Then click on "system settings". Then find the "Update Manager" icon and click it.

---

### Post by YesWeCan on 2011-07-29
> **drs305 said:**
> BTW, I had initially replied to 'ajjawad' via PM without seeing the post and was responsible for the 'lilo' suggestion. Apologies to all.
Hi, no worries. This thread is reminding me just how complicated linux can be for a novice if they need to do something unusual. By the time we sort this out the quick way it will have been quicker to reinstall both OS's from scratch. ;)

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> These instructions will work in the live CD Ubuntu too.
You need to tick the "universe" source (see image). Then close those windows

Then in a console:
[COLOR=Navy]sudo apt-get update[/COLOR]

Then the testdisk install commands.


OK, checked 'universal' and left others as is. So it updated...and now wants me to install...WHICH means 227 updates selected and 243MB will be downloaded. SO...unless you can show me/tell me which ONE I need..I am shut down for the day; because the only way I can get internet other than dial up in this remote area is satelite hughes net and it only allows me 200MB a day with a download speed of...um..I forgot..its slowest. BUT it is free in the middle of the night....so of course I am not clicking install updates at this time.

---

### Post by YesWeCan on 2011-07-29
No, don't do the install or we'll be here all night. It isn't necessary at all. Just close the windows.

Then open a terminal and do
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk

---

### Post by amjjawad on 2011-07-29
No, it's my fault for sure. My apology to everyone here.

I've been sleeping 3-4 hours daily for more than 2 weeks now. My family keeps saying I became a zombie and I keep ignoring that. 

I'll log off now.

Sorry again!

AJ

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> No, don't do the install or we'll be here all night. Just close the windows.


So now what? You know what? When I started using linux on laptop, I really liked how clean and fast it was. Even though I'd have these 'grey outs' when it locks up and you can't do anything, it was still nice. (other person once told me that is a linux thing to have to deal with) But so far I am not in love with it. Would like to, but this is like being an abused woman and still saying, "but I love him". I'm not that gullible or stupid! 

So no other options now? (maybe when I hit post, you'll have another reply.)

IF I reinstall/reformat/restore windows XP, will it or won't it cover up/erase/obliterate this freshly installed ubuntu that won't boot??? 
Asked another way: if I reformat with XP, is it going to take all of its partitions back I gave ubuntu? 

IF yes, then sounds like I should just do that. We've already spent so much time on things that aren't working. 
IF no, then ice cream is in my freezer. So I have no worries.

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> No, don't do the install or we'll be here all night. It isn't necessary at all. Just close the windows.

Then open a terminal and do
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk


This is the second time I've seen this happen...thought I was wrong...but the above sentence of yours ending in 'windows' came through WITHOUT the four lines below it. I then posted and looked at this again ..and the four lines are there! (hughes net ...you are NOT getting any of my icecream!)

Ok..working on sudo apt-get update..it is 'doing it now. (thought we tried this before..but we have tried So many things, I am not sure.

---

### Post by primal woman on 2011-07-29
Asked if I wanted to create a log, I did. 

Now, I have three options: (without all the wording it does give me)
disk /dev/sda   200G
        /dev/sdb  13 G   (this my slave drive??)
        /dev/sr1   732MB

I am to hit one and hit 'proceed'.

So which? 

Keep in mind if you say something like...now do what oldfred told you to do or 'do what that web site said to do..I have to go back and find it and uggg...I will if I have to. But I could get lost!

---

### Post by primal woman on 2011-07-29
Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 200 GB / 186 GiB - ATA WDC WD2000BB-22G
Disk /dev/sdb - 13 GB / 12 GiB - ATA QUANTUM FIREBALL
Disk /dev/sr1 - 732 MB / 698 MiB (RO) - LITE-ON CD-ROM LTN-4891S






[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.


hadn't tried to paste it...there it is...

---

### Post by YesWeCan on 2011-07-29
It will be the 200G
You are nearly there...patience...:)

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> It will be the 200G
You are nearly there...patience...:)

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 200 GB / 186 GiB - ATA WDC WD2000BB-22G
Disk /dev/sdb - 13 GB / 12 GiB - ATA QUANTUM FIREBALL
Disk /dev/sr1 - 732 MB / 698 MiB (RO) - LITE-ON CD-ROM LTN-4891S






[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

---

### Post by primal woman on 2011-07-29
whoops..didn't work...wait...trying again...

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> It will be the 200G
You are nearly there...patience...:)

Disk /dev/sda - 200 GB / 186 GiB - ATA WDC WD2000BB-22G

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selectionubuntu@ubuntu:~$ 





Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

---

### Post by YesWeCan on 2011-07-29
Select "Intel" and press enter
On the next screen select "Advanced" and press enter

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Select "Intel" and press enter
On the next screen select "Advanced" and press enter


Disk /dev/sda - 200 GB / 186 GiB - ATA WDC WD2000BB-22G

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selectionubuntu@ubuntu:~$ ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 




Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.


see the return section...it is adding ubuntu's but not giving me 'advanced' anywhere.

See your owl eyes....I wonder what mine look like!

---

### Post by primal woman on 2011-07-29
In fact it does not allow me to scroll up or down that list if I wanted. (and I am patiently waiting to hear that my DVD is working on it)

---

### Post by YesWeCan on 2011-07-29
Select the first item [Intel] and press enter.

---

### Post by YesWeCan on 2011-07-29
Oh. It looks like it went back to the command line. What did you type?
Start from the beginning: sudo testdisk

---

### Post by primal woman on 2011-07-29
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63

     Partition                  Start        End    Size in sectors
 2 * FAT32                    0   1  1   542 254 63    8723232 [RECOVERY]
 1 P HPFS - NTFS            543   0  1 14524  73 11  224609375
 3 P Linux                14524  74 15 14536 102 30     194560
 4 E extended             14536 134 61 24321  74  9  157192194
 5 L Linux Swap           14536 134 63 14840  81 25    4880384
   X extended             14840  81 26 15448  39 15    9764864
 6 L Linux                14840 113 58 15448  39 15    9762816
   X extended             15448  39 16 24321  74  9  142546944
 7 L Linux                15448  71 48 24321  74  9  142544896





[  Type  ]  [  Boot  ]  [Image Creation]  [Undelete]  [  Quit  ]
                              Boot sector recovery


It took a long time to let me do this OR this thing needs to be full sized in order to do it! stated too many lines or something! anyway..now what do I do?

---

### Post by YesWeCan on 2011-07-29
Select 1 P (the second line)
Then select "Boot" at the bottom
Then press enter

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Select 1 P (the second line)
Then select "Boot" at the bottom
Then press enter

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS            543   0  1 14524  73 11  224609375

Boot sector
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.




















[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]
                      Copy boot sector over backup sector

---

### Post by primal woman on 2011-07-29
Hoping you are still there. I keep hitting refresh and sometimes it waits 15 minutes before it gives me new posts!

---

### Post by YesWeCan on 2011-07-29
The backup boot sector is flagged as Bad. Whether it is really bad or is just different from the current boot sector is not clear.

Perhaps oldfred can comment?

If you do not want to wait, you have nothing to lose at this stage. So I would try using the backup anyhow. To do this, select the "Backup BS" at the bottom and press enter. It should ask you to confirm with a Y.

At best XP will now boot. At worst, nothing will boot. But nothing boots anyhow, right?

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> The backup boot sector is flagged as Bad. Whether it is really bad or is just different from the current boot sector is not clear.

Perhaps oldfred can comment?

If you do not want to wait, you have nothing to lose at this stage. So I would try using the backup anyhow. To do this, select the "Backup BS" at the bottom and press enter. It should ask you to confirm with a Y.

At best XP will now boot. At worst, nothing will boot. But nothing boots anyhow, right?


I can wait if I need to. As long as this thing can be patient and just sit here; I'm ok with that. 

I could perhaps also message oldfred? 

And no, nothing to lose I suppose, nothing was booting but my CD. 

And you mean to select the ORG. BS just to make sure..right?

---

### Post by YesWeCan on 2011-07-29
Oops, sorry I didn't look at you post in detail. There is no "Backup BS" but there is a "Rebuild BS" so try that.

I have sent a message to oldfred.

---

### Post by YesWeCan on 2011-07-29
Yes, you can just leave it sitting there.

---

### Post by primal woman on 2011-07-29
rebuild sounded like a good word, so I hit it!

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS            543   0  1 14524  73 11  224609375

filesystem size           224609375 224609361
sectors_per_cluster       8 8
mft_lcn                   16 16
mftmirr_lcn               5968666 5968666
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.







[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]
                           List directories and files

---

### Post by oldfred on 2011-07-29
Run the rebuild BS command, but I know NTFS partition boot sectors are different for different versions of windows and for partitions that are not bootable. I doubt that testdisk checks which version of windows it is and includes that. But if changed at least to a NTFS partition we can make sure the boot flag is on it and repairs from an XP disk should then work.

---

### Post by primal woman on 2011-07-29
> **oldfred said:**
> Run the rebuild BS command, 

Did that and results are: 

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS            543   0  1 14524  73 11  224609375

filesystem size           224609375 224609361
sectors_per_cluster       8 8
mft_lcn                   16 16
mftmirr_lcn               5968666 5968666
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.







[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]
                           List directories and files



but I know NTFS partition boot sectors are different for different versions of windows and for partitions that are not bootable. I doubt that testdisk checks which version of windows it is and includes that. But if changed at least to a NTFS partition we can make sure the boot flag is on it and repairs from an XP disk should then work

but sounds like I don't have a XP disk. All I have is the emachine xp media center edition restore disk and that is what I use to reformat/reload my entire OS. 

.
says this message is too short..whuzatagin...

---

### Post by YesWeCan on 2011-07-29
So you now need to select "Write" to write it to the disk.

---

### Post by primal woman on 2011-07-29
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS            543   0  1 14524  73 11  224609375

filesystem size           224609375
sectors_per_cluster       8
mft_lcn                   16
mftmirr_lcn               5968666
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]
                           List directories and files



Is this looking good???

---

### Post by YesWeCan on 2011-07-29
> **oldfred said:**
> Run the rebuild BS command, but I know NTFS partition boot sectors are different for different versions of windows and for partitions that are not bootable. I doubt that testdisk checks which version of windows it is and includes that. But if changed at least to a NTFS partition we can make sure the boot flag is on it and repairs from an XP disk should then work.
At the moment it is set to boot sda1, which in turn boots sda2. Do you think this now needs to be changed or should she try booting as is first?

---

### Post by YesWeCan on 2011-07-29
That looks good. It says "Extrapolated boot sector and current boot sector are identical." which means it has written it to the disk.
Next is either to reboot your PC or to change the boot flag first. Just waiting for oldfred's opinion.

There is a question about whether the boot flag should be set to partition sda1 (current) or partition sda2.

If it doesn't boot then the flag should be set to the other and reboot again.

---

### Post by primal woman on 2011-07-29
OK, I'll wait.

---

### Post by YesWeCan on 2011-07-29
You might as well reboot it while you are waiting. ;)
It will either boot into XP or it won't boot. It won't hurt. If it doesn't boot, you will need to reboot from live CD again.

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> You might as well reboot it while you are waiting. ;)
It will either boot into XP or it won't boot. It won't hurt. If it doesn't boot, you will need to reboot from live CD again.


OK, didn't work. I rebooted with neither of the CD's in drive and it will not boot. 

by the way..now on laptop ubuntu 10.04 firefox. Sure like this firefox better. Is it the 10.04 version that makes it different or an updated/outdated firefox that makes it different?

---

### Post by primal woman on 2011-07-29
Rebooting, but taking MUCH MUCH longer to go into live CD; in fact...does not look like it is going to go. 

It is up to try ubuntu and I clicked it, but it is just thinking and going nowhere. Took a long time just to get to this point.

---

### Post by YesWeCan on 2011-07-29
That's too bad. The final step before throwing in the towel is to change the boot flag to sda2. You need to use the sfdisk command for this. You may need to go back to Update Manger and add the "universe" source again. But try it first.

[COLOR="Navy"]sudo apt-get install sfdisk[/COLOR]

If is says sfdisk is not found, then turn on "universe" again and then do:
[COLOR="Navy"]sudo apt-get update
sudo apt-get install sfdisk[/color]

Once sfdisk is installed do:
[COLOR="Navy"]sudo sfdisk /dev/sda -A2[/COLOR]

Then post the output of
[COLOR="Navy"]sudo sfdisk -l[/COLOR] so I can check the flag is correctly set.

---

### Post by oldfred on 2011-07-29
I had to go back to the boot script output. It is sda1 that looks like the main XP install and it had the boot flag. Post the output suggested just to confirm boot flag is still there.

Then we can try rebooting.

---

### Post by YesWeCan on 2011-07-29
I'm afraid I am going to have to abandon you very soon. If the CD won't boot then probably best to switch it off for a while and try again later. Check the CD disk looks clean.

I think the odds of this working by changing the boot flag are low. If you are having lots of problems with the CD then you may just want to throw in the towel and reinstall everything using your recovery disc. If you do reinstall I imagine your Ubuntu partitions will be wiped out.

Different versions of Firefox are supported by different versions of Ubuntu. Firefox 4 (I think) in 11.04 takes some adjustment. My Windows 7 is using Firefox 5.

---

### Post by YesWeCan on 2011-07-29
That's a good idea, oldfred, to check where the flag is before doing anything else.

You can do this with this command (no need to install it)
[COLOR="Navy"]sudo fdisk -l[/COLOR]

---

### Post by primal woman on 2011-07-29
If is says sfdisk is not found, then turn on "universe" again and then do:
[COLOR=Navy]sudo apt-get update

It finally loaded and I'm on..and I'm doing the above and it is working on it...will post more when it's done. 

[/COLOR]

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> That's too bad. The final step before throwing in the towel is to change the boot flag to sda2. You need to use the sfdisk command for this. You may need to go back to Update Manger and add the "universe" source again. But try it first.

[COLOR=Navy]sudo apt-get install sfdisk[/COLOR]

If is says sfdisk is not found, then turn on "universe" again and then do:
[COLOR=Navy]sudo apt-get update
sudo apt-get install sfdisk[/COLOR]

Once sfdisk is installed do:
[COLOR=Navy]sudo sfdisk /dev/sda -A2[/COLOR]

Then post the output of
[COLOR=Navy]sudo sfdisk -l[/COLOR] so I can check the flag is correctly set.
  
Was I supposed to do the last two lines? 
Here is up to [COLOR=Navy]sudo sfdisk /dev/sda -A2[/COLOR]

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 5,149 kB in 2min 46s (30.9 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install sfdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sfdisk
ubuntu@ubuntu:~$ sudo sfdisk /dev/sda -A2
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Done

ubuntu@ubuntu:~$

---

### Post by primal woman on 2011-07-29
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sdb: 1665 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/240/63 (instead of 1665/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 7741440 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   1768    1769-  13373608+   c  W95 FAT32 (LBA)
        end: (c,h,s) expected (1023,239,63) found (744,239,63)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1        543   14524-  13982- 112304687+   7  HPFS/NTFS
/dev/sda2   *      0+    542     543-   4361616    b  W95 FAT32
/dev/sda3      14524+  14536-     13-     97280   83  Linux
/dev/sda4      14536+  24321-   9785-  78596097    5  Extended
/dev/sda5      14536+  14840-    304-   2440192   82  Linux swap / Solaris
/dev/sda6      14840+  15448-    608-   4881408   83  Linux
/dev/sda7      15448+  24321-   8874-  71272448   83  Linux
ubuntu@ubuntu:~$

---

### Post by YesWeCan on 2011-07-29
Yes, just port the output of: [COLOR="Navy"]sudo sfdisk -l[/COLOR]

---

### Post by YesWeCan on 2011-07-29
Good job. Ok well fingers crossed and reboot it. :)

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Yes, just port the output of: [COLOR=Navy]sudo sfdisk -l[/COLOR]

Didn't know what you mean by port the output and also did not nkow if that was an l or a 1 so did both. You already got the post for l and here is the result for a 1!

ubuntu@ubuntu:~$ sudo sfdisk -1
sfdisk (util-linux-ng 2.17.2)
Usage: sfdisk [options] device ...
device: something like /dev/hda or /dev/sda
useful options:
    -s [or --show-size]: list size of a partition
    -c [or --id]:        print or change partition Id
    -l [or --list]:      list partitions of each device
    -d [or --dump]:      idem, but in a format suitable for later input
    -i [or --increment]: number cylinders etc. from 1 instead of from 0
    -uS, -uB, -uC, -uM:  accept/report in units of sectors/blocks/cylinders/MB
    -T [or --list-types]:list the known partition types
    -D [or --DOS]:       for DOS-compatibility: waste a little space
    -R [or --re-read]:   make kernel reread partition table
    -N# :                change only the partition with number #
    -n :                 do not actually write to disk
    -O file :            save the sectors that will be overwritten to file
    -I file :            restore these sectors again
    -v [or --version]:   print version
    -? [or --help]:      print this message
dangerous options:
    -g [or --show-geometry]: print the kernel's idea of the geometry
    -G [or --show-pt-geometry]: print geometry guessed from the partition table
    -x [or --show-extended]: also list extended partitions on output
                             or expect descriptors for them on input
    -L  [or --Linux]:      do not complain about things irrelevant for Linux
    -q  [or --quiet]:      suppress warning messages
    You can override the detected geometry using:
    -C# [or --cylinders #]:set the number of cylinders to use
    -H# [or --heads #]:    set the number of heads to use
    -S# [or --sectors #]:  set the number of sectors to use
You can disable all consistency checking with:
    -f  [or --force]:      do what I say, even if it is stupid
ubuntu@ubuntu:~$

---

### Post by primal woman on 2011-07-29
Likely was not a 1!

---

### Post by oldfred on 2011-07-29
We often post commands so you can easily copy & paste into to terminal. Many times 1, I  & l get confused depending on typeface used. Also spaces may not look like spaces. So just copy & paste especially if unsure.

---

### Post by YesWeCan on 2011-07-29
I was in the middle of writing my post when you posted what I was asking for and I didn't know you had done it. ;)
Yes it is -l as in list.

---

### Post by primal woman on 2011-07-29
> **oldfred said:**
> We often post commands so you can easily copy & paste into to terminal. Many times 1, I  & l get confused depending on typeface used. Also spaces may not look like spaces. So just copy & paste especially if unsure.


Well, I rebooted as directed and nothing. This time though it did a nicer shut down instead of having to hard shut down. But again, nothing in the drives and no windows. 

But did we even change anything this last time? I don't know. 

Guess that is it huh? Last ditch effort is a restore/reformat so it seems.

---

### Post by YesWeCan on 2011-07-29
Well, I'm all out of suggestions. Sorry that didn't work.

---

### Post by primal woman on 2011-07-29
> **YesWeCan said:**
> Well, I'm all out of suggestions. Sorry that didn't work.


I really appreciate the time you guys took to assist me. It is amazing what you know and how easy you get around ubuntu. 

Well, I certainly am not going to restore at this moment, but when I do, I'll want to reinstall ubuntu (slap me silly). And amajjwad had said I don't need that fourth entry called boot. So first off...will hitting my first option...'install next to windows' instead of what I did; 'something else' give me the option to give ubuntu some space????????? And if so..then I'll go that route. But if not, I want to give it some space and will chose 'something else'. Then I'll have to partition using swap, home, and /. Those three. If that is correct. Great. But I'll sure want a web site tutorial for me to go through when I do it. Got one?

---

### Post by YesWeCan on 2011-07-29
I think oldfred can help you with some tutorials. I normally manually install but you don't need to. The Ubuntu installer should take care of everything for you so you don't need to make any decisions except for how much space to use.
Good luck with the reinstall. :)
See you later.

---

### Post by oldfred on 2011-07-29
When you boot your XP disk do you get this screen?

Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)


Some links for installs. Hermans are very detailed as he explains everything, but sometimes that extra info can be too much for a new user. I think his are still 10.10, but the process is the same and the screens have changed only slightly.  aysiu's are a bit less detailed, but she has one that is 11.04..

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Some info on partitioning:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by drs305 on 2011-07-29
Here is a great guide for installing Ubuntu, complete with graphics. There are several scenarios to choose from. 

[http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/~herman546/index.html")

---

### Post by primal woman on 2011-07-29
> **oldfred said:**
> When you boot your XP disk do you get this screen?

Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)


[]("http://www.psychocats.net/ubuntu/installseparatehome")


NO, I do not get that screen. I get hit r to start recovery options in 5 seconds, count down and then gives me option to hit F11 to start recovery. And if I do nothing, it does nothing. Blank screen. 

If I hit r then I get option to full system restore or restore with back up.

---

### Post by primal woman on 2011-07-29
I guess I now own a paperweight. I did a system restore and it finished and stated to hit restart to complete it. I did, and it did not boot. Seems whatever I did could be undone. I don't get it.

---

### Post by primal woman on 2011-07-29
when it rains it pours. Now my CD drive won't open! Just hicups when I try to. 

There is a very small hole in the front, is that some kind of manual way to open it? 


Anyway, as I posted, reformat did not work. Thought I'd go into BIOS again. Remember I said I went into BIOS and 'fourth boot' option was disabled and I put it to hard disk? Well, then I was told not to do that, so I changed it back. This was yesterday or maybe before. Well, now it was on network. So what gives? Why would that change? I changed it back to disabled again.

Here is only PART of what the bios says:
The first four items are called boot priority 
The next four items are called 1st boot, 2nd boot and so on. And of course they are labeled CD or whatever. I did not write all them down. But booting up with my cd or dvd has not been a problem anyway.

---

### Post by primal woman on 2011-07-29
CD rom drive opened on its own same time DVD rom drive opened after second try at reformat and it was ejecting restore disc. 

So what's new? Nothing, second try hitting F11 gave me the same options as hitting r for recovery! That was dumb. Either way...it did not restore. Took less than 10 minutes and it said it was done. Just asks to restart.

---

### Post by oldfred on 2011-07-29
It may not restore MBR. But from windows you need a windows XP disk to run repairs. I do not understand a vendor not providing a way to create a repair disk. I would suggest to contact them and complain.

You can put the windows work alike boot loader in the MBR from the Ubuntu liveCD.

Again you need the Universe repositories enabled to download lilo.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.
[URL="http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html"]
[/URL]

---

### Post by amjjawad on 2011-07-30
Hello Everyone,

I'm sorry if I'm interrupting something here but I see this is taking way too long than what it supposed to take. We all thought by fixing the MBR issue, it would be shorter and easier to carry on and solve the whole thing but "obviously", fixing the MBR issue is taking longer than any other possible solution to this issue.

Above all, I feel there is something wrong as the Restore CD is not helping and BIOS settings are changing almost every time the machine is rebooting.

Primal Woman is doing her very best and everyone here is doing their very best too, **no doubt about it**, period.

But ... in my humble opinion, I think it's time for another approach.

I will NOT suggest to DO THIS or THAT but instead, I'll explain what I would do if I were in such situation.

Primal Woman: YOU ARE FREE to ignore this post or follow it. I'm just sharing with all of you the steps that I would do to fix such issue, specially after all that time we all spent on this.

There you go ...

1) I will first check BIOS and see what's wrong with the booting options and why it's changing or not saving my selection.

2) Phoenix Award BIOS should look similar to this: 

[IMG]http://www.computerhope.com/help/bios5.gif[/IMG]


[IMG]http://www.cuug.ab.ca/branderr/mepis/PhoenAward1.jpg[/IMG]


[IMG]http://www.cuug.ab.ca/branderr/mepis/PhoenAward2.jpg[/IMG]


Regardless HOW DOES IT LOOK LIKE, there must be away to change values and if it's the same BIOS as in the above pictures, then "**Enter**" to select the item and "**+/-/Page Up/Page Down**" to change value. Otherwise, there must be away, period.

NO MATTER what the BIOS looks like, NO MATTER what machine is that, the correct settings much be as follows:

[COLOR=Red][B]First Boot Device: [COLOR=Blue]CD-ROM[/COLOR]
Second Boot Device: [COLOR=Blue]Hard Disk Drive (HDD)[/COLOR]
[/B][/COLOR]
In some other cases which is different from Primal Woman's Scenario, the boot sequence could be different but that depends whether the user is booting from a CD Drive OR External CD Drive OR USB Drive. However, the 2nd option must always be the internal HDD.

That's the default Boot Device Settings.


After changing anything in BIOS, I'll save the settings which is the most important step.

If I feel there is something wrong, I would "Restore" the BIOS settings to its default settings. Then, make sure the CDROM is the first device and the HDD is the second one.

Save and Reboot.


3- Boot my PC from Ubuntu LiveCD.

4- Start GParted and wipe the whole HDD ***[Remove ALL the partitions]*** In fact, I would create a new Partition Table, specially if my HDD is messed up.

It's done from **Device** Menu in GParted then **"Create Partition Table"**. 

Some actions in GParted require APPLY so it's better to do that after each operation.

5- While I'm still in GParted, I need to come up with my own scheme to create my own partitions.

[COLOR=Red]a) If I'm planning to Dual Boot Windows XP and Ubuntu, then my partitions scheme should meet my needs. [/COLOR]

[B]Say My HDD is 200GB
[/B]
[U]Example 1:
[/U]75GB for Windows XP
**75GB for Ubuntu*
50GB NTFS Shard Partition between Windows and Ubuntu

[U]Example 2:
[/U]100GB for Windows
**100GB for Ubuntu*

[U]Example 3:
[/U]50GB for Windows XP
[I]*50GB for Ubuntu
[/I]50GB NTFS Shard Partition between Windows and Ubuntu
50GB a Backup Partition OR Unallocated Space.


[SIZE=4][B]* Ubuntu Partition Scheme:
[/B][/SIZE]
The most recommended (but not a must) scheme for Ubuntu Partitions is:

Root Partition (/) - ext4
Home Partition (/home) - ext4
SWAP Partition (Linux-Swap) 

The easiest scheme for Ubuntu Partitions is:

Root Partition (/) - ext4
SWAP Partition (Linux-Swap) 


The size of each partition will depend on my needs. I may need 20GB or I may need 100GB. That's totally up to what I'll decide and that is totally depends on my needs and usage.

However, [**SWAP Partition**]("https://help.ubuntu.com/community/SwapFaq") in most cases should be:

Swap Partition = Your RAM [example: if RAM is 1GB then Swap is 1GB]

OR

Swap Partition = Double RAM [example if RAM is 512MB then Swap is 1GB]

Nowadays, RAMs became so cheap and available in higher capacity so if I have 1GB RAM or 2GB RAM, I'll set my SWAP to be 1GB or 2GB too.

[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?](https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?)


[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)



[COLOR=Red]b) If I'm planning to install Ubuntu as my ONLY Operating System on my machine, my Partitions Scheme will be different.
[/COLOR]
[B]Say My HDD is 200GB
 [/B]
[U]Example 1:
[/U]100GB for Ubuntu
100GB unallocated space for future use

[U]Example 2:
[/U]The whole space will be allocated to Ubuntu


6- If I'm planning to Dual-Boot Ubuntu with Windows XP, then long story short, I would follow the steps which I have explained in details and that will be the 2nd link in my signature.

Or, I'll go to google and search for that

Or, I'll follow the links which had been provided in this thread or other threads.

ALL what I know, Windows XP can be installed either by using Windows XP CD ... OR ... a Backup Image which is either on a bootable CD or on a file stored anywhere safe.

7- Once XP is installed up and running, I'll start Ubuntu installation.

8- [COLOR=Navy]NO MATTER what version/release/variant of Ubuntu I'm going to use, NO matter what partition Scheme I'll follow, there is ONE important step that MUST be done ... [/COLOR]

I'll install Ubuntu Boot Loader (GRUB2) in the MBR of my Hard Disk Drive, the same Hard Disk where Windows is installed.

Why? simply because I trust GRUB2 and I know how to fix anything might go wrong.


9- After installation, I'll make sure BOTH Systems are up and running.

10- If there is something wrong, I would stop, take a walk or eat something and will come back to check what is wrong?

11- After all this, if nothing will work the way I wanted and planned to, then that's totally different story. It could be software error or it could be hardware error. Again, that's different story.


[B]The End.
[/B]

That is what I would do if I were you.

Good luck!

AJ

---

### Post by YesWeCan on 2011-07-30
If you are unable to do the restore of the original XP system, you will probably still have your Ubuntu installation intact on the hard disk and you can still boot it and use it. Just requires reinstalling Grub to the MBR:

boot live CD
[COLOR=Indigo]sudo mount /dev/sda3 /mnt
sudo grub-install --root-partition=/mnt /dev/sda[/COLOR]

---

### Post by primal woman on 2011-07-30
I am impressed with the help and the time you are all offering. I am honored. I would also do the same for you if positions were swapped. Thank you so much. 

Amajjawad, thanks for that post you put quite an effort into. 

Not sure yet what I am going to do. That one option on the right in the BIOS there...load defaults or whatever it said in your post...sounds easy enough. Ha

Just a thought: would my Acer laptop restore discs (2 of them) have something my emachine desktop could use to 'repair' like oldfred has been wanting me to do? They are both xp media center editions. I know..nothing to lose, just try it. And perhaps I will. 

I'd do what oldfred's post says, but it is not detailed enough for a layman. Take for instance, I think he said 'go to synaptic'. Well, um; blank stare here..I have no idea where that is! The rest is also too cryptic for me to know what to do. 

I posted on craigslist for a recommended computer/tech guru to take it to (which I am reluctant, but may have no choice) and I got a response from one person that said the same as oldfred and you guys about the xp CD and recovery option. (and of course we found out I don't have that option), but his directions pasted below starting at fixmbr C: ......are those correct directions? 

Boot to a Windows XP or Vista install CD.


Press "R" or opt to use the Recovery Console when prompted.


Get to the dos prompt and enter these commands.


FIXMBR C: 
FIXBOOT C: 
COPY CDDrive:\I386\NTLDR C:\ 
COPY CDDrive:\I386|NTDETECT.COM C:\ 
BOOTCFG /rebuild.


Well, another day gone by without my desktop. I'll likely work on it, but also want/need to go out and pull fence posts and build fence to keep my sanity!

---

### Post by amjjawad on 2011-07-30
The honor and the pleasure is mine, Primal Woman!

I have an extra Hard Drive (40GB) which I don't use it right now. I wiped it and planning to install XP and Ubuntu 11.04 just to go through all of this by myself. It's been a long time (many months) since I have done a test so it's the best time and I have a good reason for that. I need to refresh my memory a little bit.

To make it even more detailed and clear, I'll post some screen shots so that you'll get the Full Picture of what I was talking about in my previous (last) post.

1- Boot from Ubuntu 11.04 LiveCD and Run GParted. You can find GParted in System Settings when you click on the shutdown icon. I still don't know WHY would System Settings be in the same list of Shutdown, restart, etc but ... oh well.

My HDD is 40GB so ignore the size, just follow the steps.

Don't even bother to format or remove the partitions manually. Just go to Device and hit Create Partition Table.

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8073[/IMG]




2- Time to create the partitions

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8074[/IMG]



3- Create the first partition. This partition must be NTFS and it's for XP.

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8075[/IMG]




4- On the unallocated space:

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8076[/IMG]



5- Now, time to create Ubuntu Partitions. Since it's just a test so I'm not going to create /home partition, I'll just create root and swap.

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8077[/IMG]




6- The left/remaining unallocated space is for Swap Partition

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8078[/IMG]




7- Swap Partition. I already explained how to set the size of that partition. I have 2GB RAM and it's recommended to create 2GB SWAP but ... again ... since it's a test, I set it as 1GB. IF YOU WANT TO go for my approach which I explained in my last post, please refer back to that post and read my explanation about swap.

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8079[/IMG]



8- At the end, GParted should look this this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8080[/IMG]


Nothing left except to click Apply.


After that, I ejected my LiveCD for Ubuntu, inserted my Windows XP CD and rebooted.

My PC is installing XP now so once done, I'll install Ubuntu. Will do exactly like you did, will install GRUB2 in sda1 instead of sda.

Will be right back!

---

### Post by oldfred on 2011-07-30
@primal woman

If you have access to any full XP install which most XP disks are, then you should get to the XP install/repair menu I posted before (119). If you then can get to the command line with R from that menu, you can run the XP repair commands.

---

### Post by amjjawad on 2011-07-30
Now, it's time for some other screenshots for Ubuntu installation.

1- "Something Else" is what I usually choose. Why? simply it's easier for me and Problem-Free as long as I know what I'm doing. Beside, I always use GParted and Create my Partition "BEFORE" I install anything.

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8081[/IMG]




2- Because I already used GParted and Created my Partitions previously, I just need now to do some simple steps. I first select sda2 which will be my ext4 root partition. As I explained earlier, in this TEST, I'm not going to use a separate partition for home (/home). 

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8082[/IMG]

I highlighted /dev/sda2 - ext4 then either to Double Click or Click on "Change".



3- Use as, Format and Mount Point is what I need to select:

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8086[/IMG]



[COLOR=Red][B]4- NOW, THIS IS THE MOST IMPORTANT STEP (sorry about CAPS).

In this Step, I have to tell the installer where to install GRUB2 which is the boot loader of Ubuntu.

 >>> The Correct Step is to install GRUB2 in the MBR of my Hard Disk Drive and that will be "sda".

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8084[/IMG]
[/B][/COLOR]


Unfortunately in your case, Primal Woman, you have done [[COLOR=Red]**this**[/COLOR]]("http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8085") which is totally wrong.


5- Nothing more important than the above steps. The rest is piece of cake.


Done :)

---

### Post by amjjawad on 2011-07-30
I'm done with installing both Systems (XP and Ubuntu 11.04). Needless to say I ended up with exactly the same situation.

1- Directly after reboot (after Ubuntu installation is done), I got GRUB2 menu with all the entries, even Windows XP.

2- Choosing Windows XP do absolutely nothing and will redirect me to GRUB2 menu.

3- I was able to boot successfully to Ubuntu.

4- I then put my LiveCD and rebooted my machine.

5- Ran the Boot Script and got the following output/result:



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 47955928 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    39,092,223    39,090,176   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    75,925,503    36,833,280  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1007 MB, 1007157248 bytes
64 heads, 32 sectors/track, 960 cylinders, total 1967104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             45     1,965,055     1,965,011   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C050D45550D453AE                       ntfs       
/dev/sda2        5c61cd7a-07f5-4553-9648-9f8015be999f   ext4       
/dev/sda3        f1891946-988d-431b-9b54-1d8030b6dedd   swap       
/dev/sdf1        ACDD-FF3F                              vfat       PHONE CARD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/PHONE CARD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c61cd7a-07f5-4553-9648-9f8015be999f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c61cd7a-07f5-4553-9648-9f8015be999f ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C050D45550D453AE
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
UUID=5c61cd7a-07f5-4553-9648-9f8015be999f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.867195129 = 24.553463808   boot/grub/core.img                             1
  21.459907532 = 23.042400256   boot/grub/grub.cfg                             1
  21.644741058 = 23.240863744   boot/initrd.img-2.6.38-8-generic               2
  22.865463257 = 24.551604224   boot/vmlinuz-2.6.38-8-generic                  1
  21.644741058 = 23.240863744   initrd.img                                     2
  22.865463257 = 24.551604224   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error



```


[COLOR=Red][B]>>> sdf is 1GB USB Drive so just ignore it.


[/B][COLOR=Black]6- Now, I have to fix the issue by booting from Windows XP CD, choose repair, run the two commands, restart and boot from Ubuntu LiveCD, re-install GRUB2 to sda instead of sda1 and that should be all.

Will get back to you when I'll finish that.

I don't have internet access to that PC so I have to come and go to the other room and use my laptop. Good exercises :D

[/COLOR][/COLOR]

---

### Post by oldfred on 2011-07-30
@amjjawad
If you want to test, you can try the testdisk recovery of the PBR. Then reinstall grub2 to PBR and run the windows fixBoot repair. I would expect in your tests that both would work equally well. FixMBR will just rewrite windows boot loader to MBR which it already shows.

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> @amjjawad
If you want to test, you can try the testdisk recovery of the PBR. Then reinstall grub2 to PBR and run the windows fixBoot repair. I would expect in your tests that both would work equally well. FixMBR will just rewrite windows boot loader to MBR which it already shows.

Hello oldfred,

Thank God I saw your post before fixing the issue through the other way.

It's very good idea so I'm going to try that and will report back.

If this will fail, then shall I just do it the other way? fixboot then fixmbr and then re-install GRUB2?


Edit:
I'm done with testdisk but what I'm so confused about is why do I have to do this:

> **oldfred said:**
> Then  reinstall grub2 to PBR and run the windows fixBoot repair.

The whole problem started when GRUB2 was installed to PBR so why to re-install it again? O_o

---

### Post by oldfred on 2011-07-30
@amjjawad
It is just a test to show that testdisk can recover a PBR from the backup when the backup is a correct windows PBR using a Linux liveCD or can repair PBR from a windows repairCD using fixBoot. Both methods should work. meierfra posted that testdisk is 'better' but I think it may be that it just uses Linux and avoids trying to explain that you can not use Vista/7 to recover a XP PBR and vice-versa as PBRs have a link to the boot loaders ntldr for XP and bootmgr for Vista/7.

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> @amjjawad
It is just a test to show that testdisk can recover a PBR from the backup when the backup is a correct windows PBR using a Linux liveCD or can repair PBR from a windows repairCD using fixBoot. Both methods should work. meierfra posted that testdisk is 'better' but I think it may be that it just uses Linux and avoids trying to explain that you can not use Vista/7 to recover a XP PBR and vice-versa as PBRs have a link to the boot loaders ntldr for XP and bootmgr for Vista/7.

Ok, so let's make it as simple as possible and please correct me if I'm wrong :)

In such case scenario, fixing the MBR is not required, hence there is no need to use fixmbr and as long as I'm using testdisk to fix the PBR, there is also no need to use Windows XP CD and that will lead to one simple fact which is if someone doesn't have XP CD and have similar issue, he/she can simply use testdisk either from his/her working Ubuntu or LiveCD to just fix PBR and get both systems up and running.

Am I right so far?


Now, I'm done with testdisk. What exactly shall I do? re-install GRUB2 to sda1? run sudo update-grub? or install GRUB2 to MBR?

I'm on the LiveCD of Ubuntu right now on my PC and typing this on my laptop.

---

### Post by amjjawad on 2011-07-30
Ok, this is the result of Boot Script after running testdisk:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    39,092,223    39,090,176   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    75,925,503    36,833,280  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C050D45550D453AE                       ntfs       
/dev/sda2        5c61cd7a-07f5-4553-9648-9f8015be999f   ext4       
/dev/sda3        f1891946-988d-431b-9b54-1d8030b6dedd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c61cd7a-07f5-4553-9648-9f8015be999f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c61cd7a-07f5-4553-9648-9f8015be999f ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 5c61cd7a-07f5-4553-9648-9f8015be999f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C050D45550D453AE
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
UUID=5c61cd7a-07f5-4553-9648-9f8015be999f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.867195129 = 24.553463808   boot/grub/core.img                             1
  21.459907532 = 23.042400256   boot/grub/grub.cfg                             1
  21.644741058 = 23.240863744   boot/initrd.img-2.6.38-8-generic               2
  22.865463257 = 24.551604224   boot/vmlinuz-2.6.38-8-generic                  1
  21.644741058 = 23.240863744   initrd.img                                     2
  22.865463257 = 24.551604224   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```To compare it with the previous one in **[post #132]("http://ubuntuforums.org/showpost.php?p=11101996&postcount=132")**:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    [COLOR=Red]Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 47955928 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

```


Obviously, GRUB2 is gone and need to be re-installed.

---

### Post by drs305 on 2011-07-30
> **amjjawad said:**
> Now, I'm done with testdisk. What exactly shall I do? re-install GRUB2 to sda1? run sudo update-grub? or install GRUB2 to MBR?

I'm on the LiveCD of Ubuntu right now on my PC and typing this on my laptop.

From your RESULTS.txt:
1. You do not want to install Grub to sda1. That would put it back on the Windows PBR.

2. Running update-grub from the LiveCD will fail, as it would try to change CD files. You would have to chroot into your real partition before update-grub would act on your real OS files.

3. Mounting /dev/sda2 to /mnt and running 

```

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

will install Grub2 and point it to your Ubuntu OS. If Windows is working, it will be accessible via the Grub menu once you run "sudo update-grub" after booting.

---

### Post by amjjawad on 2011-07-30
Ok, I restarted my PC and I'm no longer booting from the LiveCD.

Windows XP was booting then was doing something so quickly, many lines, couldn't read it.

Then I rebooted and I got a message:

> [B]Windows - Registry Recovery
[/B]
One of the files containing the system's Registry data had to be recovered by use of a log or alternate copy. The recovery was successful


OK button is the only thing to do on that pop up window/msg.


Then, got another message says:

> **Error**

Installation Failed



OK pressed on the first then OK pressed on the 2nd (error message).

I think I'm in the recovery mode or safe mode because there is no background (the default one for XP) and the theme is Windows Classic instead of XP one (blue one - the default). I don't understand? I'll restart and see what will happen.

I did not install or did anything right after XP installation. I just made sure it's working then I installed Ubuntu as already explained earlier.


Well, I just restarted and it's the same. Something is missing!
Looks like it's not the same copy of XP which I installed.

When I go to Display Properties and try to choose another theme like Windows XP, nothing happened. When I choose Windows Classic, I got an error:

> The Theme could not load. Unspecified Error.

File: C:\Windows\resources\Themes\Windows Classic.theme


Oh well. What is going on?!

---

### Post by drs305 on 2011-07-30
I can't speak to Windows problems, but don't install Grub until you have Windows booting normally from the Windows bootloader .....

---

### Post by amjjawad on 2011-07-30
> **drs305 said:**
> I can't speak to Windows problems, but don't install Grub until you have Windows booting normally from the Windows bootloader .....

Hello drs305,

No, I will NOT do it for sure. I'm shocked and surprised. Never happened with me before.

Guess what?

I did:
My Computer - Right Click
Properties
Advanced
Performance > Settings

and ... there is NOTHING in the list O_o
It's totally BLANK.

LOL, I don't know what to say?!

Edit: ain't this the Safe Mode for XP? why I'm on the Safe Mode anyway?

---

### Post by oldfred on 2011-07-30
@amjjawad
Is this after the testdisk recovery of the PBR or a fixBoot repair?

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> @amjjawad
Is this after the testdisk recovery of the PBR or a fixBoot repair?

Dear friend,

This is right after testdisk. 

I followed each and every word here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But I did not re-install GRUB2 nor booted from Windows XP CD.

I just did the 7 steps explained and that is all.

Any idea what's that?

I just did what we agreed about. I didn't want to use fixboot to solve this issue, wanted to see what could testdisk can do and I guess I saw that :)

---

### Post by primal woman on 2011-07-30
> **oldfred said:**
> @primal woman

If you have access to any full XP install which most XP disks are, then you should get to the XP install/repair menu I posted before (119). If you then can get to the command line with R from that menu, you can run the XP repair commands.


As I said before, no, I don't have those options nor did/does my screen look like that link in post #119. 

I tried again as you do know more than I and here is what I get:
My typical F2 or F10 options which are BIOS or Boot menu respectively. 
Then comes F10 for configuration (think I remember that word right)
Then comes hit R for recovery options (upper case R which of course is not possible I suppose, so lower case r is what I can hit). 
If I do nothing in five seconds, then it gives me F11 for recovery. 
Hitting r as above gives me another option: R for 'you will boot into the recovery partition or on CD if no recovery partition is found.'
OR hit Q to boot the OS on hard disk. 

You wanted me to hit r, so I have done that twice yesterday and both times it went to only TWO options; one was totally destroy and reinstall or reinstall with backup made onto C drive. 

So, did I do something wrong in trying to find the picture in link 119?


On to the further posts: Looks like amjjwad has the same problem now?? 
"Something else" must definitely mean 'something else'. Sorry to hear from what it looks to me that you are now in the same boat. And all in the name of trying to help me. Want to go build some fence with me? Sigh

---

### Post by amjjawad on 2011-07-30
> **primal woman said:**
> On to the further posts: Looks like amjjwad has the same problem now?? 
"Something else" must definitely mean 'something else'. Sorry to hear from what it looks to me that you are now in the same boat. And all in the name of trying to help me. Want to go build some fence with me? Sigh

Don't worry about me, I put myself in that boat purposely because:

1- I want to do the same steps that you will do
2- Feel how hard and bad it's
3- Learn from it

Don't worry, it's just a test on an old HDD which I don't need anyway and it's true that I spent hours on that without eating (I forget to eat while I'm working like that) but I'll never regret it nor feel sorry about it, it's called new experience and it's called learning new stuff so I'm more than glad to do it ;)

I'm doing my best to help you and same goes to my friends here.

Don't worry, I'm sure we'll achieve something.

Remember, that's all is one approach which is fixing the issue rather than format the whole thing and install from scratch.

---

### Post by primal woman on 2011-07-30
> **amjjawad said:**
> Don't worry about me, I put myself in that boat purposely because:

1- I want to do the same steps that you will do
2- Feel how hard and bad it's
3- Learn from it

.


1. same steps may not be same steps anymore as I am not sure the state of my computer anymore after trying to reformat. 
2. I could have simply just told you! chuckle
3. OK for you, but I don't learn this stuff easy enough. After I do something (install div x or something simple, I have to ask my daughter months later how to do it if I have to do it again! Ha


Is it possible that ubuntu 11.04 that we download and install onto our CD could be faulty? I downloaded mine on July 25, 2011.

---

### Post by amjjawad on 2011-07-30
> **primal woman said:**
> 1. same steps may not be same steps anymore as I am not sure the state of my computer anymore after trying to reformat. 
2. I could have simply just told you! chuckle
3. OK for you, but I don't learn this stuff easy enough. After I do something (install div x or something simple, I have to ask my daughter months later how to do it if I have to do it again! Ha


Just don't worry about it, this is my way to learn and help other people.
I have done many many Dual-Boot Installation, I even did Multi-Boot (9 OS's) but never faced the same issue that we both have right now.

This thread will definitely be a great reference for me and others, no doubt about it.

If we can't fix this issue the way we already started then this mean:
1- Either there is something wrong in your machine
2- Or there is something wrong in what we're doing

Either ways, we need to find out what is going on.

> Is it possible that ubuntu 11.04 that we download and install onto our CD could be faulty? I downloaded mine on July 25, 2011.Faulty could mean Bad Burn or damaged download. Each, has its approach to check.
Right after downloading Ubuntu, you need to check MD5SUM.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then you need to compare the result with Ubuntu Hashes:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

After that, when you burn it to a CD, make sure to choose lower burning speed. I usually choose 8x or 16x.

Some, for faster response and to save time, prefer to create LiveUSB. How? it's already explained in Step2 here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)


It's your call ... I already told you that before 2 or 3 days :)
You can fix it the way we are already doing right now ... or ... start all over again IF and ONLY IF you are 1000% sure that your XP CDs you have are actually able to install XP by restoring the image on that CD.
If that CD is NOT capable of doing so, then you can't install XP if you'll wipe your Hard Disk Drive.

I explained everything you need to know. My friends here did the same. It's your call now to choose :)

Edit:
I already told you what's wrong and everyone here told you the same. Installing GRUB2 to sda1 instead of sda was the problem. The CD that you have is NOT faulty :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8085[/IMG]

---

### Post by YesWeCan on 2011-07-30
Looks like lots of useful research going on here. I gather testdisk doesn't satisfactorily fix the PBR code.


@primal woman: I don't know whether it is too late but I imagine most any XP installation CD could be used to fix the boot sector of your existing installation. So if you have any friends who have an XP disk lying around that you could borrow.

---

### Post by oldfred on 2011-07-30
I know testdisk does work as we literally had 100's of users install grub to the PBR with 10.04 due to poor grub install instructions and many used testdisk sucessfully with all versions of windows.

I have to agree with YesWeCan on finding a friend with a full XP disk as the best choice for trying to repair it. I have seen some XP install disks suggested on Internet but would not want to use them as who knows how valid they may be. Perhaps your vendor has a download for a repair CD?

---

### Post by primal woman on 2011-07-30
> **amjjawad said:**
> Just don't worry about it, this is my way to learn and help other people.
I have done many many Dual-Boot Installation, I even did Multi-Boot (9 OS's) but never faced the same issue that we both have right now.

This thread will definitely be a great reference for me and others, no doubt about it.

If we can't fix this issue the way we already started then this mean:
1- Either there is something wrong in your machine
2- Or there is something wrong in what we're doing



So I take it from the above number 1 and 2; that you fixed your issue? 

And above that: 9 OS's. Quite a few. I only would want one, BUT windows is slower than ubuntu. But ubuntu has grey outs where I can't do anything and it does not allow me to use my external camera to skype. (at least on laptop with 10.04). Never had a chance to become familiar and use 11.04 installed on desktop of course. 

I'll try my acer xp disc. (I mentioned I had two restore discs for laptop, so don't have to borrow a friends hopefully.)

---

### Post by amjjawad on 2011-07-30
No, I couldn't restore Windows to its original so I re-installed it and I'm installing Ubuntu now.

If 11.04 is hard for you then simply use 10.04 :) 
I don't like 11.04 but I just installed it as I said to do this test to help you with your issue.

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> I know testdisk does work as we literally had 100's of users install grub to the PBR with 10.04 due to poor grub install instructions and many used testdisk sucessfully with all versions of windows.

It did not help in my case but in order to make sure it does or it doesn't, I formatted and re-installed XP. I'm now re-installing Ubuntu and will do the same (install GRUB2 to sda1).

The question is ... what if I use testdisk and get the same issue?

Edit:
Question 2: in Screen 6, are you sure it's "BackupBS" and not something else?

---

### Post by drs305 on 2011-07-30
> **amjjawad said:**
> It did not help in my case but in order to make sure it does or it doesn't, I formatted and re-installed XP. I'm now re-installing Ubuntu and will do the same (**install GRUB2 to sda1**).

The question is ... what if I use testdisk and get the same issue?

Edit:
Question 2: in Screen 6, are you sure it's "BackupBS" and not something else?

Just to make sure - **sda1** will not be your Ubuntu partition if you install Windows first and you should not be installing Grub to it.  :P

---

### Post by YesWeCan on 2011-07-30
> **oldfred said:**
> I know testdisk does work as we literally had 100's of users install grub to the PBR with 10.04 due to poor grub install instructions and many used testdisk sucessfully with all versions of windows.
I just experimented with my VBox XP Pro & 11.04 same disk installation.
1) I corrupted the XP PBR, sda1, by installing Grub to it.
2) I then ran testdisk and used it to restore the backup BS. This allowed XP to boot normally.
3) I corrupted sda1 PBR again.
4) I asked testdisk to "Rebuild BS". This time it came up with an extrapolated BS but it also stated "Extrapolated boot sector and current boot sector are identical." and did not give me a "Write" option. Clearly they are not the same, unless testdisk rebuild ignores the PBR boot code.

Hmm.

---

### Post by amjjawad on 2011-07-30
> **drs305 said:**
> Just to make sure - **sda1** will not be your Ubuntu partition if you install Windows first and you should not be installing Grub to it.  :P

I know, I know :D
As I said before, it's just a **test** :)

I'm trying to put myself in the same situation that the OP has. Then, try to fix it as suggested by oldfred with testdisk which did not help in my first try so this is the second one.

:)

---

### Post by oldfred on 2011-07-30
@drs305 amjjawad is testing how to repair windows partition boot sector. meierfra. had posted the testdisk method which we used a lot with 10.04. He also said it worked when fixboot did not, but there has to be a valid backup for it to find. Windows XP has its fixBoot command and Vista/7 use BootRec.exe /FixBoot.
@   	amjjawad
That is correct.

Could you copy the PBR. I had saved these instructions. Copy after windows install. After resizing windows. After installing grub. After testdisk. and after a fixboot but I would like to know if windows works after each change. I know windows wants to run chkdsk after a resize as it has to upate settings in the PBR and maybe in registry. If too much that is ok. Just a suggestion.

Check with fdisk -lu at what sector the first partition starts at.
Usually this is 63, but newer systems are now 2048
sudo fdisk -lu
The result of that command will show that the first partition almost always begins in sector 63, except in the case of Vista and Windows 7, which normally don't begin until sector 2048.
Save the embeding area when you recovered GRUB 2 to sda.1 with e.g.
dd if=/dev/sda of=sda.1 count=63
Then boot Windows and then some LiveCD or your Ubuntu with a rescue disk
or something like that.
And do it again but this time use of=sda.2
To see the difference you could then e.g. use
diff -u <(hd sda.1) <(hd sda.2)

Details on how NTFS works:
[http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx)
FAT
[http://support.microsoft.com/kb/140418](http://support.microsoft.com/kb/140418)
[http://mirror.href.com/thestarman/asm/mbr/MSWIN41.htm](http://mirror.href.com/thestarman/asm/mbr/MSWIN41.htm)
Boot sector - Bootable partition that stores information about the layout of the volume and the file system structures, as well as the boot code that loads Ntdlr (XP).
[http://mirror.href.com/thestarman/asm/mbr/NTFSBR.htm](http://mirror.href.com/thestarman/asm/mbr/NTFSBR.htm)

---

### Post by drs305 on 2011-07-30
> **amjjawad said:**
> I know, I know :D
As I said before, it's just a **test** :)

I'm trying to put myself in the same situation that the OP has. Then, try to fix it as suggested by oldfred with testdisk which did not help in my first try so this is the second one.

:)

OK. I'll just take a relaxing evening and let all of you bask in your carnage...

---

### Post by YesWeCan on 2011-07-30
This is the correct XP PBR:

```
@natty:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 74 00  |.X.MSWIN4.1..@t.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 5b 63 02 1b 13 00 00  00 00 00 00 02 00 00 00  |.[c.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 16 61 14 4e  4f 20 4e 41 4d 45 20 20  |..)..a.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 4e 54  |..............NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|

```

This is the corrupted PBR after Grub has been installed to it:

```
@natty:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
00000000  eb 63 90 4d 53 57 49 4e  34 2e 31 00 02 40 74 00  |.c.MSWIN4.1..@t.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 5b 63 02 1b 13 00 00  00 00 00 00 02 00 00 00  |.[c.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 16 61 14 4e  4f 20 4e 41 4d 45 20 20  |..)..a.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 80 38 56 a7 02  |  FAT32   ..8V..|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  69 73 73 69 6e 67 ff 0d  |...<.u..issing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|

```

They are obviously different in the boot code areas. I wonder whether XP PBR code is transferable to another XP installation? Probably not as there will be fixed sector addresses involved, no doubt.

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> meierfra. had posted the testdisk method which we used a lot with 10.04. He also said it worked when fixboot did not, but **there has to be a valid backup for it to find**. Windows XP has its fixBoot command and Vista/7 use BootRec.exe /FixBoot.

What does this mean? a valid backup to find? 
Don't tell me it means that there must be a restore partition or something? because definitely I don't have that ... I started my installation on a wiped clean HDD with nothing on it.

If that means BackupBS will fix PBR and create a backup to it, then that's different story. If that's so then why it damaged my Windows Installation and gave me Safe Mode XP?



> Could you copy the PBR. I had saved these instructions. Copy after windows install. After resizing windows. After installing grub. After testdisk. and after a fixboot but I would like to know if windows works after each change. I know windows wants to run chkdsk after a resize as it has to upate settings in the PBR and maybe in registry. If too much that is ok. Just a suggestion.

It's not that it's too much but it's too late now :(
I am writing this from the Live Session of Ubuntu 11.04 and the installation is done and I'm about to reboot.

After rebooting, if Ubuntu will work and XP should not work, I'll install testdisk while logging in to Ubuntu and will try to repeat the same as before but ... I need you to confirm whether it's BackupBS or something else?

---

### Post by amjjawad on 2011-07-30
> **drs305 said:**
> OK. I'll just take a relaxing evening and let all of you bask in **your carnage**...

What we're doing reminds me of 300 movie :D

Enjoy and I do need that too after not sure how many hours sitting on two machines trying to do something that could be done with one word "fixboot" :)

---

### Post by YesWeCan on 2011-07-30
> **drs305 said:**
> OK. I'll just take a relaxing evening and let all of you bask in your carnage...
:P Funny. Yes there is a lot of ugly debris from where we vultures have picked over the carcass.

---

### Post by primal woman on 2011-07-30
> **YesWeCan said:**
> :P Funny. Yes there is a lot of ugly debris from where we vultures have picked over the carcass.


Hey, that's my carcass you're talking about! chuckle

I'm loading or at least I think I'm loading my acer laptop xp media center onto emachine desktop. Do you guys want details?

---

### Post by oldfred on 2011-07-30
In this version of the carnage with seem to have put amjjawad out front.

Window NTFS partitions create a backup of the boot sector automatically. Part of the advantage of NTFS over FAT for windows users.

---

### Post by YesWeCan on 2011-07-30
> **amjjawad said:**
> I need you to confirm whether it's BackupBS or something else?
I think oldfred is referring to the backup copy of the XP boot sector that is in the XP partition. Testdisk will let you restore this backup, or backup the current boot sector. Unfortunately, primal woman's XP partition did not contain a valid backup. And the promisingly named "Rebuild BS" facility did not work.

---

### Post by YesWeCan on 2011-07-30
> **oldfred said:**
> Window NTFS partitions create a backup of the boot sector automatically. Part of the advantage of NTFS over FAT for windows users.
My XP partition contains a backup.

```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /grub.bin.bak looks at 
                       sector 40082174 of the same hard drive for core.img. 
                       core.img is at this location and looks for b2can on 
                       this drive.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

```

---

### Post by YesWeCan on 2011-07-30
> **primal woman said:**
> Hey, that's my carcass you're talking about! chuckle
8-[
> I'm loading or at least I think I'm loading my acer laptop xp media center onto emachine desktop. Do you guys want details?
Bring it on!

---

### Post by primal woman on 2011-07-30
> **YesWeCan said:**
> 8-[

Bring it on!

It didn't work. Ha

BUT it sure tried:
disc 1 was loading 'please wait'.
took about an hour. 
Then asked to load disc 2. 
then when done it said, loadint15 driver error at x:/int15.sys
(and I said: I had my seat belt on!)
"please load disc 1. 
Copying files on a screen I've never seen before. shades of green boxes 'working'. 
took several minutes. 
then kept restarting over and over. but never gets passed logo windows xp. 
(At least I got the logo....ya hoo. sheepish grin)
then brought up the page to start in safe mode or normal (sure you've all seen that kind of page)
tried normal. 
Kept trying to boot. 
Then asked safe mode again or other options. 
This time I picked safe mode. 
The system is not fully installed, please run set up again. 
bunch of 'drivers' scrolling up screen.
Black screen with safe mode at four corners and serial or other numbers and xp at top. 
Then it rebooted and kept trying. 
Prompt again for which mode. 
I chose safe with command. (figured I'd get told what to do...ha ha)
same bunch of 'drivers' scrolling up screen. and eventually tries to reboot again and again. 
system not fully installed. 

That's about all that happened. I tell you it is better than going downtown and watching haircuts. Yep.

---

### Post by primal woman on 2011-07-30
How can I remove linux.....???

I found the answer on this web site:

first, pray to satan, then get naked and cry like a girl, then get  someoneelse to fix the problem... but get dressed before asking for  help.


[http://www.pcuser.com.au/pcuser/hs2.nsf/lookup+1/FBC8A94788467700CA256DBF00118AE7](http://www.pcuser.com.au/pcuser/hs2.nsf/lookup+1/FBC8A94788467700CA256DBF00118AE7)

Ha ha

---

### Post by geogur on 2011-07-30
that is by far the best response i have seen to a problem , dude deserves a tshirt for that        i am using linux on a usb that way all i need is a host pc i use there internet and log on in unbuntu leaving the host pc un touched i like that set up better than a dual boot . you now have a pocket sized linux system :)

---

### Post by Hakunka-Matata on 2011-07-30
@YesWeCan;  When I run ```
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
``` in a terminal I get the output, but not formatted quite so cleanly as this QUOTE displays.  How does one produce this format?  Thanks

> **YesWeCan said:**
> This is the correct XP PBR:

```
@natty:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 74 00  |.X.MSWIN4.1..@t.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 5b 63 02 1b 13 00 00  00 00 00 00 02 00 00 00  |.[c.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 16 61 14 4e  4f 20 4e 41 4d 45 20 20  |..)..a.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 4e 54  |..............NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|

```This is the corrupted PBR after Grub has been installed to it:

```
@natty:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
00000000  eb 63 90 4d 53 57 49 4e  34 2e 31 00 02 40 74 00  |.c.MSWIN4.1..@t.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 5b 63 02 1b 13 00 00  00 00 00 00 02 00 00 00  |.[c.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 16 61 14 4e  4f 20 4e 41 4d 45 20 20  |..)..a.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 80 38 56 a7 02  |  FAT32   ..8V..|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  69 73 73 69 6e 67 ff 0d  |...<.u..issing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|

```They are obviously different in the boot code areas. I wonder whether XP PBR code is transferable to another XP installation? Probably not as there will be fixed sector addresses involved, no doubt.

---

### Post by Hakunka-Matata on 2011-07-30
Thanks, I got it.  Copied and pasted into text editor, then massaged a bit.  
Great thread

---

### Post by primal woman on 2011-07-30
Great thread? chuckle. Maybe....my computer is still sick! 

I am SO thankful I did not lose anything. Luckily I don't store precious information on my computers. Happy sigh here. 

How about this idea? 
A local person said he would wipe my drive completely back to 0's so I can reinstall. He has the cd's to completely wipe drives clean like refurbished machines are guaranteed to be wiped free. Same cd's. 

Will that work to fix that boot problem AND will my restore CD/DVD be able to pick up from total emptyness? 

Keep in mind that I've tried to restore system twice and it still does not boot and I no longer even know if I have xp or ubuntu on there.

---

### Post by amjjawad on 2011-07-30
> **oldfred said:**
> Window NTFS partitions create a backup of the boot sector automatically. Part of the advantage of NTFS over FAT for windows users.

Why that backup doesn't show on the result of the Boot Script?
Or it shouldn't be shown anyway?

---

### Post by amjjawad on 2011-07-30
> **primal woman said:**
> How about this idea? 
A local person said he would wipe my drive completely back to 0's so I can reinstall. He has the cd's to completely wipe drives clean like refurbished machines are guaranteed to be wiped free. Same cd's. 

Will that work to fix that boot problem AND will my restore CD/DVD be able to pick up from total emptyness? 

Keep in mind that I've tried to restore system twice and it still does not boot and I no longer even know if I have xp or ubuntu on there.

primal woman, I already have explained many times HOWTO do that but for some reason you keep ignoring it.

I don't know what's the point of keep trying the same helpless procedure? sorry, not being rude at all but I just don't understand?

Myself and others have offered ALL what we have but you keep saying the same?!

Perhaps I need to sleep?

---

### Post by amjjawad on 2011-07-30
@oldfred:

I'm now on testdisk and I'll try to do this for the last time before going to bed ... it's 6:00am here :(

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  2432 254 63   39086082
 2 P Linux                 2433  96 32  4726  36 46   36833280
 3 P Linux Swap            4726  36 47  4866  62 60    2250752

[  Type  ]  [  Boot  ]  [Image Creation]  [Undelete]  [  Quit  ]
                              Boot sector recovery


```After choosing Boot, this is what I got:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  2432 254 63   39086082

Boot sector
Status: OK

Backup boot sector
Status: OK

[B][COLOR=Red]Sectors are not identical.

A valid NTFS Boot sector must be present in order to access[/COLOR] [COLOR=Red]
any data; even if the partition is not bootable.[/COLOR][/B]

[  Quit  ]  [  List  ]  [Org. BS ]  [Backup BS]  [Rebuild BS]  [  Dump  ]
                            Return to Advanced menu

```MY BAD :(
I have got the same message before but I ignored it and chose BackupBS which apparently why things got messed up in my test.


So, what shall I do now?


[B]Edit:
[/B]
I chose to Rebuild BS so I got:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  2432 254 63   39086082

filesystem size           39086082
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2442880
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```
[B]Edit 2:
[/B]Restarting my PC, got GRUB2 and was able to login to Ubuntu normally.
I'm again on testdisk now and I repeated the same steps and got the same message:

**[COLOR=Red]Sectors are not identical.[/COLOR]**

That is it? I guess in my test, there is no way that testdisk could work and fix that, right?

[U][B][COLOR=Blue]Edit 3:
[/COLOR][/B][/U]oldfred, just to make sure we are in the same page, I want you to know that I did NOT do "FixBoot" at all. I ran "testdisk" immediately after installing it while I'm logging into Ubuntu.

By far, I see testdisk is NOT helping to fix the issue, unless I'm missing something?!

I will not do anything, I'll wait for your reply ... it's getting too late now ... cya

---

### Post by amjjawad on 2011-07-30
> **YesWeCan said:**
> I think oldfred is referring to the backup copy of the XP boot sector that is in the XP partition. Testdisk will let you restore this backup, or backup the current boot sector. Unfortunately, primal woman's XP partition did not contain a valid backup. And the promisingly named "Rebuild BS" facility did not work.


```
Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```

Any thoughts?

---

### Post by GregA on 2011-07-30
Hello Primal Women,

Let me suggest a different tack (approach).   Are you located in an area that has stores like a "Best Buy" that have a "Geek Squad" service?   

I think that despite the fantastic help messages/examples provided by the forum members, you may just need to have someone sit with you  and look at your system hands-on.   Do you have a local college or university near - - sometimes contacting a local professor or TA might result in a IT student or two that could take a look (you might have to bring the PC to them).

Anyway, check into that angle, you might find a low cost or even eager volunteer.

---

### Post by primal woman on 2011-07-31
> **amjjawad said:**
> primal woman, I already have explained many times HOWTO do that but for some reason you keep ignoring it.

I don't know what's the point of keep trying the same helpless procedure? sorry, not being rude at all but I just don't understand?

Myself and others have offered ALL what we have but you keep saying the same?!

Perhaps I need to sleep?

I keep saying the same maybe because I keep getting the same....no results, computer not co-operating, not doable. 

We worked together on skype and you walked me through step by step, but if you recall, there were several things that my computer would not do and I do not have the cd's I speak of and my xp cd/dvd does not have what oldfred speaks of. Nothing has worked. And oldfred said borrow an xp cd anyway to hit r to repair, not a totally erasing type cd (which I believe may be different) which is what we are going to do after I got an answer from this forum. This guy asked me what brand hard drive it is as it makes a difference. He has all the cd's to wipe hard drives clean except toshiba and fujitsu. 

And yes, there are other offers of info, but I have said I did not know how to do those things. Like 'run synaptic'. I have no idea and even asked about that among other things. Unless I missed it, I have not seen the answer to that. 

 I certainly was not ignoring at all. I am sorry I was unable to follow all the advice. And there certainly was a lot of it. I appreciate it. 
  Once upon a time a person could say 'right click on the mouse' and very few people knew what it meant. Now likely most people do. But when they don't, they need to have it explained. They may not even know what a mouse is! It is the same here. This is so in-depth that it is foreign material for the average person. 

Thanks for all the help.

---

### Post by amjjawad on 2011-07-31
> **primal woman said:**
> I keep saying the same maybe because I keep getting the same....no results, computer not co-operating, not doable. 

We worked together on skype and you walked me through step by step, but if you recall, there were several things that my computer would not do and I do not have the cd's I speak of and my xp cd/dvd does not have what oldfred speaks of. Nothing has worked. And oldfred said borrow an xp cd anyway to hit r to repair, not a totally erasing type cd (which I believe may be different) which is what we are going to do after I got an answer from this forum. This guy asked me what brand hard drive it is as it makes a difference. He has all the cd's to wipe hard drives clean except toshiba and fujitsu. 

And yes, there are other offers of info, but I have said I did not know how to do those things. Like 'run synaptic'. I have no idea and even asked about that among other things. Unless I missed it, I have not seen the answer to that. 

 I certainly was not ignoring at all. I am sorry I was unable to follow all the advice. And there certainly was a lot of it. I appreciate it. 
  Once upon a time a person could say 'right click on the mouse' and very few people knew what it meant. Now likely most people do. But when they don't, they need to have it explained. They may not even know what a mouse is! It is the same here. This is so in-depth that it is foreign material for the average person. 

Thanks for all the help.

I'm deeply sorry for my rudeness and harsh words, I shouldn't have written that but believe it or not, I have been awake for 3 days just to figure out the best way to help and fix the issue. I can understand how hard it could be because simply I've been in the same boat/situation that you are in right now, trust me and I was even rude with the people who tried to help me but then I learned and understood everything like how to deal with this forum, people, myself, etc and of course how to fix things.
It's a NEW world for everyone and not even the Linux Gurus/Geeks where Gurus/Geeks when they were born ... they learned that by time. We keep learning to th end of our lives, no doubt about it.

I have done all what I can and I'm out of ideas/suggestions in case there is any.
However, I suggest few more things:

1- Try to read the suggestions again but as per poster not as per the posts. How?
For example, read the whole thread and see what oldfred wrote or asked you to do.
Or
Read whatever YesWeCan asked you to do
Or
Read whatever "X" person/poster asked you to do
Or
Read whatever post I wrote

I think it's better because reading the whole thing at once will be like sitting in a small room with 10 people who are speaking loudly at the same time ... definitely you will not understand anything clearly.

**I'm sure the solution is somewhere between these posts but because there are too many of them, you can't find it.**

2- If there is something that "I' posted and it's NOT clear, please do let me know and I'll make sure to make it as clear as possible. I can't speak on others behalf but I'm sure they will do the same.

3- Note that, you can install Ubuntu now, any version/release of it then install XP later on when you figure out howto do that from the CDs that you already have but that of course "IF" your current CDs that you got have the ability to re-install XP on a wiped clean HDD.

4- I saw one of the suggestions here to ask for someone's else help or ask them to come over and have a look. It's a good idea too.

5- I've been dealing with people who don't even read/write and I had to explain how "M" letter for example looks like so that they can press the right button, etc... I was working as a Customer Service Executive in a Contact Center and believe me, you are MUCH better but you just need to take it easy and try it one by one. If I were you, I would be in the same position with all these posts.

Having that said, if you think that's too much already and you can't go any further, then do one thing ... don't try to fix anything anymore.
Too much is too bad.

6- You have been giving many choices and suggestions and we both know you haven't tried ALL yet.
What do you think? do you prefer many suggestions at the same time? 
OR
You prefer one advice/suggestion that you'll follow at one time?

Finally, if you need anything, please let me/us know.

Thanks and have a nice day.

AJ

---

### Post by primal woman on 2011-07-31
> **GregA said:**
> Hello Primal Women,

Let me suggest a different tack (approach).   Are you located in an area that has stores like a "Best Buy" that have a "Geek Squad" service?   

I think that despite the fantastic help messages/examples provided by the forum members, you may just need to have someone sit with you  and look at your system hands-on.   Do you have a local college or university near - - sometimes contacting a local professor or TA might result in a IT student or two that could take a look (you might have to bring the PC to them).

Anyway, check into that angle, you might find a low cost or even eager volunteer.

Yes, I am trying this. Hence how I found a computer place to call yet, but first found this person who said he can wipe it clean. 

I don't know much about a local college or anything yet. I just moved here. But I am checking. 

Sure hope that disc to wipe everything totally empty is ok to do. Unless I have missed it, no one here has answered whether it will. 
(Again; I have my xp media center emachine restore disc which restores my system to windows with or without a back up. My question is will it be able to do this if I totally wipe the hard drive clean? NO boot stuff; all the way back to 0's.)

Thanks for your advice.

---

### Post by primal woman on 2011-07-31
> **amjjawad said:**
> 

I think it's better because reading the whole thing at once will be like sitting in a small room with 10 people who are speaking loudly at the same time ... definitely you will not understand anything clearly.

**I'm sure the solution is somewhere between these posts but because there are too many of them, you can't find it.**

2- If there is something that "I' posted and it's NOT clear, please do let me know and I'll make sure to make it as clear as possible. I can't speak on others behalf but I'm sure they will do the same.

3- Note that, you can install Ubuntu now, any version/release of it then install XP later on when you figure out howto do that from the CDs that you already have but that of course "IF" your current CDs that you got have the ability to re-install XP on a wiped clean HDD.

4- I saw one of the suggestions here to ask for someone's else help or ask them to come over and have a look. It's a good idea too.

AJ


"reading the whole thing at once will be like sitting in a small room with 10 people who are speaking loudly at the same time"
 I agree, but sometimes it pays off too. If you look back, I've seen posts that say...no, don't do that because it won't work. And then it either makes it better for the layman or worse depending on which advice is correct. 

"I'll make sure to make it as clear as possible". 
Yes, you have been VERY clear and it has been very easy to follow your posts. But of course I was unable to do the reinstalls because my boot sector is still bad. (or grub2 needs to be sda instead of sda1) 

"you can install Ubuntu now, any version/release of it then install XP  later on when you figure out howto do that from the CDs that you already  have but that of course "IF" your current CDs that you got have the  ability to re-install XP on a wiped clean HDD."

I do know how to reinstall my xp, but it won't work due to the boot sector issue. And I don't want to  reinstall ubuntu yet if I'm going to wipe it clean and since it still has a problem. I do need both OS's as I like ubuntu, but as far as 10.04 anyway; I can't skype with video for some reason. (on laptop) and ubuntu also sometimes won't allow me to make changes to a word document, it saves it as a read only. I have to go to windows with the word document in order to be able to save changes on that very same document. and if I want those 'freeze up grey outs' I spoke of; I can get my stupid 10 second freeze ups on acer xp windows! 

Your big IF above is a great one. I still don't have that answer. I am guessing no one knows. And I don't know if that is common knowledge among even those who know so much about computers as you guys do. 

Thanks for the help and I appreciate your response.

---

### Post by amjjawad on 2011-07-31
As explained in this post: [http://ubuntuforums.org/showpost.php?p=11103495&postcount=175](http://ubuntuforums.org/showpost.php?p=11103495&postcount=175)

Testdisk did not help to fix the issue.

Since it's a test, I tried to install GRUB2 to sda. Of course nothing happened. XP wasn't bootable at this stage.

I decided to try the other way which is: Booting from XP CD, Hit "R" for repair and type "fixboot" then "fixmbr" (because GRUB2 was installed to the sda MBR). XP did not boot AT ALL. ALL what I get was the logo BUT that lasted for 1-2 seconds only and the PC restarted itself. Ubuntu was not bootable and this stage.

I booted from the LiveCD, installed GRUB2 to sda yet again and rebooted. Ubuntu worked.

I then ran:
```
sudo update-grub

```and rebooted.

SAME, XP showed the logo for 1-2 seconds then restarted.

**Ubuntu is fine, XP is no longer bootable.**

I remember the same happened with me before and I was unable to fix it ... in fact, I didn't even bother at that time to look for an answer.
It happened again today.

Some info:

I'm using now P4 @3.00GHz - 2M Cashe
2GB RAM
40GB HDD

I was wondering whether the HDD being a slave ... does this effect anything?
Yes, XP is installed in sda1 but the HDD is slave. Why it's slave? it's a long story but I can't do anything about it, it must be slave. I can't use my SATA HDD because it's not for testing at all.

Result of the current boot script is:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    75,925,503    36,833,280  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA30BBCC30BBBDAF                       ntfs       
/dev/sda2        2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b   ext4       
/dev/sda3        f1891946-988d-431b-9b54-1d8030b6dedd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CA30BBCC30BBBDAF
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
UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.863807678 = 24.549826560   boot/grub/core.img                             1
  28.908287048 = 31.040036864   boot/grub/grub.cfg                             1
  19.562500000 = 21.005074432   boot/initrd.img-2.6.38-8-generic               2
  22.863586426 = 24.549588992   boot/vmlinuz-2.6.38-8-generic                  1
  19.562500000 = 21.005074432   initrd.img                                     2
  22.863586426 = 24.549588992   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39086144    19543041    7  HPFS/NTFS
/dev/sda2        39092224    75925503    18416640   83  Linux
/dev/sda3        75925504    78176255     1125376   82  Linux swap / Solaris



```
I'm running out of ideas ... can't even think about anything at all ...

Edit: and I'm not going to format and install XP and Ubuntu again for the 3rd time ... I need a fresh air now!

---

### Post by amjjawad on 2011-07-31
> **primal woman said:**
> Your big IF above is a great one. I still don't have that answer. **I am guessing no one knows**. And I don't know if that is common knowledge among even those who know so much about computers as you guys do.

Yes, if I want to speak about myself only. I have no clue at all whether your current CD which you already have is capable of doing that job or not? 

THE ONLY one who can answer this question is: the place you bought your machine from OR someone who has exactly the same CD and same machine (maybe).

Perhaps you can search on Google to find about that?

Otherwise, I'm out of ideas ... sorry!

Edit:
Hey, why don't you try that? if you have NO important files and your machine is NOT booting anything at the moment ... why don't you find out yourself? :)

Wipe your HDD as I explained previously with screenshots and give it a try ... check my previous posts ... I explained in details how to do that. No harm at all to give it a try ;)

---

### Post by amjjawad on 2011-07-31
_[COLOR=Red]Primal Woman, these are the posts I was referring to:[/COLOR]_

[http://ubuntuforums.org/showpost.php?p=11101432&postcount=126](http://ubuntuforums.org/showpost.php?p=11101432&postcount=126)

GParted: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

Installing Ubuntu and its boot loader: [http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

How-to Dual Boot: [http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

---

### Post by primal woman on 2011-07-31
> **amjjawad said:**
> _[COLOR=Red]Primal Woman, these are the posts I was referring to:[/COLOR]_

[http://ubuntuforums.org/showpost.php?p=11101432&postcount=126](http://ubuntuforums.org/showpost.php?p=11101432&postcount=126)

GParted: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

Installing Ubuntu and its boot loader: [http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

How-to Dual Boot: [http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)


Thanks. I know I've tried so many many things. But thought I'd try again: post 126....went into BIOS restore defaults. Insert ubuntu CD and it takes FOREVER to finally get to the 'try ubuntu'. And that is where it sits. it is not even going to bring up my live ubuntu. Wheel just keeps spinning. 

Thanks for trying so hard to help.

---

### Post by oldfred on 2011-07-31
I also am losing track of what is where.

But to answer question on synaptic. If a command or program is unfamiliar you can always go to a terminal and type in man and the command.
man synaptic

But since it is a gui app you still have to know it is System, Administration, Synaptic Package Manager. Not sure exact way to get to it with the new gui in 11.04. 
```

NAME
       synaptic - graphical management of software packages

SYNOPSIS
       synaptic [options]

DESCRIPTION
       Synaptic  is a frontend for the apt package managent system.  It allows
       you to perform all actions of the command line tool apt-get in a graph&#8208;
       ical environemnt. This includes installing, upgrading, downgrading  and
       removing of single packages or even upgrading your whole system.

```If you reset BIOS to defaults that may be part of the reason It is slow loading. Some have had a default of a floppy drive and have no floppy, so it spends a lot of time looking for a floppy drive. Sometimes other settings can also cause issues.  If you did not save the settings, you have to be willing to experiment and do some research on what settings do what.
One site that discusses some settings.
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)
I also see amjjawd's link show an example of a BIOS screen also.

You can use Ubuntu, or any rescue LinuxCD to totally erase drive. Be sure you have correct drive if you do this:
Entire Drive - May take a long time where XdY is your drive like sda, some Linux may use hda, hdb etc:
sudo dd if=/dev/zero of=/dev/XdY
#example is for sdb, change to your drive:
sudo shred -n2 -v /dev/sdb
[http://www.dban.org/](http://www.dban.org/)

---

### Post by amjjawad on 2011-07-31
[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8088[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8089[/IMG]




Best Boot Sequence for BIOS:

[IMG]http://www.cuug.ab.ca/branderr/mepis/PhoenAward2.jpg[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

Regardless what BIOS do you have, the Boot Sequence should be the same in any BIOS:

First Device = CDROM
Second Device = Hard Disk Drive

---

### Post by YesWeCan on 2011-07-31
> **primal woman said:**
> Thanks. I know I've tried so many many things. But thought I'd try again: post 126....went into BIOS restore defaults. Insert ubuntu CD and it takes FOREVER to finally get to the 'try ubuntu'. And that is where it sits. it is not even going to bring up my live ubuntu. Wheel just keeps spinning.
Tina Turner: Big wheel keep on turnin'
This and some of your previous posts makes me wonder if your CD drive needs a clean. If you take it into a shop why not ask them to check it?
Also, when you boot the Ubuntu CD run "check disc for errors" to make sure the CD has been recorded properly and can be read ok. :)
A USB stick is a lot more reliable but some older PCs don't support booting from USB.

---

### Post by amjjawad on 2011-07-31
Well, my test mission has been accomplished successfully :D
Thank you SO MUCH oldfred, you are amazing.

I booted my machine with XP CD, pressed "R" to enter Repair Mode and did "chkdsk" 

First, it said there is no need and if you want anyway, use " /p" so I did it and ... 

My Test Machine is able to boot and login to both XP and Ubuntu 11.04 :D



> **amjjawad said:**
> As explained in this post: [http://ubuntuforums.org/showpost.php?p=11103495&postcount=175](http://ubuntuforums.org/showpost.php?p=11103495&postcount=175)

Testdisk did not help to fix the issue.

Since it's a test, I tried to install GRUB2 to sda. Of course nothing happened. XP wasn't bootable at this stage.

I decided to try the other way which is: Booting from XP CD, Hit "R" for repair and type "fixboot" then "fixmbr" (because GRUB2 was installed to the sda MBR). XP did not boot AT ALL. ALL what I get was the logo BUT that lasted for 1-2 seconds only and the PC restarted itself. Ubuntu was not bootable and this stage.

I booted from the LiveCD, installed GRUB2 to sda yet again and rebooted. Ubuntu worked.

I then ran:
```
sudo update-grub

```and rebooted.

SAME, XP showed the logo for 1-2 seconds then restarted.

**Ubuntu is fine, XP is no longer bootable.**

I remember the same happened with me before and I was unable to fix it ... in fact, I didn't even bother at that time to look for an answer.
It happened again today.

Some info:

I'm using now P4 @3.00GHz - 2M Cashe
2GB RAM
40GB HDD

I was wondering whether the HDD being a slave ... does this effect anything?
Yes, XP is installed in sda1 but the HDD is slave. Why it's slave? it's a long story but I can't do anything about it, it must be slave. I can't use my SATA HDD because it's not for testing at all.

Result of the current boot script is:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    75,925,503    36,833,280  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA30BBCC30BBBDAF                       ntfs       
/dev/sda2        2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b   ext4       
/dev/sda3        f1891946-988d-431b-9b54-1d8030b6dedd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CA30BBCC30BBBDAF
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
UUID=2ca142e9-ef4b-47ba-8e5d-6070bcde9e8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.863807678 = 24.549826560   boot/grub/core.img                             1
  28.908287048 = 31.040036864   boot/grub/grub.cfg                             1
  19.562500000 = 21.005074432   boot/initrd.img-2.6.38-8-generic               2
  22.863586426 = 24.549588992   boot/vmlinuz-2.6.38-8-generic                  1
  19.562500000 = 21.005074432   initrd.img                                     2
  22.863586426 = 24.549588992   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39086144    19543041    7  HPFS/NTFS
/dev/sda2        39092224    75925503    18416640   83  Linux
/dev/sda3        75925504    78176255     1125376   82  Linux swap / Solaris



```
I'm running out of ideas ... can't even think about anything at all ...

Edit: and I'm not going to format and install XP and Ubuntu again for the 3rd time ... I need a fresh air now!

---

### Post by YesWeCan on 2011-07-31
> **amjjawad said:**
> I'm now on testdisk and I'll try to do this for the last time before going to bed ... it's 6:00am here :(
Looks like your commitment paid off. :)

---

### Post by oldfred on 2011-07-31
@amjjawad
Glad you got it working. Good to know something works eventually.

Now i wonder if chkdsk should maybe be first on the list of things to run, so other fixes may work or work better?

I now know that the PBR has a link to the backup PBR. And the backup PBR is now the last sector of the NTFS partition. So if the resize software did not adjust that and maybe other settings it may be looking in the wrong place?

---

### Post by YesWeCan on 2011-07-31
> **oldfred said:**
> I now know that the PBR has a link to the backup PBR. And the backup PBR is now the last sector of the NTFS partition. So if the resize software did not adjust that and maybe other settings it may be looking in the wrong place?
Very interesting. I didn't catch the full sequence of events in this test but is the implication that the Ubuntu installer breaks the backup BS access when it shrinks the XP partition?

---

### Post by amjjawad on 2011-07-31
> **oldfred said:**
> @amjjawad
Glad you got it working. Good to know something works eventually.

Now i wonder if chkdsk should maybe be first on the list of things to run, so other fixes may work or work better?


Yes, finally something at least is working ... thanks :)

Well, I'm not sure whether it should be the first to run or the last? sda1, which has Windows Boot Loader and got overwritten by GRUB2, it should have GRUB2 info instead of Windows Boot Loader so the question will be ... is "chkdsk" able to fix that? I don't think so ... otherwise, "fixboot" wouldn't be needed, right?

My guess is that ... one must first run "fixboot" then "chkdsk".
I wish I could do it again but I have no time for today or the coming days.

As whether testdisk is able to fix such issue? as you know, I tired twice and it didn't help at all. Maybe run "chkdsk" after testdisk? hmmm, I don't really know?!


> I now know that the PBR has a link to the backup PBR. And the backup PBR  is now the last sector of the NTFS partition. So if the resize software  did not adjust that and maybe other settings it may be looking in the  wrong place?

Definitely not in my test because: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

I always do the partition part before installation. 

It would be great if we could find out what was going on!

---

### Post by amjjawad on 2011-07-31
> **YesWeCan said:**
> Looks like your commitment paid off. :smile:
Yes, apparently it did :D


> **YesWeCan said:**
> Very interesting. I didn't catch the full sequence of events in this test but is the implication that the **Ubuntu installer breaks the backup BS access when it shrinks the XP partition?**

No, because I did not shrink XP partition :)

[http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

---

### Post by drs305 on 2011-07-31
> **YesWeCan said:**
> Very interesting. I didn't catch the full sequence of events in this test but is the implication that the Ubuntu installer breaks the backup BS access when it shrinks the XP partition?

> **oldfred said:**
> I now know that the PBR has a link to the backup PBR. And the backup PBR is now the last sector of the NTFS partition. So if the resize software did not adjust that and maybe other settings it may be looking in the wrong place?

If the Windows partition is resized, I can imagine the PRB backup being rewritten since the partition's data changes. Although the start of the Windows partition may not change, partitioning would change other aspects. I don't know what is recorded in the PBR but it would seem logical to me if the backup was to serve to recover from corruption and not from an intentional resizing. 

I don't know that it works that way of course. It would explain why so many times after jumping through all the testdisk hoops to get to the Restore point testdisk then says the two are identical (and provides no BackupBS). There was a point where I directed so many users to TestDisk only to run into the "no BackupBS" result I stopped directing them there unless nothing else worked. But it would be interesting to see how many of those had problems after partitioning.

---

### Post by YesWeCan on 2011-07-31
> **primal woman said:**
> then when done it said, loadint15 driver error at x:/int15.sys
I just realised this error arose when you were using the Acer recovery CD, which is not designed for your system.

I don't think this error has anything to do with your hard disk needing to be erased. These recovery CDs are customised to their own systems.

What you have are manufacturer's system recovery CDs. What you need is a Microsoft XP installation CD.

---

### Post by YesWeCan on 2011-07-31
> **amjjawad said:**
> No, because I did not shrink XP partition :)
Ok.
I just noticed your post #176 where you asked me to comment.
Could you confirm that this is what happened?
1. You partitioned your disk
2. You installed XP and Ubuntu
3. You wrote Grub to the XP PBR
4. You ran testdisk and restored from "backup BS"
5. XP booted but was somehow messed up
6. You reinstalled XP
7. You ran testdisk and it said both the BS and the backup BS were OK but that they were different?

Is that right?

---

### Post by primal woman on 2011-07-31
Maybe emachine will not work as a dual boot with ubuntu. We wiped  the hard drive totally empty. Then reinstalled xp windows with my emachine xp CD/DVD system restore (only one was supplied when new) disc. Then rebooted  and computer was like brand new. Did not bother to do any updating or anything before I tried ubuntu again. So put in live CD of ubuntu and loaded ubuntu onto it with the first  choice instead of the last 'something else' choice. It kindly  automatically gave ubuntu almost half the hard drive. We booted a few  times, neither time allowed windows to boot. Tried an xp windows disc so we could hit r and try to repair and that did not work. Ubuntu was working fine. (as it did the first 2-4  times before, then no longer worked) 

Then I brought it home with a different  xp windows disc borrowed; so I could hit r to repair. I booted up with  cd in drive; NOTHING. I took cd out and booted; NOTHING! It no longer  boots at all. I get a blank screen and a fan running on the inside of the case! 

This tells me that for one...I likely did not do anything wrong to start with as I installed ubuntu totally different and with very little direct answers from a human. It did it all on its own. 


Yeswecan said: "This and some of your previous posts makes me wonder if your CD drive  needs a clean. If you take it into a shop why not ask them to check it?
Also, when you boot the Ubuntu CD run "check disc for errors" to make  sure the CD has been recorded properly and can be read ok. :smile:"

Evidently it did not need cleaning as it all installed just fine this morning. I have not run check disc on the CD. 
I don't have a usb/sd card large enough.

---

### Post by amjjawad on 2011-08-01
> **YesWeCan said:**
> Ok.
I just noticed your post #176 where you asked me to comment.
Could you confirm that this is what happened?
1. You partitioned your disk
2. You installed XP and Ubuntu
3. You wrote Grub to the XP PBR
4. You ran testdisk and restored from "backup BS"
5. XP booted but was somehow messed up
6. You reinstalled XP
7. You ran testdisk and it said both the BS and the backup BS were OK but that they were different?

Is that right?

1- HDD were partitioned using GParted before installing anything
2- XP installed then Ubuntu
3- GRUB2 were installed in sda1 which is Windows XP PBR
4- Yes.
5- Yes.
6- I formatted my HDD and installed XP then Ubuntu and did the same with Ubuntu, install GRUB2 to sda1 (XP PBR).
7- Yes.

That's what happened with test 1 and test 2.

I then got this problem: [http://ubuntuforums.org/showpost.php?p=11104576&postcount=182](http://ubuntuforums.org/showpost.php?p=11104576&postcount=182)

Then issue got fixed here: [http://ubuntuforums.org/showpost.php?p=11105875&postcount=189](http://ubuntuforums.org/showpost.php?p=11105875&postcount=189)

---

### Post by amjjawad on 2011-08-01
After solving the previous issue in Test 2, that encouraged me to carry on with a 3rd test but something happened and I'd like to share it with you as always

Remember: After solving the issue in test 2 and as explained in my last post, BOTH Ubuntu and XP were bootable without any issue.


1- I re-installed Ubuntu only
2- GRUB2 were installed in sda1 (XP PBR) instead of sda (MBR).
3- After installation, Ubuntu was bootable but XP wasn't - obviously. So far so good.

4- I decided to try XP CD to fix the issue (fixboot) and then if it failed for some reason, I would try testdisk.

5- I ran from Repair Mode: "fixbook" then "chkdsk".

[COLOR=Black]6- after rebooting, BOTH Systems worked **_WITHOUT re-installing GRUB2 to sda (MBR)_** so HOW COME?
I just don't believe it![/COLOR]

7- I did not run "fixmrb". I forgot GRUB2 was previously installed in the MBR in test2. BUT ... since I formated sda2 which is the root partition and where all the files including most of GRUB2 files are stored, does it mean MBR still has the code or the link to the GRUB2 files? even after formatting sda2 (root partition) that will work? didn't know that before :)


This is the result of the boot script after the above try (after using fixboot and chkdsk to fix the issue).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 129.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    75,925,503    36,833,280  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1967 MB, 1967128576 bytes
1 heads, 62 sectors/track, 61968 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *            129     3,842,047     3,841,919   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA30BBCC30BBBDAF                       ntfs       
/dev/sda2        c4285560-d05e-4080-87ac-628e7136df0a   ext4       
/dev/sda3        f1891946-988d-431b-9b54-1d8030b6dedd   swap       
/dev/sdf1        6E1F-0EE2                              vfat       LG-MC

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/LG-MC             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4285560-d05e-4080-87ac-628e7136df0a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4285560-d05e-4080-87ac-628e7136df0a ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CA30BBCC30BBBDAF
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
UUID=c4285560-d05e-4080-87ac-628e7136df0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.975814819 = 35.407511552   boot/grub/core.img                             1
  22.887046814 = 24.574779392   boot/grub/grub.cfg                             1
  19.300334930 = 20.723576832   boot/initrd.img-2.6.38-8-generic               2
  32.974102020 = 35.405672448   boot/vmlinuz-2.6.38-8-generic                  1
  19.300334930 = 20.723576832   initrd.img                                     2
  32.974102020 = 35.405672448   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdf1

00000000  eb 3c 90 61 6e 64 72 6f  69 64 20 00 02 40 01 00  |.<.android ..@..|
00000010  02 00 02 00 00 f0 eb 00  10 00 04 00 00 00 00 00  |................|
00000020  70 9f 3a 00 00 00 29 e2  0e 1f 6e 4c 47 2d 4d 43  |p.:...)...nLG-MC|
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa 31  |      FAT16   .1|
00000040  c0 8e d0 bc 00 7c fb 8e  d8 e8 00 00 5e 83 c6 19  |.....|......^...|
00000050  bb 07 00 fc ac 84 c0 74  06 b4 0e cd 10 eb f5 30  |.......t.......0|
00000060  e4 cd 16 cd 19 0d 0a 4e  6f 6e 2d 73 79 73 74 65  |.......Non-syste|
00000070  6d 20 64 69 73 6b 0d 0a  50 72 65 73 73 20 61 6e  |m disk..Press an|
00000080  79 20 6b 65 79 20 74 6f  20 72 65 62 6f 6f 74 0d  |y key to reboot.|
00000090  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
Perhaps even if I formatted XP and Ubuntu and re-installed as per the above scenario, since the MBR won't be touched, I guess fixboot alone will fix the issue.

Looks like these fews tests will give me lots of experience I wouldn't imagine to learn in months :)

Seriously, nothing better than trying by your own hands :)

**Edit:**
This will give me only one conclusion ... it's recommended to "Create New Partition Table" in such scenarios to avoid conflicts, etc. Before installing anything, one can do this simple step, especially if the HDD was previously used for Dual-Booting, etc.

---

### Post by YesWeCan on 2011-08-01
> **amjjawad said:**
> 1- HDD were partitioned using GParted before installing anything
2- XP installed then Ubuntu
3- GRUB2 were installed in sda1 which is Windows XP PBR
4- Yes.
5- Yes.
6- I formatted my HDD and installed XP then Ubuntu and did the same with Ubuntu, install GRUB2 to sda1 (XP PBR).
7- Yes.

That's what happened with test 1 and test 2.

I then got this problem: [http://ubuntuforums.org/showpost.php?p=11104576&postcount=182](http://ubuntuforums.org/showpost.php?p=11104576&postcount=182)

Then issue got fixed here: [http://ubuntuforums.org/showpost.php?p=11105875&postcount=189](http://ubuntuforums.org/showpost.php?p=11105875&postcount=189)
Ok, so after 7 you restored from the backup BS using testdisk but found XP still wouldn't boot until you used the XP CD to run chdsk?


I would like to know why primal woman's backup BS was BAD. Installing Grub to the PBR should not have affected the backup. So was there no backup in the first place or did something else break it?

---

### Post by amjjawad on 2011-08-01
> **YesWeCan said:**
> Ok, so after 7 you restored from the backup BS using testdisk but found XP still wouldn't boot until you used the XP CD to run chdsk?


After #7, BackupBS wasn't helpful as both PBR and its backup were NOT identical so testdisk didn't help. Yes, I used the XP CD to fixboot and then chkdsk.

> 
I would like to know why primal woman's backup BS was BAD. Installing Grub to the PBR should not have affected the backup. So was there no backup in the first place or did something else break it?Well, she used "Something Else" to install Ubuntu on her desktop:

> **primal woman said:**
> I installed ubuntu 11.04 onto emachine  desktop. I used the third option titled 'something else' and partitioned  almost half my hard drive for ubuntu. I must have done something wrong.  It does not give me an option for boot up at all, just goes right into  ubuntu. Works fine, but I wanted the option to boot up in windows. 
The First Post.

If *there is a backup* that should be stored at the end of XP Partition and that partition got resized, then that explains what happened.

Honestly, this is my first time to learn that there is a backup for PBR and it can be stored.

Perhaps, there is no backup anyway but if that's true, then does it mean sometimes there is backup and some other time there is no backup?

Seriously, it's getting so much complicated and in the same time, so much interested.

I still believe in my theory. MBR must be overwritten and a new partition table must be created to fix this issue.

The major issue in this thread is ... OP doesn't have Windows XP CD.
I don't think fixboot, fixmbr or even chkdsk will solve the issue but hope I'm wrong. 

There is two solutions left and I'm seriously out of ideas:

_[COLOR=Red]**Solution 1:**[/COLOR]_
Primal Woman needs to use Windows XP CD that she borrowed from someone to do this:
a) From Repair mode: **fixboot **then [COLOR=Black]**fixmbr**[/COLOR] then [COLOR=Black]**chkdsk**[/COLOR].
b) Exit (it's a command by the way that need to be written to exit)
c) XP should work fine
d) If XP didn't work for some weird reason then ... 

_[COLOR=Red]**Solution 2:**[/COLOR]_
As I already explained many times before, Ubuntu LiveCD must be used. GParted to create new partition table, create partitions as previously explained  and start installing from scratch.

But then ... another problem is ... Primal Woman doesn't know whether her current CDs (Windows XP Media Center) is able actually to install XP from Scratch or not?

---

### Post by primal woman on 2011-08-01
> **amjjawad said:**
> 

Well, she used "Something Else" to install Ubuntu on her desktop:


The major issue in this thread is ... OP doesn't have Windows XP CD.
I don't think fixboot, fixmbr or even chkdsk will solve the issue but hope I'm wrong. 

There is two solutions left and I'm seriously out of ideas:

_[COLOR=Red]**Solution 1:**[/COLOR]_
Primal Woman needs to use Windows XP CD that she borrowed from someone to do this:
a) From Repair mode: **fixboot **then [COLOR=Red]**fixmbr**[/COLOR] then **[COLOR=Red]chkdsk[/COLOR]**.
b) Exit (it's a command by the way that need to be written to exit)
c) XP should work fine
d) If XP didn't work for some weird reason then ... 

_[COLOR=Red]**Solution 2:**[/COLOR]_
As I already explained many times before, Ubuntu LiveCD must be used. GParted to create new partition table, create partitions as previously explained  and start installing from scratch.

But then ... another problem is ... Primal Woman doesn't know whether her current CDs (Windows XP Media Center) is able actually to install XP from Scratch or not?


I know it is easy to miss posts here, so I'll say it again: 
With my totally wiped clean hard drive and reinstalls of both xp and ubuntu (this time let it do it on its own from first option), I STILL have a problem. See post #198. 


And as I have posted: I used two different xp windows to try 'r' for repair, both to no avail. 

Tried you solution 2 stuff. didn't work. 

And as posted in 198, it did work to wipe drive clean and reinstall totally fresh. 

Hope you are getting some sleep now. Thanks for your help.

---

### Post by amjjawad on 2011-08-01
> **primal woman said:**
> I know it is easy to miss posts here, so I'll say it again: 
With my totally wiped clean hard drive and reinstalls of both xp and ubuntu (this time let it do it on its own from first option), I STILL have a problem. See post #198. 


And as I have posted: I used two different xp windows to try 'r' for repair, both to no avail. 

Tried you solution 2 stuff. didn't work. 

And as posted in 198, it did work to wipe drive clean and reinstall totally fresh. 

Hope you are getting some sleep now. Thanks for your help.

How did you wipe your HDD?
If you didn't create new partition table as I have explained, then I guess no matter how many times you try what you have done in post 198, it will not work.

Try to download a fresh new copy of Ubuntu from your laptop. Follow the instructions on Ubuntu site of how to burn it to a CD and don't forget MD5SUM before burning. 
Use the new CD to create new partition table.

Then ... try what you have done in post 198.

If still nothing will change, then there MUST be something totally different and I have no idea what is it.

[COLOR=Red]**Edit**[/COLOR]:
I have read your post 198.

If you installed GRUB2 to MBR (sda) then both XP and Ubuntu should work.
They did not work and that proves my theory that the Partition Table MUST be overwritten and a NEW one must be created. Otherwise, can someone explain to us why it didn't work and the HDD was wiped???

---

### Post by madjr on 2011-08-01
> **primal woman said:**
> I know it is easy to miss posts here, so I'll say it again: 
With my totally wiped clean hard drive and reinstalls of both xp and ubuntu (this time let it do it on its own from first option), I STILL have a problem. See post #198. 


And as I have posted: I used two different xp windows to try 'r' for repair, both to no avail. 

Tried you solution 2 stuff. didn't work. 

And as posted in 198, it did work to wipe drive clean and reinstall totally fresh. 

Hope you are getting some sleep now. Thanks for your help.

if am not mistaken, your drive should look something similar to this now with gparted:

[IMG]http://2.bp.blogspot.com/-AvyWTPv93V0/Tfw54V5DJ_I/AAAAAAAAB_A/Ex2glwo1WQQ/s1600/gparted+in+ubuntu+11.04+-+screenshot.png[/IMG]

can you take a screen?


and if needed this guide can tell you about everything about partitioning ubuntu:
[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)


also with **boot-repair app**, you can install windows "after" ubuntu, as many times as you like, and fixes grub automatically each time from live-cd, no problems.
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

[IMG]http://lh5.googleusercontent.com/-fT9AjTaZBsE/Tfn6P5h8n_I/AAAAAAAAE7M/NZHXeZLYQVg/boot-repair.png[/IMG]

---

### Post by amjjawad on 2011-08-01
If you'll tell me that you have already tried EVERYTHING already then please do this:

1- Create New Partition Table
2- Create ONE Partition for Windows and leave the remaining Space untouched. Just leave it unallocated. Yes, you need GParted.
3- Install Windows XP ONLY.
4- If it boots fine with NO problems whatsoever for 1-2 days, after many restarting, etc etc, then go ahead and install Ubuntu the same way I have previously explained. Yes, you need to download Ubuntu again and burn new CD in case you suspect your current CD for any reason.
5- Make sure GRUB2 is installed - as explained - in sda NOT sda1.
6- After installation is done, reboot and wait.
7- GRUB menu should show up. Select XP. If you can't boot into XP then run the boot script (last link in my signature) and post the result here again.
8- If your boot script is fine and both systems have their own bootloader in its place AND you still can't boot into XP then I really don't know how to fix that.

Finally (I keep saying that but keep posting more suggestions) ... do us a favor and try Ubuntu 10.04. Just try it. Yes, install it instead of 11.04 on your PC.

Thank you!

---

### Post by amjjawad on 2011-08-01
> **madjr said:**
> if am not mistaken, your drive should look something similar to this now with gparted:


Simply, it should be something similar to the attached screen.

---

### Post by drs305 on 2011-08-01
> **amjjawad said:**
> 
1- I re-installed Ubuntu only
2- GRUB2 were installed in sda1 (XP PBR) instead of sda (MBR).
3- After installation, Ubuntu was bootable but XP wasn't - obviously. So far so good.

4- I decided to try XP CD to fix the issue (fixboot) and then if it failed for some reason, I would try testdisk.

5- I ran from Repair Mode: "fixbook" then "chkdsk".

[COLOR=Black]6- after rebooting, BOTH Systems worked **_WITHOUT re-installing GRUB2 to sda (MBR)_** so HOW COME?
I just don't believe it![/COLOR]

7- I did not run "fixmrb". I forgot GRUB2 was previously installed in the MBR in test2. BUT ... since I formated sda2 which is the root partition and where all the files including most of GRUB2 files are stored, does it mean MBR still has the code or the link to the GRUB2 files? even after formatting sda2 (root partition) that will work? didn't know that before :)


You installed XP, then Ubuntu (normally, with G2 to the MBR). Then you started your experiments and installing to the sda1 PBR.

When you installed Grub 2 to the PBR of sda1, it did leave the MBR unchanged. If you elect to install to a partition, G2 assumes you have another bootloader on the MBR that will continue to control things (such as chainloading to G2 in sda1) and won't alter it.

Since you already had the MBR pointing to your Ubuntu installation, it continued to work.

---

### Post by YesWeCan on 2011-08-01
> **amjjawad said:**
> After #7, BackupBS wasn't helpful as both PBR and its backup were NOT identical so testdisk didn't help. Yes, I used the XP CD to fixboot and then chkdsk.
They were both not identical? What does that mean?

If you installed Grub in the PBR I would expect testdisk to report the BS is OK and the backup BS is OK and they are different. In this case, you would want to restore the BS from the backup BS.

---

### Post by primal woman on 2011-08-01
I see I have a few more suggestions. I'll try not to be rude here, but please read my posts again. 

And in case you missed it again; I get NOTHING. MY computer now is  a fan and a black/blank screen. NO live CD or restore CD works AT ALL. 

I do not know how to make myself more clear than that. Sorry.

---

### Post by amjjawad on 2011-08-01
> **YesWeCan said:**
> They were both not identical? What does that mean?

If you installed Grub in the PBR I would expect testdisk to report the BS is OK and the backup BS is OK and they are different. In this case, you would want to restore the BS from the backup BS.

[http://ubuntuforums.org/showpost.php?p=11103495&postcount=175](http://ubuntuforums.org/showpost.php?p=11103495&postcount=175)

Shall we start new thread for me, you, oldfred and maybe drs305 to discuss? this is getting so complicated with 20 pages thread.

---

### Post by amjjawad on 2011-08-01
> **primal woman said:**
> I see I have a few more suggestions. I'll try not to be rude here, but please read my posts again. 

And in case you missed it again; I get NOTHING. MY computer now is  a fan and a black/blank screen. NO live CD or restore CD works AT ALL. 

I do not know how to make myself more clear than that. Sorry.

Do you know how to open your case? if I'll ask you to do something, will you be able to do it? like unplug your HDD or take the mother board battery out?

---

### Post by YesWeCan on 2011-08-01
> **primal woman said:**
> Maybe emachine will not work as a dual boot with ubuntu. We wiped  the hard drive totally empty. Then reinstalled xp windows with my emachine xp CD/DVD system restore (only one was supplied when new) disc. Then rebooted  and computer was like brand new. Did not bother to do any updating or anything before I tried ubuntu again. So put in live CD of ubuntu and loaded ubuntu onto it with the **first  choice** instead of the last 'something else' choice. It kindly  automatically gave ubuntu almost half the hard drive. We booted a few  times, **neither time allowed windows to boot**. Tried an xp windows disc so we could hit r and try to repair and that did not work. Ubuntu was working fine. (as it did the first 2-4  times before, then no longer worked)
Specifics are very important. What was the "first choice"? Was it "install alongside Windows"?
"neither time allowed windows to boot" - do you mean that it booted into Ubuntu without offering you a menu, or do you mean it had a menu but XP would not boot when you selected it?

Trying to repair XP is not necessarily the correct course anymore because the installation is now different than before. So we need to see what it now is before knowing how to proceed. Another bootinfoscript output would be useful.

---

### Post by amjjawad on 2011-08-01
> **drs305 said:**
> You installed XP, then Ubuntu (normally, with G2 to the MBR). Then you started your experiments and installing to the sda1 PBR.

When you installed Grub 2 to the PBR of sda1, it did leave the MBR unchanged. If you elect to install to a partition, G2 assumes you have another bootloader on the MBR that will continue to control things (such as chainloading to G2 in sda1) and won't alter it.



Not exactly drs305 :)

I did 3 tests.


1- With GParted, I created 3 partitions: NTFS for XP (sda1), Ext4 for Root (sda2) and Swap-Linux for Swap (sda3).

2- I installed XP.

3- I installed Ubuntu and purposely, chose to install GRUB2 to sda1 (XP Partition) NOT sda.

4- Re-installed GRUB2 to MBR (sda) but that did not fix the issue.

--- test 1 ends here ---

5- I formated sda1 and installed XP once more

6- I formatted sda2 and installed Ubuntu once more

7- GRUB2 was installed yet again purposely to sda1 instead of sda.

8- Re-installed GRUB2 to MBR (sda) after testdisk failed for the 2nd time to fix the issue ([http://ubuntuforums.org/showpost.php?p=11103495&postcount=175](http://ubuntuforums.org/showpost.php?p=11103495&postcount=175)).

--- test 2 ends here ----

9- I formatted sda2 ONLY and installed Ubuntu for the 3rd time. Didn't touch XP this time.

10- GRUB2 was installed in sda1 yet again.

11- From XP CD, I ran fixboot and chkdsk

12- Rebooted

13- BOTH SYSTEMS worked just fine without the need to re-install GRUB2.

My guess is ... MBR remained untouched even though sda2 (ubuntu partition) got formatted so MBR pointed again to that partition even after formatting sda2.

Am I right?


> Since you already had the MBR pointing to your Ubuntu installation, it continued to work.
Even if I format Ubuntu Partition where everything is stored there?
Except of course a link from MBR to the partition.

---

### Post by amjjawad on 2011-08-01
> **YesWeCan said:**
> Trying to repair XP is not necessarily the correct course anymore because the installation is now different than before. So we need to see what it now is before knowing how to proceed. **Another bootinfoscript output would be useful**.

I second that.

---

### Post by madjr on 2011-08-01
> **primal woman said:**
> I see I have a few more suggestions. I'll try not to be rude here, but please read my posts again. 

And in case you missed it again; I get NOTHING. MY computer now is  a fan and a black/blank screen. NO live CD or restore CD works AT ALL. 

I do not know how to make myself more clear than that. Sorry.

no worries, you have your own geeksquadt here !! :D

---

### Post by drs305 on 2011-08-01
> **amjjawad said:**
> 
8- Re-installed GRUB2 to MBR (sda) after testdisk failed for the 2nd time to fix the issue ([http://ubuntuforums.org/showpost.php?p=11103495&postcount=175](http://ubuntuforums.org/showpost.php?p=11103495&postcount=175)).

This step put G2 back on the MBR and nothing you did after that touched it.

---

### Post by amjjawad on 2011-08-01
> **drs305 said:**
> This step put G2 back on the MBR and nothing you did after that touched it.

I see :)
That explain a lots, thank you :D

Time for Test 4 :P 
Nuh, just kidding ... not today!

---

### Post by primal woman on 2011-08-01
> **YesWeCan said:**
> Specifics are very important. What was the "first choice"? Was it "install alongside Windows"?
"neither time allowed windows to boot" - do you mean that it booted into Ubuntu without offering you a menu, or do you mean it had a menu but XP would not boot when you selected it?

Trying to repair XP is not necessarily the correct course anymore because the installation is now different than before. So we need to see what it now is before knowing how to proceed. Another bootinfoscript output would be useful.


I have opened that case, yes. That is how I vaccummed it as I posted. Also that is how I took the hard drive out to put it into another computer to wipe clean, etc. 

I would have NEVER thought that a person could run " **Another bootinfoscript output would be useful**." when the computer does NOTHING when booting up, but make the fan run. HOW...HOW....HOW do you run a bootinfoscript when all that is running is a fan?????



What was the "first choice"? Was it "install alongside Windows"? YES, as I have said. 

do you mean that it booted into Ubuntu without offering you a menu? YES again, same as before.

---

### Post by primal woman on 2011-08-06
Interesting that everyone just left. I do appreciate all of the help truly. And looks like my posts were not really read through when I received answers. But at any rate, I kept trying and I got it to work. Or at least I got something to work. So I consider this issue unsolved, but I made it work another way.

---

### Post by drs305 on 2011-08-06
> **primal woman said:**
> Interesting that everyone just left. I do appreciate all of the help truly. And looks like my posts were not really read through when I received answers. But at any rate, I kept trying and I got it to work. Or at least I got something to work. So I consider this issue unsolved, but I made it work another way.

I think we thought you had either given up or we were out of ideas. 

At any rate, I'm glad you have at least *something* working now.

I'd recommend you mark this SOLVED. I know it's not an ideal solution, but you can edit the first post to say it isn't really solved but you didn't find an answer and don't want to pursue it. 

Marking it solved and editing the first post will do two things. It will prevent someone from trying to read through the entire post to try to find out what worked, and it will probably stop new helpers from trying to provide assistance. At this point, it would be almost impossible for someone to fully understand the thread.

If you need help, I think starting an entirely new thread would be in everyone's best mental health.  ;-)

Best wishes and please don't let this thread discourage you from seeking help on the Ubuntu forums.

---

### Post by amjjawad on 2011-08-07
> **primal woman said:**
> Interesting that everyone just left.

Not going to speak on someone's else behalf but myself, was waiting for another post rather than this: [http://ubuntuforums.org/showpost.php?p=11109037&postcount=219](http://ubuntuforums.org/showpost.php?p=11109037&postcount=219)

And I also agree with drs305. I thought you gave up but again, was waiting for another post from you :)


> But at any rate, I kept trying and I got it to work. 

GLAD to know that :)

> Or at least I got something to work. So I consider this issue unsolved, but I made it work another way.As always, we still here if you need us.

---

### Post by amjjawad on 2011-08-07
> **drs305 said:**
> I think we thought you had either given up or we were out of ideas. 

At any rate, I'm glad you have at least *something* working now.

I'd recommend you mark this SOLVED. I know it's not an ideal solution, but you can edit the first post to say it isn't really solved but you didn't find an answer and don't want to pursue it. 

**Marking it solved and editing the first post** will do two things. It will prevent someone from trying to read through the entire post to try to find out what worked, and it will probably stop new helpers from trying to provide assistance. At this point, it would be almost impossible for someone to fully understand the thread.

**[COLOR=Red]If you need help, I think starting an entirely new thread would be in everyone's best mental health.[/COLOR]**  ;-)

Best wishes and [COLOR=Red]please don't let this thread discourage you from seeking help on the Ubuntu forums[/COLOR].

I totally agree with the above post, especially the highlighted text :)

---

### Post by amjjawad on 2011-08-13
6 Days now and we didn't hear back from the OP.

---

