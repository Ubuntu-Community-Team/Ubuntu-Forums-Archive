---
title: "Partition full of important data lost. Need help recovering it!"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by iskald on 2011-06-19
Hi!

Last night I was running W7 and was putting everything of my important stuff from my C: disk to my D: disk so I could install Kubuntu on my laptop. Now I have 2 OS's, which is OK. Both of them on my former C: disk. The problem is that I can't seem to find the D: where all my data is.

Right now I have SDA1 at 14 GB which is the recovery partition. I have SDA2 which is the partition with the boot (86 GB). Anb I have SDA3 which seems to have two "subs". These two are ext4 (26 GB) and SDA5 (335 GB. this is the lost one where all my data is, and is inactive).

All my data is on the Unknown. It says that it's unformatted, but I can't seem to access it without doing so.
Currently I can access SDA2 (Windows) and ext4 (Linux). 

What I really need, if possible, is to access the SDA5 so that I can retrieve all of my data..

Can anyone try to understand what I just wrote and help me? ;)

---

### Post by westie457 on 2011-06-19
> **iskald said:**
> Hi!

Last night I was running W7 and was putting everything of my important stuff from my C: disk to my D: disk so I could install Kubuntu on my laptop. Now I have 2 OS's, which is OK. Both of them on my former C: disk. The problem is that I can't seem to find the D: where all my data is.

Right now I have SDA1 at 14 GB which is the recovery partition. I have SDA2 which is the partition with the boot (86 GB). Anb I have SDA3 which seems to have two "subs". These two are ext4 (26 GB) and SDA5 (335 GB. this is the lost one where all my data is, and is inactive).

All my data is on the Unknown. It says that it's unformatted, but I can't seem to access it without doing so.
Currently I can access SDA2 (Windows) and ext4 (Linux). 

What I really need, if possible, is to access the SDA5 so that I can retrieve all of my data..

Can anyone try to understand what I just wrote and help me? ;)

Hi 
Using the words of 'coffecat'. This looks like a job for testdisk.

Open 'Ubuntu Software Centre' > Search for 'testdisk' > check what it does > click on 'Install'.
When this process has finished open a terminal ```
sudo testdisk
```

---

### Post by coffeecat on 2011-06-19
I came across this thread by chance and found that I have been quoted! Which is flattering. I'm sure that westie457 is right and that you will need to use testdisk, but there are some important things to think about first.

Most importantly: don't boot into Kubuntu on the ext4 partition. At least for the time being. It's not clear exactly what your partition layout was like before you installed Kubuntu, but on the off-chance that the Kubuntu partition has overwritten part of your former D: partition, it would be wise not to use it until we have determined what the situation is.

Next - I can see that you have a logical partition (sda5), so there must be an extended partition, which might be sda3, but where your Kubuntu partition fits into all this is not clear. But there's a good way to find out. Boot up with a Kubuntu or Ubuntu live CD, and choose "try Kubuntu/Ubuntu" so that you get  the live desktop. Now go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Although the boot script is intended for boot problems, it is also an excellent tool in situations like this for seeing what is on a system and it should give us the information we need to decide what needs to be done.

---

### Post by iskald on 2011-06-20
> **coffeecat said:**
> I came across this thread by chance and found that I have been quoted! Which is flattering. I'm sure that westie457 is right and that you will need to use testdisk, but there are some important things to think about first.

Most importantly: don't boot into Kubuntu on the ext4 partition. At least for the time being. It's not clear exactly what your partition layout was like before you installed Kubuntu, but on the off-chance that the Kubuntu partition has overwritten part of your former D: partition, it would be wise not to use it until we have determined what the situation is.

Next - I can see that you have a logical partition (sda5), so there must be an extended partition, which might be sda3, but where your Kubuntu partition fits into all this is not clear. But there's a good way to find out. Boot up with a Kubuntu or Ubuntu live CD, and choose "try Kubuntu/Ubuntu" so that you get  the live desktop. Now go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Although the boot script is intended for boot problems, it is also an excellent tool in situations like this for seeing what is on a system and it should give us the information we need to decide what needs to be done.

I didn't actually know I had quoted you :o

Anyways.. I did as you told me, and here is the results.txt :

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

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

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2          30,716,280   210,971,374   180,255,095   7 NTFS / exFAT / HPFS
/dev/sda3         210,972,670   976,768,064   765,795,395   f W95 Extended (LBA)
/dev/sda5         274,904,343   976,768,064   701,863,722  83 Linux
/dev/sda6         210,972,672   266,586,111    55,613,440  83 Linux
/dev/sda7         266,588,160   274,903,039     8,314,880  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        520C3A1D0C39FC93                       ntfs       
/dev/sda6        776fca9e-5319-48a8-b5ef-50869eb660c3   ext4       
/dev/sda7        1233dad7-2ff3-4b37-bf62-857a577de8e9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
set locale_dir=($root)/boot/grub/locale
set lang=nb_NO
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
if background_color 0,71,115; then
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=776fca9e-5319-48a8-b5ef-50869eb660c3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=776fca9e-5319-48a8-b5ef-50869eb660c3 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 776fca9e-5319-48a8-b5ef-50869eb660c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 520C3A1D0C39FC93
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
UUID=776fca9e-5319-48a8-b5ef-50869eb660c3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=1233dad7-2ff3-4b37-bf62-857a577de8e9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 116.812068939 = 125.426003968  boot/grub/core.img                             1
 105.377170563 = 113.147875328  boot/grub/grub.cfg                             1
 101.977619171 = 109.497634816  boot/initrd.img-2.6.38-8-generic               2
 116.810340881 = 125.424148480  boot/vmlinuz-2.6.38-8-generic                  1
 101.977619171 = 109.497634816  initrd.img                                     2
 116.810340881 = 125.424148480  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  75 96 44 31 60 14 6b 09  4e 14 4a e7 da be a3 b2  |u.D1`.k.N.J.....|
00000010  ac 95 16 47 e6 cb a4 d1  55 ff f9 ad f9 5b 09 42  |...G....U....[.B|
00000020  7d 8a 7c fc f0 67 f5 31  05 35 14 cc b8 e4 e0 80  |}.|..g.1.5......|
00000030  a1 89 95 d1 84 a4 00 00  00 00 00 00 00 00 00 00  |................|
00000040  ff fb 70 c0 00 03 90 99  51 3e 6c 24 73 82 3c 29  |..p.....Q>l$s.<)|
00000050  67 05 96 0e 7a 00 00 01  80 aa 15 48 03 a1 c5 64  |g...z......H...d|
00000060  22 26 a2 8f 10 c4 6f cd  8d 4b d7 02 92 65 31 59  |"&....o..K...e1Y|
00000070  86 65 20 75 98 14 0a f3  40 0b ae 04 95 b4 09 85  |.e u....@.......|
00000080  45 c4 83 eb cc 13 88 79  7c 25 46 47 a8 11 2e 85  |E......y|%FG....|
00000090  21 b2 a8 94 83 96 5c 2f  30 ba a8 0b 21 59 a6 5c  |!.....\/0...!Y.\|
000000a0  c9 83 a4 51 11 62 42 11  e0 68 e8 64 30 3a 38 47  |...Q.bB..h.d0:8G|
000000b0  47 d7 32 ca 75 85 85 cc  22 85 71 07 3f 33 28 ac  |G.2.u...".q.?3(.|
000000c0  8b b2 16 45 15 45 6f 2a  29 91 9c c8 3f 39 e2 13  |...E.Eo*)...?9..|
000000d0  18 df f0 47 5b f4 87 f8  43 a4 44 8a 98 cc 9a c0  |...G[...C.D.....|
000000e0  1c 85 83 40 3e 47 64 e2  2a 40 d3 33 d1 0b af ec  |...@>Gd.*@.3....|
000000f0  81 df 8b 46 5d 84 cc b3  00 29 ad 5b 6b 96 75 d8  |...F]....).[k.u.|
00000100  5a 46 04 8a ab 48 44 70  32 66 1f 9f 0f 2e 88 68  |ZF...HDp2f.....h|
00000110  06 26 21 c0 50 72 72 da  0f 45 0a c3 a5 c3 89 45  |.&!.Prr..E.....E|
00000120  82 00 f4 cc 51 30 d6 30  72 a5 62 53 d6 0f c7 c1  |....Q0.0r.bS....|
00000130  2c 7f 48 78 7c 7a da fd  51 03 a2 73 a8 d3 ba 54  |,.Hx|z..Q..s...T|
00000140  30 81 7a fe c6 7d 1d d9  ab ce 9d ec 2f 56 b1 e4  |0.z..}....../V..|
00000150  6c b4 c8 b5 65 bb 85 56  ad 99 ec 59 89 a7 0e 20  |l...e..V...Y... |
00000160  fd 6f fc 35 c2 f1 db 07  b5 31 05 35 14 cc b8 e4  |.o.5.....1.5....|
00000170  e0 80 a1 89 95 d1 84 a4  00 00 00 00 ff fb 72 c0  |..............r.|
00000180  00 03 d0 c4 f7 3a 2c 31  2e da 3c 28 66 c1 96 0e  |.....:,1..<(f...|
00000190  7a 00 8a 8f 33 5d 81 20  84 1a 73 95 1f f1 4b 8d  |z...3]. ..s...K.|
000001a0  52 64 2c 16 dd f8 6b 92  a8 ba b3 af 41 20 08 08  |Rd,...k.....A ..|
000001b0  55 78 e8 9c d1 d8 4d 7d  72 31 f0 5c ad c2 00 fe  |Ux....M}r1.\....|
000001c0  ff ff 83 fe ff ff 19 85  cf 03 2a 97 d5 29 00 fe  |..........*..)..|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 98 50 03 00 00  |............P...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 17 b5 62 10  |........?.....b.|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 00 b4 c6 00 00 00 00  00 30 59 cf 0b 00 00 00  |.........0Y.....|
000000c0  00 e0 fe c8 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200


=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".


```

---

### Post by coffeecat on 2011-06-20
> **iskald said:**
> I didn't actually know I had quoted you :o

You didn't; westie457 did. :)

> **westie457 said:**
> Hi 
Using the words of 'coffecat'. This looks like a job for testdisk.

Anyway, to your problem.

I'll post a few thoughts and then pm a couple of others and ask them to have a look as well. It's always useful in a situation such as this where a partition or important data have gone awol to have more than one viewpoint.

Your partition layout is as follows sizes in GB approximate):

sda1 - Hidden Recovery partition - 15.7 GB
sda2 - Windows C: partition - 92.3GB
sda3 - extended partition, which contains these logical partitions:
sda5 - 359GB - this is almost certainly all or most of your D: partition, but there are problems to deal with. See below.
sda6 - Your Kubuntu/Ubuntu partition. 28.5GB. Interestingly, it identifies itself as Ubuntu in the grub menu but you say you installed Kubuntu. Perhaps Kubuntu does - I haven't used the Kubuntu version much.
sda7 - swap partition - 4.3GB

The sda5 partition appears as Linux filesystem in the output of fdisk (which reflects what is in the partition table), but as "unknown filesystem" early in the boot script. It could be that the filesystem is damaged, or perhaps this just reflects a mismatch between the NTFS filesystem in the partition (which is what your D: would have been) and the partition table entry.

The questions I have - which are rhetorical at the moment - are: was your D: partition originally a primary partition or a logical one? And: was it originally 359GB in size, or did it cover the whole of the approx 392GB that the extended partition now covers?

Do you remember what size the D: partition was? What did you do with the partitions when you installed Kubuntu?

I think this indeed is a job for testdisk. Here is a link for you to look at:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Don't do anything just yet. I'll be pm-ing the others just as soon as I have posted.

---

### Post by Rubi1200 on 2011-06-20
Another decent guide for using Testdisk is here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

So, coffeecat asked me to comment and this is what I want to suggest.

Boot the computer with a LiveCD and choose to try not install. Then, install Testdisk and using either the guide coffeecat posted or the one I suggested (whichever is easier) use the program to search your partitions and see what it finds.

Do not, I repeat, do not attempt to write any changes yet! Simply run the search and report back here with the findings so we can decide on the best approach.

Additionally, as coffeecat also mentioned, do not use the Linux partitions for the moment until we determine that you are not overwriting valuable data.

As an extra precaution, I would use dd to make a copy of sda5 in its current state so you have something to go back to should things go wrong (which we hope won't be the case). You need something with enough space to hold the image:

```
sudo dd if=/dev/sda5 of=/dev/path to external drive or usb etc 
```

change the path according to your needs e.g. of=/dev/sdb

Make sure the path is correct before running the command.

coffeecat will correct me if the syntax is wrong :-)

---

### Post by iskald on 2011-06-22
> **coffeecat said:**
> You didn't; westie457 did. :)



Anyway, to your problem.

I'll post a few thoughts and then pm a couple of others and ask them to have a look as well. It's always useful in a situation such as this where a partition or important data have gone awol to have more than one viewpoint.

Your partition layout is as follows sizes in GB approximate):

sda1 - Hidden Recovery partition - 15.7 GB
sda2 - Windows C: partition - 92.3GB
sda3 - extended partition, which contains these logical partitions:
sda5 - 359GB - this is almost certainly all or most of your D: partition, but there are problems to deal with. See below.
sda6 - Your Kubuntu/Ubuntu partition. 28.5GB. Interestingly, it identifies itself as Ubuntu in the grub menu but you say you installed Kubuntu. Perhaps Kubuntu does - I haven't used the Kubuntu version much.
sda7 - swap partition - 4.3GB

The sda5 partition appears as Linux filesystem in the output of fdisk (which reflects what is in the partition table), but as "unknown filesystem" early in the boot script. It could be that the filesystem is damaged, or perhaps this just reflects a mismatch between the NTFS filesystem in the partition (which is what your D: would have been) and the partition table entry.

The questions I have - which are rhetorical at the moment - are: was your D: partition originally a primary partition or a logical one? And: was it originally 359GB in size, or did it cover the whole of the approx 392GB that the extended partition now covers?

Do you remember what size the D: partition was? What did you do with the partitions when you installed Kubuntu?

I think this indeed is a job for testdisk. Here is a link for you to look at:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Don't do anything just yet. I'll be pm-ing the others just as soon as I have posted.

The D: partition was a partition I only used for my businessfiles, movies, pictures, etc.

The size of the D: partition was in fact exactly 359GB in size before install.

I'll run testdisk on friday/saturday. I'm moving to another city tomorrow morning, so I'll get to it as fast as I can!

---

### Post by wieman01 on 2011-06-22
And just a quick word of advice (might seem out of place here)... please start thinking about a proper backup strategy for your data. I know it's a hassle, but losing precious data is even more so. :-)

---

