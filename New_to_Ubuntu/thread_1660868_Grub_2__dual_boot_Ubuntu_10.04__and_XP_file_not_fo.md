---
title: "Grub 2  dual boot Ubuntu 10.04  and XP file not found error for booting into Ubuntu"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by bigbsatti on 2011-01-05
Below  is my Grub menu at boot time
--------------------------------------
GNU GRUB version .198+20100804-5ubuntu3
--------------------------------------------------------------
Ubuntu with Linux version_find_latest$list
Ubuntu with Linux version_find_latest$list(recovery mode)
Memory test (memtest86+)
Memory test (memtest86+,serial console 115200)
Windows XP (on /dev/sda1 )
I am able to boot to windows but not Ubuntu 

I tried all the three ways to reinstall grub2 as given in the ubuntu help 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

No luck at all . Pleas suggest me a way

---

### Post by Rubi1200 on 2011-01-06
Hi and welcome to the forums :-)

You need to boot the computer with a LiveCD choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by amjjawad on 2011-01-06
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

You need to boot the computer with a LiveCD choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

+1



[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]


After you post the result, highlight all the text (the result of boot script) and click "#" from the top of the post box.

Good luck :)

---

### Post by bigbsatti on 2011-01-06
Thank you for the quick reply . Attached is the result.txt after running the shell script . Let me know if i need to post

---

### Post by Zepp Jamieson on 2011-01-06
I encountered the same sh:grub> problem, and after unsuccessfully trying to install Grub2 with the live CD, and trying to boot linuz from sda1, I finally found a solution that works.  
Go to this Source Forge site:
[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It has the following instructions:
Warning: The solution below is only for Wubi 9.10. It will make older versions unbootable.

Boot into Windows and click on the following link to download the file "wubildr":

wubildr

Don't try to open the file. Move the file to "C:\" to replace the faulty "C:\wubildr". (to get to "C:\" go to "My Computer" or "Computer" and double click the "C:drive")

If Wubi is not on the C:drive, you might need to place wubildr into the partition containing Wubi. So if Wubi is not on the C:\drive, repeat the above instructions, using the drive letter of the partition containing Wubi in place of "C:". 

They also have instructions on how to update your Grub to Grub2 in case you haven't already run into this problem (you will) and directions for 9.04.

It worked perfectly for me.

---

### Post by amjjawad on 2011-01-07
> **bigbsatti said:**
> Thank you for the quick reply . Attached is the result.txt after running the shell script . Let me know if i need to post

               ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for (,msdos9)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #45651968 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /NST/menu.lst /boot.ini /bootmgr /Boot/BCD /ntldr 
                       /NTDETECT.COM

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    21,205,799    21,205,737   7 HPFS/NTFS
/dev/sda2          21,205,861    78,140,159    56,934,299   f W95 Ext d (LBA)
/dev/sda5          21,205,863    30,897,518     9,691,656   7 HPFS/NTFS
/dev/sda6          75,200,328    78,140,159     2,939,832  82 Linux swap / Solaris
/dev/sda7          45,651,968    73,863,167    28,211,200  83 Linux
/dev/sda8          73,865,216    75,198,463     1,333,248  82 Linux swap / Solaris
/dev/sda9          30,898,176    44,902,399    14,004,224  83 Linux
/dev/sda10         44,904,448    45,639,679       735,232  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        01CB72AE3829F1A0                       ntfs                                     
/dev/sda10       e41f9bc9-f109-4bf1-9ace-d423ef311d9a   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        01CB72AE4A50B3F0                       ntfs                                     
/dev/sda6        ad20be81-80d0-46f6-a9e8-8c28f8625ed0   swap                                     
/dev/sda7        1ae41a88-8b71-4489-8593-1fe96ad64af6   ext4                                     
/dev/sda8        e3ebb3f5-9f5a-4a0e-a43d-c442dde6477e   swap                                     
/dev/sda9        d6cd035b-36f2-463e-a8a7-e11acb13750d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B7D3-1BF1                              vfat       Lexar                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!
================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=1ae41a88-8b71-4489-8593-1fe96ad64af6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e3ebb3f5-9f5a-4a0e-a43d-c442dde6477e none            swap    sw              0       0

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
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
menuentry 'Ubuntu, with Linux version_find_latest$list' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
	linux	/version_find_latest$list root=/dev/sda9 ro   quiet splash
}
menuentry 'Ubuntu, with Linux version_find_latest$list (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
	echo	'Loading Linux version_find_latest$list ...'
	linux	/version_find_latest$list root=/dev/sda9 ro single 
	echo	'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set d6cd035b-36f2-463e-a8a7-e11acb13750d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 01cb72ae3829f1a0
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

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=d6cd035b-36f2-463e-a8a7-e11acb13750d  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=e41f9bc9-f109-4bf1-9ace-d423ef311d9a  none         swap  sw                   0  0  
/dev/sda7                                  /media/sda7  ext4  defaults             0  0  

=================== sda9: Location of files loaded by Grub: ===================


  20.5GB: boot/grub/core.img
  20.9GB: boot/grub/grub.cfg
  22.5GB: boot/initrd.img-2.6.32-21-generic
  22.8GB: boot/initrd.img-2.6.35-23-generic
  22.9GB: boot/initrd.img-2.6.35-24-generic
  16.4GB: boot/vmlinuz-2.6.32-21-generic
  22.5GB: boot/vmlinuz-2.6.35-23-generic
  22.8GB: boot/vmlinuz-2.6.35-24-generic
  22.9GB: initrd.img
  22.8GB: initrd.img.old
  22.8GB: vmlinuz
  22.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  0e 40 27 b6 4f bf a5 43  0b c1 05 cf 9c 1a 7f de  |.@'.O..C........|
00000010  1f df 47 e7 13 e7 8c 60  0c b7 40 09 cf 15 94 68  |..G....`..@....h|
00000020  c6 11 e6 5f 0b 3d 0c 05  57 4a 7c df 88 41 7f 22  |..._.=..WJ|..A."|
00000030  5d 7e e2 57 c4 13 1d e5  d4 a7 90 47 d7 ae 3d 7b  |]~.W.......G..={|
00000040  8a bd 7e f6 4c 0d c2 de  fd a7 ce 97 33 2d b4 7b  |..~.L.......3-.{|
00000050  31 2e 33 b5 bb a8 e8 70  38 3f 8d 74 fb 7a 72 f7  |1.3....p8?.t.zr.|
00000060  63 ac 82 95 46 e6 f9 fe  45 68 ef 9a 4b 68 91 1f  |c...F...Eh..Kh..|
00000070  72 85 c6 e9 63 0a 59 b3  ce 0f 61 fc ea c5 b4 90  |r...c.Y...a.....|
00000080  43 f6 83 23 c7 19 50 30  24 7c 99 bd 87 ae 33 5c  |C..#..P0$|....3\|
00000090  95 f0 f1 a1 2e 77 ba 3a  68 fb b7 a9 2e a2 dc ce  |.....w.:h.......|
000000a0  a3 e6 0b 9b 57 fd d4 fe  71 18 cb 74 c6 3d f8 c1  |....W...q..t.=..|
000000b0  eb 54 65 f2 6c a2 92 58  7c f1 23 42 5a 66 01 99  |.Te.l..X|.#BZf..|
000000c0  54 2f 55 11 8e e4 74 c5  42 c4 aa 71 e7 b5 ce 85  |T/U...t.B..q....|
000000d0  5d 46 29 a4 0a 22 31 6c  11 84 0e 80 a2 e7 97 18  |]F).."1l........|
000000e0  19 c8 3c 9e bd 7f 9d 4c  64 16 e9 1e 03 a8 95 bc  |..<....Ld.......|
000000f0  a6 74 21 bc a1 82 7a 76  a7 ed d5 b4 dc ce 58 c4  |.t!...zv......X.|
00000100  ae 97 c9 15 a3 d4 23 62  44 84 47 2c 92 8b 78 10  |......#bD.G,..x.|
00000110  c8 49 9f 82 4b f1 c2 8c  7a 91 d4 75 a6 ad d3 6d  |.I..K...z..u...m|
00000120  91 6d fc e6 86 39 36 c8  86 20 ab 14 9f c4 08 3d  |.m...96.. .....=|
00000130  73 ed d6 b2 96 26 10 5c  eb a9 c6 f1 6e a4 1a 9a  |s....&.\....n...|
00000140  29 4d 7e f7 32 b4 0b e5  2b ad c9 74 5d c1 43 96  |)M~.2...+..t].C.|
00000150  1d 40 e8 8a 3f 0a ae 2f  52 68 d8 5b 2a f9 b1 c9  |.@..?../Rh.[*...|
00000160  e5 38 c6 02 38 f5 27 d7  d6 bb 28 af 75 6b ab 2a  |.8..8.'...(.uk.*|
00000170  86 2b da 46 cf 6b 14 2e  45 b9 6f 3e 48 c5 c5 ec  |.+.F.k..E.o>H...|
00000180  8e 65 5b a8 f3 9b 29 33  d5 40 e0 1f c0 8e b5 99  |.e[...)3.@......|
00000190  2c a4 2c a1 19 9d e2 21  99 8b 03 b8 13 d4 ff 00  |,.,....!........|
000001a0  3a e6 95 55 19 f2 ee 7c  2e 69 07 4e 57 96 cb f1  |:..U...|.i.NW...|
000001b0  31 be db bf 0e 4a 4c 16  57 41 34 2b f2 ba 00 fe  |1....JL.WA4+....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 08 e2 93 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff a4 e3  37 03 f7 db 2c 00 00 00  |........7...,...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


Edit:

You have 3 swap partitions and you have Ubuntu 10.04 and Ubuntu 10.10 so which one exactly you have installed and want to keep?
We need to know which OS you want to keep and Dual Boot with XP.

---

### Post by wilee-nilee on 2011-01-07
> **Zepp Jamieson said:**
> I encountered the same sh:grub> problem, and after unsuccessfully trying to install Grub2 with the live CD, and trying to boot linuz from sda1, I finally found a solution that works.  
Go to this Source Forge site:
[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It has the following instructions:
Warning: The solution below is only for Wubi 9.10. It will make older versions unbootable.

Boot into Windows and click on the following link to download the file "wubildr":

wubildr

Don't try to open the file. Move the file to "C:\" to replace the faulty "C:\wubildr". (to get to "C:\" go to "My Computer" or "Computer" and double click the "C:drive")

If Wubi is not on the C:drive, you might need to place wubildr into the partition containing Wubi. So if Wubi is not on the C:\drive, repeat the above instructions, using the drive letter of the partition containing Wubi in place of "C:". 

They also have instructions on how to update your Grub to Grub2 in case you haven't already run into this problem (you will) and directions for 9.04.

It worked perfectly for me.

There is no Wubi on this computer.

---

### Post by wilee-nilee on 2011-01-07
So OP on a 40 gig drive you have 3 swaps to begin with and multiple partitions you probably don't need.

You have the neosmart bootloader installed.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info**:     BootPart in the file /NST/nst_grub.mbr is trying to **
                       chain load sector #45651968 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:  ** /NST/menu.lst** /boot.ini **/bootmgr /Boot/BCD** /ntldr 
                       /NTDETECT.COM

You have a setup that is precarious at best. Could you give a better explanation of what is going on. What is the boot menu is it grub2 you see?

And what can you boot?

This part highlighted /bootmgr /Boot/BCD looks like the boot for a vista once in sda5 is this correct as far as a Vista install or formerly there.

This in the sda5 is a little strange.
According to the info in the boot sector, sda5 starts 
                       at sector 63.

---

### Post by amjjawad on 2011-01-07
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

[COLOR="Red"]/dev/sda1[/COLOR]    *             [COLOR="Red"]63[/COLOR]    21,205,799    21,205,737   7 HPFS/NTFS
/dev/sda2          21,205,861    78,140,159    56,934,299   f W95 Ext d (LBA)
/dev/sda5          21,205,863    30,897,518     9,691,656   7 HPFS/NTFS
/dev/sda6          75,200,328    78,140,159     2,939,832  82 Linux swap / Solaris
/dev/sda7          45,651,968    73,863,167    28,211,200  83 Linux
/dev/sda8          73,865,216    75,198,463     1,333,248  82 Linux swap / Solaris
/dev/sda9          30,898,176    44,902,399    14,004,224  83 Linux
/dev/sda10         44,904,448    45,639,679       735,232  82 Linux swap / Solaris
```

Looks like sda1 was shrinked before installation of Ubutnu. Sda5 is Logical so no way Windows could be installed there.

This is a very messed up partition scheme so hope the OP will explain more :)

---

### Post by bigbsatti on 2011-01-07
Thanks for the reply , I want to keep 10.04 LTS .Suggest me the instructions .

---

### Post by wilee-nilee on 2011-01-07
> **bigbsatti said:**
> Thanks for the reply , I want to keep 10.04 LTS .Suggest me the instructions .

So we have found some inconsistencies with your set up, but to be honest you haven't really explained exactly what is going on. And the history of the additional bootloaders and the Vista boot I highlighted, and asked about, so I give you this a a reference on a better outline for help.
[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by amjjawad on 2011-01-08
What wilee-nilee is trying to explain is without the "extra information and/or explanation" from your side, we can't help you and we can't offer the better advice/suggestion that you're looking for.

With the very few information you're providing, we'll advice you blindly and if you ask me, I would say do this and that but that might not be the right advice.

**Try to explain in details and in steps (1, 2, 3, etc) **what exactly you have, what steps you followed and how did you try to fix that, etc. Everything might help.

Thank you!

---

### Post by bigbsatti on 2011-01-09
I should have given the complete details of what installations went on the machine, its my fault asking people to help with out giving the proper details . 

Below are the sequence of installations i have done on this machine 

1) I have Windows XP installed initially , then used partition magic tool for partition.
2) On the partition i installed Ubuntu 10.04 LTS with a live CD .
3) And after some time i installed Ubuntu 10.10  
Everything was working file i was able to boot to all the three installations.
4) When i was using the 10.04 LTS system froze when updates were installing.When i tried to restart the system i had problems with GRUB.
5) so i followed all the three steps for restoring grub given in the help documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
6) After trying all three options for restoring GRUB,one of my friend suggested me EASY BCD for multiple boot . Its a windows program, but after installing i realized that it uses Neo Grub.While toying with EASY BCD i messed up the windows XP installation,So I used Windows Vista installation CD that is the reason at boot time it shows windows vista boot .
Is there any way for me to boot in to any one of the Ubuntu installation along with windows XP?.
Let me know if you guys need any further information.

---

### Post by amjjawad on 2011-01-10
It's such a complicated scenario. I'm afraid you did not follow the right procedure to fix the problem and that led to another problems.

Never mind, hope we could help :)


> **bigbsatti said:**
> 

1) I have Windows XP installed initially , then used partition magic tool for partition.

2) On the partition i installed Ubuntu 10.04 LTS with a live CD .

3) And after some time i installed Ubuntu 10.10  
Everything was working file i was able to boot to all the three installations.

4) When i was using the 10.04 LTS system froze when updates were installing.When i tried to restart the system i had problems with GRUB.

5) so i followed all the three steps for restoring grub given in the help documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

6) After trying all three options for restoring GRUB,one of my friend suggested me EASY BCD for multiple boot . Its a windows program, but after installing i realized that it uses Neo Grub.While toying with EASY BCD i messed up the windows XP installation,So I used Windows Vista installation CD that is the reason at boot time it shows windows vista boot .
Is there any way for me to boot in to any one of the Ubuntu installation along with windows XP?.
Let me know if you guys need any further information.


IMHO, these are the steps you need to follow:

1) Boot your machine with Ubuntu LiveCD

2) From the Live Desktop, please run GParted.
System > Administration > GParted

3) Delete these partitions:
sda8
sda9
sda10

4) Reboot/Restart your machine

5) Fix Windows Boot Loader using XP Disc or a repair disc
Make sure your machine will boot and login to XP.

6) Now, you need to re-install GRUB2 as per these instruction:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

7) I suggest before you re-install GRUB2 to run**_[ the boot script]("http://bootinfoscript.sourceforge.net/")_** again and post the result here. 


The only thing I have no experience with is the other boot loaders. I hope the above steps will fix the issue. Otherwise, perhaps someone else may correct me if I'm wrong.

Good luck :)

---

### Post by bigbsatti on 2011-01-19
I have reinstalled the Ubuntu 10.04 LTS on my machine, Every thing was working fine until the updates to the kernel bu update manager .
boot time display
 Ubuntu, with Linux 2.6.32.27-generic
 Ubuntu, with Linux 2.6.32.27-generic(recovery mode)
 Ubuntu, with Linux 2.6.32.21-generic
 Ubuntu, with Linux 2.6.32.21-generic(recovery mode)
 Memory test (memtest86+)
 Memory test (memtest86+,serial console 115200)
 Windows Vista(loader) (on /dev/sda1)

when i boot to Ubuntu  I get the following error
 
init:ureadahead main process(273) terminated with status 5
The steps i followed are
1)Used Ubuntu 10.04 LTS live cd to boot 
2) Ran the script for boot info given in the previous post .
Attached are the  results from the script.

Suggest me steps to fix this issue.

---

### Post by bigbsatti on 2011-01-19
I have reinstalled the Ubuntu 10.04 LTS on my machine, Every thing was working fine until the updates to the kernel bu update manager .
boot time display
 Ubuntu, with Linux 2.6.32.27-generic
 Ubuntu, with Linux 2.6.32.27-generic(recovery mode)
 Ubuntu, with Linux 2.6.32.21-generic
 Ubuntu, with Linux 2.6.32.21-generic(recovery mode)
 Memory test (memtest86+)
 Memory test (memtest86+,serial console 115200)
 Windows Vista(loader) (on /dev/sda1)

when i boot to Ubuntu  I get the following error
 
init:ureadahead main process(273) terminated with status 5
The steps i followed are
1)Used Ubuntu 10.04 LTS live cd to boot 
2) Ran the script for boot info given in the previous post .
Attached are the  results from the script.

Suggest me steps to fix this issue.

---

### Post by oldfred on 2011-01-19
Can you boot with the older (.21) kernel? 

This says it happens with those who installed with a separate /var partition and deleting it works, but you do not have a separate /var.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334)

Someone posted that this worked.

aptitude reinstall ureadahead

---

### Post by bigbsatti on 2011-01-19
I did not try to boot with older kernel, will do once i am out of office . I read the post about ureadahead issue . I did aptitude reinstall ureadahead with ubuntu 10.04 LTS live CD but i still get init:ureadahead main process(273) terminated with status 5 eror when i try to boot.

---

### Post by bigbsatti on 2011-01-19
i tried to log in with old kernel but i am still getting the error 
ureadahead main process(273) terminated with status 5 erorr

---

### Post by oldfred on 2011-01-20
Just running the commands from a liveCD will not update your system, but just the liveCD unless you chroot into your system.

Several versions of chrooting to run commands.
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

---

### Post by bulbus on 2011-01-24
Hi, I'm having the same issue...

1. Win7 got messed up so was trying to re-install with XP from a CD. 
Decided not to go ahead(cancelled midway).
2. MBR got overwritten
3. Booted up with 9.1 CD and reinstalled Grub2(although on hdd it is upgraded to Lucid)
4. Now grub starts and then gets stuck @
```

 grub>

```Following are some quick stats on partition and output from os-prober.
```
ubuntu@ubuntu:/mnt/boot/grub$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130e8a61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       25497   204696576    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25498      121601   771955380    5  Extended
/dev/sda4          120570      121601     8289540   82  Linux swap / Solaris
/dev/sda5           25498       26712     9759424+  83  Linux
/dev/sda6           26713       58322   253907293+  83  Linux
/dev/sda7           58323      120568   499990932    b  W95 FAT32
ubuntu@ubuntu:/mnt/boot/grub$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 10.04.1 LTS (10.04):Ubuntu:linux

```Also I've attached the output from bootInfoScript. Please help!

---

### Post by oldfred on 2011-01-25
bulbus, You really should start your own thread, boot problems are always unique. While you often can use the same commands to repair, each has to be adjusted to a users specific system. 

Your grub is pointing to sda1 but your install is on sda5. You also moved partitions around as the install partition is not the same as the current partitions, but your UUIDs look to be the same. You need to reinstall grub from sda5.

You also overwrote the windows boot files from the hidden windows boot sector in sda1. You need a  windows repair CD, move boot flag to sda2 and repair the windows install in sda2.

---

