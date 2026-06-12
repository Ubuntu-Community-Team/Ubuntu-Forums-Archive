---
title: "Windows loader just restarts"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by Maaku on 2011-05-25
I am having problems with getting into Windows from the GRUB loader. It does list Vista, but when I select to boot it, the computer just restarts and loads up the GRUB loader again where I have a choice of Ubuntu, previous Ubuntu versions, or Windows Loader.

I have partitioned my computer correctly, and I installed Windows first before Ubuntu. So, the primary partition is Windows.

Here is the output from blkid:
```

/dev/sda2: LABEL="ACER" UUID="1AA02B3DA02B1F2F" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="52EE2190EE216D83" TYPE="ntfs" 
/dev/sda5: UUID="cbc188a4-2fbc-45d4-8776-a4b2276b3455" TYPE="swap" 
/dev/sda6: UUID="502617eb-0a26-44a1-9fd1-f096a8c0e228" TYPE="ext2"

```

I have been able to boot into Windows prior to the new distro release, so I am wondering if the new distro is the cause of the problem.

How would I be able to have Windows Loader boot first before GRUB, if that is possible?

Thanks for your help.

Release 11.04 (natty)
Kernel Linux 2.6.38-8-generic

---

### Post by Quackers on 2011-05-25
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Maaku on 2011-05-25
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *          2,048    54,218,751    54,216,704   6 FAT16
/dev/sda3          54,218,752    97,835,007    43,616,256   7 NTFS / exFAT / HPFS
/dev/sda4          97,835,008   156,301,311    58,466,304   5 Extended
/dev/sda5         154,032,128   156,301,311     2,269,184  82 Linux swap / Solaris
/dev/sda6          97,837,056   154,030,079    56,193,024  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        1AA02B3DA02B1F2F                       ntfs       ACER
/dev/sda3        52EE2190EE216D83                       ntfs       DATA
/dev/sda5        cbc188a4-2fbc-45d4-8776-a4b2276b3455   swap       
/dev/sda6        502617eb-0a26-44a1-9fd1-f096a8c0e228   ext2       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /                        ext2       (rw,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
title Windows Vista
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=502617eb-0a26-44a1-9fd1-f096a8c0e228 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=502617eb-0a26-44a1-9fd1-f096a8c0e228 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=502617eb-0a26-44a1-9fd1-f096a8c0e228 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=502617eb-0a26-44a1-9fd1-f096a8c0e228 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 502617eb-0a26-44a1-9fd1-f096a8c0e228
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 1AA02B3DA02B1F2F
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
UUID=502617eb-0a26-44a1-9fd1-f096a8c0e228 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cbc188a4-2fbc-45d4-8776-a4b2276b3455 none            swap    sw              0       0
# DATA DRIVE
UUID=52EE2190EE216D83 /media/DATA/ ntfs none 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  47.089988708 = 50.562490368   boot/grub/core.img                             1
  47.139247894 = 50.615382016   boot/grub/grub.cfg                             1
  47.043079376 = 50.512121856   boot/grub/menu.lst                             1
  46.965362549 = 50.428674048   boot/initrd.img-2.6.35-28-generic              5
  46.945514679 = 50.407362560   boot/initrd.img-2.6.38-8-generic               5
  47.007919312 = 50.474369024   boot/vmlinuz-2.6.35-28-generic                 3
  47.002498627 = 50.468548608   boot/vmlinuz-2.6.38-8-generic                  3
  46.945514679 = 50.407362560   initrd.img                                     5
  46.965362549 = 50.428674048   initrd.img.old                                 5
  47.002498627 = 50.468548608   vmlinuz                                        3
  47.007919312 = 50.474369024   vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  4e 8e f0 d4 9c a5 8e 45  72 d2 1d b2 16 90 5f 4f  |N......Er....._O|
00000010  20 8e cb 93 f2 72 69 a8  51 50 57 27 42 bc 45 d1  | ....ri.QPW'B.E.|
00000020  65 f5 ea 09 a9 51 14 44  26 08 0d e8 54 40 24 05  |e....Q.D&...T@$.|
00000030  82 28 15 25 07 53 13 87  84 a2 40 65 a1 c1 12 a6  |.(.%.S....@e....|
00000040  09 17 15 3c 81 88 40 2a  ff 23 ab 26 58 c2 27 9b  |...<..@*.#.&X.'.|
00000050  23 72 ad 4d 70 3d 6b 5e  2b 2e bb 58 86 4e b9 b2  |#r.Mp=k^+..X.N..|
00000060  9e 2f fe e4 d3 d6 d7 ce  ed 3d 57 68 a8 71 55 75  |./.......=Wh.qUu|
00000070  5a 26 04 8e 11 d4 af de  06 6a a3 85 f1 a4 5d ca  |Z&.......j....].|
00000080  e1 71 82 14 40 a5 58 be  4e 97 09 8c 5f 94 0b 59  |.q..@.X.N..._..Y|
00000090  92 c6 5d 58 e3 a6 96 50  b8 66 12 48 cd 46 22 95  |..]X...P.f.H.F".|
000000a0  60 e0 14 a6 d0 db 38 0e  92 f7 04 84 27 f6 8d 74  |`.....8.....'..t|
000000b0  d7 42 75 76 e2 ec 27 24  b5 57 54 42 ee 44 53 0b  |.Buv..'$.WTB.DS.|
000000c0  89 be 63 b8 9d d0 5f 2b  cf 91 f1 51 27 14 0f c9  |..c..._+...Q'...|
000000d0  22 ec 9d a7 11 84 19 2a  c6 96 80 a5 44 cc 94 42  |"......*....D..B|
000000e0  93 8a 85 d5 94 d8 5a 13  d8 b0 1c 91 26 51 74 3b  |......Z.....&Qt;|
000000f0  36 70 96 f9 95 47 22 4a  60 b0 d9 38 b7 4a a6 10  |6p...G"J`..8.J..|
00000100  a8 64 ec b4 eb 8f 36 90  f1 7d 57 b2 cb ea 4f aa  |.d....6..}W...O.|
00000110  be 58 47 39 1a 88 62 3c  41 7a ec 30 2a 21 b7 f6  |.XG9..b<Az.0*!..|
00000120  8d f7 27 2d 0d 7e 2c be  3f 5b 5b f7 e0 0e 07 13  |..'-.~,.?[[.....|
00000130  16 36 17 18 50 e9 d2 4f  3a 63 73 bb f8 39 75 00  |.6..P..O:cs..9u.|
00000140  4d 15 28 34 68 50 88 0a  15 03 18 88 4c 60 90 99  |M.(4hP......L`..|
00000150  83 87 42 c4 63 01 10 00  ca 33 05 81 c0 49 ac cc  |..B.c....3...I..|
00000160  9a 36 66 a0 11 39 74 d5  94 ac 12 0a 03 21 1a 63  |.6f..9t......!.c|
00000170  27 75 29 7a e5 ff fb e0  64 1b 0f a7 2a 65 d3 8b  |'u)z....d...*e..|
00000180  8f 4e a2 d2 4b 5a 75 69  ec d4 5c 49 8b 4e 0e 3d  |.N..KZui..\I.N.=|
00000190  37 4a f2 2f 6a 45 a7 a6  e8 8c 91 e8 19 04 25 92  |7J./jE........%.|
000001a0  b3 44 9a 42 da 96 30 a4  fa 66 cd 3e 14 e3 ba 0c  |.D.B..0..f.>....|
000001b0  ad d7 78 9d 88 76 48 2c  1b 94 41 70 f3 46 00 fe  |..x..vH,..Ap.F..|
000001c0  ff ff 82 fe ff ff 00 80  59 03 00 a0 22 00 00 fe  |........Y..."...|
000001d0  ff ff 05 fe ff ff 4a 03  00 00 b6 74 59 03 00 00  |......J....tY...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-05-25
Did you previously have another grub menu entry referring to a Windows Recovery Environment Loader?
There appear to be inconsistencies in your data.
sda2 appears to be your Windows partition, however, in the output from Drive/Partition info sda2 is a FAT16 partition.

On a different note, you have a  /boot/grub/menu.lst in with your grub boot files in sda6, and the file system is ext2. This is not normal when grub2 is installed. /boot/grub/menu.lst is a grub legacy file (the original grub). Has this system been upgraded from an older version of Ubuntu?

---

### Post by Maaku on 2011-05-25
> **Quackers said:**
> Did you previously have another grub menu entry referring to a Windows Recovery Environment Loader?
There appear to be inconsistencies in your data.
sda2 appears to be your Windows partition, however, in the output from Drive/Partition info sda2 is a FAT16 partition.

On a different note, you have a  /boot/grub/menu.lst in with your grub boot files in sda6, and the file system is ext2. This is not normal when grub2 is installed. /boot/grub/menu.lst is a grub legacy file (the original grub). Has this system been upgraded from an older version of Ubuntu?

Yes, it has. I upgraded to Natty from 10.10. I have checked my menu.lst file, it seems fine. I did notice in GParted that the partition is NTFS, but in other areas it says it is FAT16.

---

### Post by Quackers on 2011-05-25
10.10 would normally be running grub2 as well - ie no grub/menu.lst - unless that was upgraded from 9.04 (I think).
There is something wrong with the Windows partitions I suspect. 
Firstly there is no sda1. This would often be a recovery partition - possibly of type FAT16
Secondly sda2, which is your Windows 7 partition should be a NTFS partition but that appears to be FAT16.
Sometimes when grub is directed to boot a FAT16 partition it will baulk and return to grub.
I'm at a loss to explain what is going on - and consequently to suggest a remedy.

---

### Post by oldfred on 2011-05-25
Since in one place it says it is NTFS and the other FAT, I think it may just be a partition entry error. I might try just changing sda2 to 07 (NTFS) with disk utility if it will let you. Then you may still need to run chkdsk or other windows repairs on the windows partition.

System, Administration, Disk Utility click on sda2, make sure it is unmounted and edit partition type to 07.

If that does not work back up partition table ( or better yet do this first). And copy to an external device.
sudo sfdisk -d /dev/sdc > parts.txt

If you cannot change it then I would try testdisk.
Part of testdisk which is in the repositories or most recovery CDs. 
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Maaku on 2011-05-25
> **Quackers said:**
> 10.10 would normally be running grub2 as well - ie no grub/menu.lst - unless that was upgraded from 9.04 (I think).
There is something wrong with the Windows partitions I suspect. 
Firstly there is no sda1. This would often be a recovery partition - possibly of type FAT16
Secondly sda2, which is your Windows 7 partition should be a NTFS partition but that appears to be FAT16.
Sometimes when grub is directed to boot a FAT16 partition it will baulk and return to grub.
I'm at a loss to explain what is going on - and consequently to suggest a remedy.

Well, I moved to Ubuntu, and at that time it was Lucid Lynx. So, I did update from 9.04 to 10.10, and then finally 11.04.

@oldfred:
I will try what you suggested. Thank you for your response.

---

### Post by Maaku on 2011-05-25
This is very interesting.

Because the image is too large, click on the direct link [here](http://i.imgur.com/Yh1Z7.png)

---

### Post by Maaku on 2011-05-25
> **oldfred said:**
> Since in one place it says it is NTFS and the other FAT, I think it may just be a partition entry error. I might try just changing sda2 to 07 (NTFS) with disk utility if it will let you. Then you may still need to run chkdsk or other windows repairs on the windows partition.

System, Administration, Disk Utility click on sda2, make sure it is unmounted and edit partition type to 07.

If that does not work back up partition table ( or better yet do this first). And copy to an external device.
sudo sfdisk -d /dev/sdc > parts.txt

If you cannot change it then I would try testdisk.
Part of testdisk which is in the repositories or most recovery CDs. 
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

I am currently doing this operation now. Does it matter if it is unmounted?

---

### Post by Quackers on 2011-05-25
It would need to be unmounted, I believe.

---

### Post by Maaku on 2011-05-25
> **Quackers said:**
> It would need to be unmounted, I believe.

For some reason it failed with the error 'Unknown error'. So, I am going to try doing this on my Live CD. It shouldn't matter if it is the 10.10 version, should it?

Thanks for your help.

---

### Post by Quackers on 2011-05-25
Ideally the same live cd as the system being used is best.

---

### Post by Maaku on 2011-05-25
> **Quackers said:**
> Ideally the same live cd as the system being used is best.

I would think so too, but I will try that first. Then, download the Live CD for 11.04. I will get back to you once I have done it.

---

### Post by Maaku on 2011-05-25
I booted into Live CD, and tried it in there. No error, but it seems to take a long time so I just cancelled it. My computer was very hot and it seemed it was going to overheat.

How long should this take or is it just not working?

---

### Post by oldfred on 2011-05-25
It should be quick.

if you output this what does it show.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Post PT.txt

My NTFS XP partition sda1 shows 7:

```
fred@fred-MavericDT:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=115330572, Id= 7, bootable
/dev/sda2 : start=156296385, size=156280320, Id=83
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=115330635, size= 40965750, Id= b
fred@fred-MavericDT:~$ 

```

---

### Post by Maaku on 2011-05-25
The output is:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=     2048, size= 54216704, Id= 6, bootable
/dev/sda3 : start= 54218752, size= 43616256, Id= 7
/dev/sda4 : start= 97835008, size= 58466304, Id= 5
/dev/sda5 : start=154032128, size=  2269184, Id=82
/dev/sda6 : start= 97837056, size= 56193024, Id=83

```

For me, sda2 is Windows Vista, and it is still 6 not 7. There may be something wrong as you said it is quick. Not sure though.

---

### Post by oldfred on 2011-05-25
Change the 6 to a 7 in your PT.txt and run this: note that the arrow is the other way.

sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

 ** 	 Using sfdisk to fix partition table problems  **
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by Maaku on 2011-05-25
> **oldfred said:**
> Change the 6 to a 7 in your PT.txt and run this: note that the arrow is the other way.

sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

 ** 	 Using sfdisk to fix partition table problems  **
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

What about the other 7? Change that to a 6?

---

### Post by Maaku on 2011-05-25
```

mark@Marks-Laptop:~$ sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2   *      0+   3374-   3375-  27108352    6  FAT16
/dev/sda3       3374+   6089-   2715-  21808128    7  HPFS/NTFS
/dev/sda4       6089+   9729-   3640-  29233152    5  Extended
/dev/sda5       9588+   9729-    142-   1134592   82  Linux swap / Solaris
/dev/sda6       6090+   9587-   3498-  28096512   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2   *      2048  54218751   54216704   7  HPFS/NTFS
/dev/sda3      54218752  97835007   43616256   6  FAT16
/dev/sda4      97835008 156301311   58466304   5  Extended
/dev/sda5     154032128 156301311    2269184  82  Linux swap / Solaris
/dev/sda6      97837056 154030079   56193024  83  Linux
Warning: partition 2 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

---

### Post by oldfred on 2011-05-25
A 7 means it is a NTFS partition which matches what the other info says both sda2 & sda3 is. So you need 7 in both. Do not change anything to 6.

---

### Post by Maaku on 2011-05-25
> **oldfred said:**
> A 7 means it is a NTFS partition which matches what the other info says both sda2 & sda3 is. So you need 7 in both. Do not change anything to 6.

Okay, I will undo that change and try again. Being a person who works with databases a lot, I got thrown off by having same IDs.

---

### Post by Maaku on 2011-05-25
Here is the output:

```

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2   *      0+   3374-   3375-  27108352    7  HPFS/NTFS
/dev/sda3       3374+   6089-   2715-  21808128    6  FAT16
/dev/sda4       6089+   9729-   3640-  29233152    5  Extended
/dev/sda5       9588+   9729-    142-   1134592   82  Linux swap / Solaris
/dev/sda6       6090+   9587-   3498-  28096512   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2   *      2048  54218751   54216704   7  HPFS/NTFS
/dev/sda3      54218752  97835007   43616256   7  HPFS/NTFS
/dev/sda4      97835008 156301311   58466304   5  Extended
/dev/sda5     154032128 156301311    2269184  82  Linux swap / Solaris
/dev/sda6      97837056 154030079   56193024  83  Linux
Warning: partition 2 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

Last time I tried booting into Vista, and I still had no success unless I need to do something else.

---

### Post by oldfred on 2011-05-26
Now partition table sees both as NTFS, so that should be consistent. Pehaps in changing to FAT something inside the Vista boot partition got messed up. Windows boot partitions have to have an exact construct for FAT, NTFS with XP or NTFS with Vista or 7. If they get mixed up or format/partition start/ends change, you have to run fixboot. It may just need a chkdsk.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by Maaku on 2011-05-26
> **oldfred said:**
> Now partition table sees both as NTFS, so that should be consistent. Pehaps in changing to FAT something inside the Vista boot partition got messed up. Windows boot partitions have to have an exact construct for FAT, NTFS with XP or NTFS with Vista or 7. If they get mixed up or format/partition start/ends change, you have to run fixboot. It may just need a chkdsk.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

Thanks oldfred. I will have a go at this later, about to go to college.

---

### Post by Maaku on 2011-05-26
> **oldfred said:**
> Now partition table sees both as NTFS, so that should be consistent. Pehaps in changing to FAT something inside the Vista boot partition got messed up. Windows boot partitions have to have an exact construct for FAT, NTFS with XP or NTFS with Vista or 7. If they get mixed up or format/partition start/ends change, you have to run fixboot. It may just need a chkdsk.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

Where do I run these commands? They seem to not be known in the Terminal.

---

### Post by oldfred on 2011-05-26
The windows repairs all have to be run from a windows repair CD. See post #9 in repair link above if you do not have one.

---

### Post by Maaku on 2011-05-26
> **oldfred said:**
> The windows repairs all have to be run from a windows repair CD. See post #9 in repair link above if you do not have one.

Okay. So, Command Prompt in recovery? If so, I have a disc.

---

