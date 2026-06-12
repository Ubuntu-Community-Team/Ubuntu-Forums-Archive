---
title: "Bootloader - Not showing up"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by lilsavalex on 2010-05-21
Well, I recently install Linux - Ubuntu and when turn on my computer theres no bootloader screen to let me choose which OS i want to go into. I know that Grub-2 was installed during my installation of Ubuntu. Are there any files that i need to edit for grub-2? I know i could use the Live-CD and go into Ubuntu to "try" it, then go to the command line and try and fix it from there. Or just simply go to the files and edit it. But I'm not sure what files are needed to be edited. Thanks in advance for your help =)

---

### Post by SlidingHorn on 2010-05-21
From your terminal, run 

```
sudo fdisk -l
```

And paste the result here.

---

### Post by lilsavalex on 2010-05-21
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59113   474825141    7  HPFS/NTFS
/dev/sda3           59114       60801    13558860    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009446a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11662    93667328   83  Linux
/dev/sdb2           11662       12162     4016129    5  Extended
/dev/sdb5           11662       12162     4016128   82  Linux swap / Solaris
```Here we go =] I just installed Ubuntu on the second hardrive which is sdb. I have vista installed on the first hardrive. My problem is that when i  rebooted after a successful OS installation and apparent grub install,  it went straight to boot up Vista.

---

### Post by oldfred on 2010-05-21
Do you boot directly to windows. Then switch drives in BIOS. 

Do you boot directly to Ubuntu. It did not see the windows and you have to hold shift key (if grub2) or escape key(if grub legacy) from BIOS until menu appears. 

If in Ubuntu, this will find your windows if it is working. 
sudo update-grub

---

### Post by lilsavalex on 2010-05-21
It automaticly boots me into Vista -_- And my second hardrive where ubuntu is install is a PM2, Should i put it was a slave or something els?

Alright, ill try that right now =] Thanks for the help. 

I tried that but this appears.
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

---

### Post by lilsavalex on 2010-05-21
Anyone have any idea?

---

### Post by oldfred on 2010-05-21
From liveCd download and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by lilsavalex on 2010-05-21
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-781739675DD521200E8602AC9D6E6C47.mbr is 
                       trying to chain load sector #187338752 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 75805896 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   949,650,344   949,650,282   7 HPFS/NTFS
/dev/sda3         949,650,345   976,768,064    27,117,720   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   187,336,703   187,334,656  83 Linux
/dev/sdb2         187,338,750   195,371,007     8,032,258   5 Extended
/dev/sdb5         187,338,752   195,371,007     8,032,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E70817870813823                       ntfs       HP                            
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        dabf9ef8-2ed3-4786-9c76-2a56d5709d6c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        70b5625a-eaff-4432-b5dd-3614ab89426d   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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

[operating systems] 
[boot loader] 
timeout=5 
c:\grldr="grub4dos"
=================== sda1: Location of files loaded by Grub: ===================


    hpGB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=70b5625a-eaff-4432-b5dd-3614ab89426d none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
  38.8GB: initrd.img
  38.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4b ac 49 f9 67 2b e3 eb  e4 71 72 e8 8a 62 5e 59  |K.I.g+...qr..b^Y|
00000010  6b bc b8 a7 4d 96 e7 49  41 a9 40 dc a5 de 9d d1  |k...M..IA.@.....|
00000020  e7 c8 4e a8 c0 58 77 9d  ed 80 5c 9c c0 e2 76 be  |..N..Xw...\...v.|
00000030  e5 84 05 ee b7 a2 d4 1a  30 26 43 31 6b 7c f8 13  |........0&C1k|..|
00000040  cb b6 34 3c 38 c0 ed c7  66 19 75 25 46 b7 00 69  |..4<8...f.u%F..i|
00000050  ee 3a fa 22 f0 bc bc b7  1e 0e 52 63 6a fc b9 60  |.:."......Rcj..`|
00000060  b9 fe 6b 9e 3e 31 1b 3d  e8 14 bd 87 b6 b0 e8 e1  |..k.>1.=........|
00000070  35 9e 68 18 af 8a c2 52  7d a1 2b 97 8e 9a 94 e1  |5.h....R}.+.....|
00000080  22 b4 2d b7 29 ad 15 fb  fb 3a 7c 7c 77 b9 99 1d  |".-.)....:||w...|
00000090  e9 03 1b 74 a0 89 88 ff  47 a3 31 26 fe e2 73 f4  |...t....G.1&..s.|
000000a0  88 26 81 b8 4c f9 aa 62  cf 36 a4 63 82 00 d0 23  |.&..L..b.6.c...#|
000000b0  78 5a a5 12 60 46 3f 32  96 f5 48 68 9e 1b 07 73  |xZ..`F?2..Hh...s|
000000c0  fb 3c 16 e7 42 6f 92 13  ae 20 56 ab 64 a1 cc e0  |.<..Bo... V.d...|
000000d0  92 67 78 12 e1 46 0a 88  c4 a7 46 4c 22 0b b2 65  |.gx..F....FL"..e|
000000e0  44 2c 1f ba 0c bc 1e 00  63 1f 30 f5 3c 4c e6 e8  |D,......c.0.<L..|
000000f0  a9 bb 4a 73 2a fa ee b0  84 67 aa 37 bc 0e c6 30  |..Js*....g.7...0|
00000100  2c ae 5a 49 b7 de 24 69  22 14 88 32 f0 a2 6c cc  |,.ZI..$i"..2..l.|
00000110  47 91 ce 2d 87 4b e3 17  22 65 f8 45 d0 e5 8a de  |G..-.K.."e.E....|
00000120  7c b4 3f d5 92 3f 47 f4  db a4 61 98 f2 d3 02 50  ||.?..?G...a....P|
00000130  f2 f1 e8 b6 31 86 a7 8b  ec f3 bf 74 a5 e6 2e 73  |....1......t...s|
00000140  70 16 e3 85 59 4c 8e b8  2a c0 47 93 26 4a 3c 3e  |p...YL..*.G.&J<>|
00000150  d9 40 f7 4f ef d7 ee 3c  46 fb 8c f9 a5 6e bc c6  |.@.O...<F....n..|
00000160  fd 98 58 91 f2 86 da f0  6c 98 b7 4c c3 73 89 bf  |..X.....l..L.s..|
00000170  26 29 56 a2 1a 02 2a ab  68 0c 61 67 04 90 7d 2c  |&)V...*.h.ag..},|
00000180  66 59 d9 35 ad 0c 96 c3  01 d1 da 7b 03 e1 1d 3e  |fY.5.......{...>|
00000190  8f 98 cc 86 8c bf f0 da  78 65 a9 f5 60 58 3a 39  |........xe..`X:9|
000001a0  c3 3a db ab 5f 31 e2 56  ef ba a1 e0 9d dc f8 07  |.:.._1.V........|
000001b0  9b ed 97 0f 91 05 c5 62  3f d5 74 7f 6d 65 00 fe  |.......b?.t.me..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

``` I tried using NeoSmart's EasyBcd but i was unsuccessful.

---

### Post by oldfred on 2010-05-22
I see two things:

/NST/menu.lst /boot.ini [COLOR=Red]/bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe[/COLOR] /grldr 
                       /boot/grub/core.img

The windows files are in red. Delete the rest. In fact the /boot conflicts with the /Boot as windows does not know the difference between caps and small letters so it sees two identical directories and does not work.

    Boot file info:     [COLOR=DarkRed]BootPart in the file 
                       /NST/nst_grub-781739675DD521200E8602AC9D6E6C47.mbr is 
                       trying to chain load sector #187338752 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to [/COLOR]

This is not a windows boot loader.

This may fix it :
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

IF not you will need to run fixboot from a windows repair disk to repair the boot sector.

You will then need to install grub to sdb. Leave lilo in sda.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

Then set sdb to boot in BIOS.

---

### Post by lilsavalex on 2010-05-22
I first tried the disktest thing and I thought it was going to fix everything. But I was wrong, Vista is now corrupted and I can't open a single program without it crashing and giving me and error and telling me to run chkdisk. I tried but it also crashes, I also can't mount that drive -_- But I'm making a windows recovery disk and hopefully that solves that. And after that I did the last thing you said. But everytime I try and boot from sdb I get "Bootmgr is missing, press alt-crtl-del to restart". I'm left without an OS. I'm left with the live cd and I can use my cousin desktop to try and fix mine.

---

### Post by lilsavalex on 2010-05-22
Ohh and I almost forgot. Thanks for trying to help :] I appreciate it (: <3

---

### Post by hopeless8009 on 2010-05-22
here is a little info that i learned when trying to boot 2 OS a long time ago. Vista has a boot loader of its own. if it is over wirtten and you boot into vista. Vista will reinstall its boot loader. i ended up using a program call system commander to step in as the boot loader. it has a feather in it to disable that in vista. i would segest you look into that

---

### Post by lilsavalex on 2010-05-22
Thanks =] But i cant go into vista, not sure if you read the 2 last posts i put. And everytime i try mounting SDB this happens All i really care about right now is fixing my vista. Thats where i have all my stuff thats really important to me

```
Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x6e696268  size: 4096  usa_ofs: 8192  usa_count: 240: Invalid argument
Actual VCN (0x0) of index buffer is different from expected VCN (0x5).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

---

### Post by wilee-nilee on 2010-05-22
> **hopeless8009 said:**
> here is a little info that i learned when trying to boot 2 OS a long time ago. Vista has a boot loader of its own. if it is over wirtten and you boot into vista. Vista will reinstall its boot loader. i ended up using a program call system commander to step in as the boot loader. it has a feather in it to disable that in vista. i would segest you look into that

I would ignore this as it is a 1st post and suggesting a unorthodox method to fix something that is broken; and needs to be fixed with the stock bootloaders, and the help of somebody who knows what there doing.

I also don't think Vista has a built in program to overwrite the MBR automatically, but manufacturers put funny things on the computer though. Many people dual boot Vista with many other operating systems with no problems.

---

### Post by lilsavalex on 2010-05-22
Then what do you suggest for me to do? -_-

---

### Post by wilee-nilee on 2010-05-22
> **lilsavalex said:**
> Then what do you suggest for me to do? -_-

I would repost the script as some changes have been suggested and then wait for oldfred or some others I wont name they know who they are to suggest some fixes.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
In the end this probably can be fixed, it just may take some special work. You also want to be careful with trying some fix and it not working then trying another that is attached to the 1st one working, this will make things very difficult to fix things. As it is now the system is pretty borked but fixable probably so you have to tread lightly at this point.

---

### Post by hopeless8009 on 2010-05-22
> **wilee-nilee said:**
> I would ignore this as it is a 1st post and suggesting a unorthodox method to fix something that is broken; and needs to be fixed with the stock bootloaders, and the help of somebody who knows what there doing.

I also don't think Vista has a built in program to overwrite the MBR automatically, but manufacturers put funny things on the computer though. Many people dual boot Vista with many other operating systems with no problems.

I built my own system it was not made my a company. the output form the mouth command tells me you may have a hardware problem. you can boot to you widnows disk and use recovory console to run chkdsk if you like :-) night night

---

### Post by lilsavalex on 2010-05-22
I should probly be extra careful on what i try to do when fixing it =] Thanks for the tip.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 75805896 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   949,650,344   949,650,282   7 HPFS/NTFS
/dev/sda3         949,650,345   976,768,064    27,117,720   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   187,336,703   187,334,656  83 Linux
/dev/sdb2         187,338,750   195,371,007     8,032,258   5 Extended
/dev/sdb5         187,338,752   195,371,007     8,032,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E70817870813823                       ntfs       HP                            
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        dabf9ef8-2ed3-4786-9c76-2a56d5709d6c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        70b5625a-eaff-4432-b5dd-3614ab89426d   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=70b5625a-eaff-4432-b5dd-3614ab89426d none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
  38.8GB: initrd.img
  38.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4b ac 49 f9 67 2b e3 eb  e4 71 72 e8 8a 62 5e 59  |K.I.g+...qr..b^Y|
00000010  6b bc b8 a7 4d 96 e7 49  41 a9 40 dc a5 de 9d d1  |k...M..IA.@.....|
00000020  e7 c8 4e a8 c0 58 77 9d  ed 80 5c 9c c0 e2 76 be  |..N..Xw...\...v.|
00000030  e5 84 05 ee b7 a2 d4 1a  30 26 43 31 6b 7c f8 13  |........0&C1k|..|
00000040  cb b6 34 3c 38 c0 ed c7  66 19 75 25 46 b7 00 69  |..4<8...f.u%F..i|
00000050  ee 3a fa 22 f0 bc bc b7  1e 0e 52 63 6a fc b9 60  |.:."......Rcj..`|
00000060  b9 fe 6b 9e 3e 31 1b 3d  e8 14 bd 87 b6 b0 e8 e1  |..k.>1.=........|
00000070  35 9e 68 18 af 8a c2 52  7d a1 2b 97 8e 9a 94 e1  |5.h....R}.+.....|
00000080  22 b4 2d b7 29 ad 15 fb  fb 3a 7c 7c 77 b9 99 1d  |".-.)....:||w...|
00000090  e9 03 1b 74 a0 89 88 ff  47 a3 31 26 fe e2 73 f4  |...t....G.1&..s.|
000000a0  88 26 81 b8 4c f9 aa 62  cf 36 a4 63 82 00 d0 23  |.&..L..b.6.c...#|
000000b0  78 5a a5 12 60 46 3f 32  96 f5 48 68 9e 1b 07 73  |xZ..`F?2..Hh...s|
000000c0  fb 3c 16 e7 42 6f 92 13  ae 20 56 ab 64 a1 cc e0  |.<..Bo... V.d...|
000000d0  92 67 78 12 e1 46 0a 88  c4 a7 46 4c 22 0b b2 65  |.gx..F....FL"..e|
000000e0  44 2c 1f ba 0c bc 1e 00  63 1f 30 f5 3c 4c e6 e8  |D,......c.0.<L..|
000000f0  a9 bb 4a 73 2a fa ee b0  84 67 aa 37 bc 0e c6 30  |..Js*....g.7...0|
00000100  2c ae 5a 49 b7 de 24 69  22 14 88 32 f0 a2 6c cc  |,.ZI..$i"..2..l.|
00000110  47 91 ce 2d 87 4b e3 17  22 65 f8 45 d0 e5 8a de  |G..-.K.."e.E....|
00000120  7c b4 3f d5 92 3f 47 f4  db a4 61 98 f2 d3 02 50  ||.?..?G...a....P|
00000130  f2 f1 e8 b6 31 86 a7 8b  ec f3 bf 74 a5 e6 2e 73  |....1......t...s|
00000140  70 16 e3 85 59 4c 8e b8  2a c0 47 93 26 4a 3c 3e  |p...YL..*.G.&J<>|
00000150  d9 40 f7 4f ef d7 ee 3c  46 fb 8c f9 a5 6e bc c6  |.@.O...<F....n..|
00000160  fd 98 58 91 f2 86 da f0  6c 98 b7 4c c3 73 89 bf  |..X.....l..L.s..|
00000170  26 29 56 a2 1a 02 2a ab  68 0c 61 67 04 90 7d 2c  |&)V...*.h.ag..},|
00000180  66 59 d9 35 ad 0c 96 c3  01 d1 da 7b 03 e1 1d 3e  |fY.5.......{...>|
00000190  8f 98 cc 86 8c bf f0 da  78 65 a9 f5 60 58 3a 39  |........xe..`X:9|
000001a0  c3 3a db ab 5f 31 e2 56  ef ba a1 e0 9d dc f8 07  |.:.._1.V........|
000001b0  9b ed 97 0f 91 05 c5 62  3f d5 74 7f 6d 65 00 fe  |.......b?.t.me..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Input/output error
```

---

### Post by oldfred on 2010-05-22
You deleted the windows boot files in sda1, that I had in red in my previous post that said to deleted the other files.
[COLOR=Red]/bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe
[COLOR=Black]You need to put these files back, you may be able to get them by running windows repairs. Also install the windows boot loader with fixmbr to sda as you will be using grub in sdb.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

[/COLOR][/COLOR]

---

### Post by lilsavalex on 2010-05-22
When it asks me to select the operating system, nothing pops up. And I tried going ahead and doing everything single thing you told me to. It still doesn't work -_-

---

### Post by oldfred on 2010-05-22
Did you get back the files that are missing. How did they get deleted. Did you delete the entire windows install. I would expect the windows tools to repair it but I never had to run repairs, so I am not sure.

---

### Post by lilsavalex on 2010-05-22
I didnt get them back -_- It was that testdisk crap, But it was my fault.. Some human error, i probly clicked on something that i wasnt suppose to. Nope, Fully i didnt cus i have alot of Data that is very crucial to me =]

---

### Post by lilsavalex on 2010-05-22
Right now, all im really interested in is Fixing My vista,

---

### Post by oldfred on 2010-05-22
If you have not overwritten the space, testdisk also will recover deleted files. I do not know exact procedure, but look at the instructions on the testdisk site.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by lilsavalex on 2010-05-22
But i have to fix the missing bootmgr thing first inroder to do that, i just created another Windows Recovery CD and ill try to fix that. After that ill try what you said =]

---

### Post by lilsavalex on 2010-05-22
Windows recovery cd method - unsuccessfull -_- Anything els I could try to fix vista? That's all I really care about.
Heres boot info script and the fdisk -l. Hopefully it becomes usefull.

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009446a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11662    93667328   83  Linux
/dev/sda2           11662       12162     4016129    5  Extended
/dev/sda5           11662       12162     4016128   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59113   474825141    7  HPFS/NTFS
/dev/sdb3           59114       60801    13558860    7  HPFS/NTFS
```

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 75805896 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   187,336,703   187,334,656  83 Linux
/dev/sda2         187,338,750   195,371,007     8,032,258   5 Extended
/dev/sda5         187,338,752   195,371,007     8,032,256  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   949,650,344   949,650,282   7 HPFS/NTFS
/dev/sdb3         949,650,345   976,768,064    27,117,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dabf9ef8-2ed3-4786-9c76-2a56d5709d6c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        70b5625a-eaff-4432-b5dd-3614ab89426d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3E70817870813823                       ntfs       HP                            
/dev/sdb3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set dabf9ef8-2ed3-4786-9c76-2a56d5709d6c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
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
# / was on /dev/sdb1 during installation
UUID=dabf9ef8-2ed3-4786-9c76-2a56d5709d6c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=70b5625a-eaff-4432-b5dd-3614ab89426d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
  38.8GB: initrd.img
  38.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4b ac 49 f9 67 2b e3 eb  e4 71 72 e8 8a 62 5e 59  |K.I.g+...qr..b^Y|
00000010  6b bc b8 a7 4d 96 e7 49  41 a9 40 dc a5 de 9d d1  |k...M..IA.@.....|
00000020  e7 c8 4e a8 c0 58 77 9d  ed 80 5c 9c c0 e2 76 be  |..N..Xw...\...v.|
00000030  e5 84 05 ee b7 a2 d4 1a  30 26 43 31 6b 7c f8 13  |........0&C1k|..|
00000040  cb b6 34 3c 38 c0 ed c7  66 19 75 25 46 b7 00 69  |..4<8...f.u%F..i|
00000050  ee 3a fa 22 f0 bc bc b7  1e 0e 52 63 6a fc b9 60  |.:."......Rcj..`|
00000060  b9 fe 6b 9e 3e 31 1b 3d  e8 14 bd 87 b6 b0 e8 e1  |..k.>1.=........|
00000070  35 9e 68 18 af 8a c2 52  7d a1 2b 97 8e 9a 94 e1  |5.h....R}.+.....|
00000080  22 b4 2d b7 29 ad 15 fb  fb 3a 7c 7c 77 b9 99 1d  |".-.)....:||w...|
00000090  e9 03 1b 74 a0 89 88 ff  47 a3 31 26 fe e2 73 f4  |...t....G.1&..s.|
000000a0  88 26 81 b8 4c f9 aa 62  cf 36 a4 63 82 00 d0 23  |.&..L..b.6.c...#|
000000b0  78 5a a5 12 60 46 3f 32  96 f5 48 68 9e 1b 07 73  |xZ..`F?2..Hh...s|
000000c0  fb 3c 16 e7 42 6f 92 13  ae 20 56 ab 64 a1 cc e0  |.<..Bo... V.d...|
000000d0  92 67 78 12 e1 46 0a 88  c4 a7 46 4c 22 0b b2 65  |.gx..F....FL"..e|
000000e0  44 2c 1f ba 0c bc 1e 00  63 1f 30 f5 3c 4c e6 e8  |D,......c.0.<L..|
000000f0  a9 bb 4a 73 2a fa ee b0  84 67 aa 37 bc 0e c6 30  |..Js*....g.7...0|
00000100  2c ae 5a 49 b7 de 24 69  22 14 88 32 f0 a2 6c cc  |,.ZI..$i"..2..l.|
00000110  47 91 ce 2d 87 4b e3 17  22 65 f8 45 d0 e5 8a de  |G..-.K.."e.E....|
00000120  7c b4 3f d5 92 3f 47 f4  db a4 61 98 f2 d3 02 50  ||.?..?G...a....P|
00000130  f2 f1 e8 b6 31 86 a7 8b  ec f3 bf 74 a5 e6 2e 73  |....1......t...s|
00000140  70 16 e3 85 59 4c 8e b8  2a c0 47 93 26 4a 3c 3e  |p...YL..*.G.&J<>|
00000150  d9 40 f7 4f ef d7 ee 3c  46 fb 8c f9 a5 6e bc c6  |.@.O...<F....n..|
00000160  fd 98 58 91 f2 86 da f0  6c 98 b7 4c c3 73 89 bf  |..X.....l..L.s..|
00000170  26 29 56 a2 1a 02 2a ab  68 0c 61 67 04 90 7d 2c  |&)V...*.h.ag..},|
00000180  66 59 d9 35 ad 0c 96 c3  01 d1 da 7b 03 e1 1d 3e  |fY.5.......{...>|
00000190  8f 98 cc 86 8c bf f0 da  78 65 a9 f5 60 58 3a 39  |........xe..`X:9|
000001a0  c3 3a db ab 5f 31 e2 56  ef ba a1 e0 9d dc f8 07  |.:.._1.V........|
000001b0  9b ed 97 0f 91 05 c5 62  3f d5 74 7f 6d 65 00 fe  |.......b?.t.me..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

ls: reading directory sdb1/: Input/output error
```

---

### Post by oldfred on 2010-05-22
Did you switch drives or are these IDE drives that can only be switched that way? Normally BIOS lets you select boot drive without switching unless you have the old IDE drives with jumpers for master & slave.

You need to install grub to what is not sda the 100GB drive. Use a liveCD.
You also need to install windows boot loader to the 500GB drive and you will want it to be first drive when you do that so it puts its boot loader on that drive. Your fixMBR overwrote the sda 100GB drive not the lilo in the windows drive. Change drives and run fixMBR again. That may be why windows does not work.

I would do this first while Ubuntu is still on sda.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be sure to install grub2 to the 100GB drive whether it is sda or sdb.
Install from LiveCD:
Find linux partition, if sda1 ( if sdb1 change all sda or sda1 to sdb or sdb1:
sudo fdisk -l
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by lilsavalex on 2010-05-22
Thanks, will try this =] How would i go upon fixing the Bootmgr missing? if i cant use the Recovery CD to fix it cus it wont let me.
It also doesnt let me mount Sdb -_-


  I get this when trying to mount it.

```
Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x6e696268  size: 4096  usa_ofs: 8192  usa_count: 240: Invalid argument
Actual VCN (0x0) of index buffer is different from expected VCN (0x5).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by oldfred on 2010-05-22
After you install grub switch drives back and see if it will let you run check disk chkdsk.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Always run chkdsk and run again until there are no errors, that may be all that is required

Testdisk can also repair some other windows errors:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by lilsavalex on 2010-05-22
How would i go upon switching back the drivers?

---

### Post by oldfred on 2010-05-23
I only have SATA drives on my computer now, and the drive order sda, sdb, sdc is the order they are plugged into the SATA ports. Changing boot order in BIOS only changes which drive boots.

Older IDE drives order depends on either the location plugged into the cable (cable select)  or the jumpers on the hard drive, master, slave. Or is this an external drive, sometimes they are first or second.

Somehow you switch drive order and I bet windows does not like that. Windows should be the first drive but you want to boot from the Ubuntu drive (100GB). If you have old IDE drives you may have to have the windows drive first but install grub to that drive as you may not be able to set sdb as the boot drive.

---

### Post by lilsavalex on 2010-05-23
The windows is a SATA hardrive. The other one the 100gb is the older version. I'll try and switch it the slave with the little white thing on the physical hardrive and maybe that switches it back :] But I know I some how switched it with testdisk, can you switch it back wiry that?

---

### Post by oldfred on 2010-05-23
You want the IDE drive to be set for master, then check your BIOS and see if you can set boot order which should not be drive order.

---

### Post by lilsavalex on 2010-05-23
He IDE is set to masters already, the IDE is the 100gb. It's been set to masters

---

### Post by lilsavalex on 2010-06-04
I fix the boot mgr thing. I could also mount my HP hardrive. Everything is still there :) But. Now it says Hal.dll is missing or corrupted but infact it's there now after I did some chkdsk c: /r .

---

### Post by oldfred on 2010-06-04
Missing hal.dll is caused by a variety of windows errors:

Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by lilsavalex on 2010-06-04
Everytime I try and do bootcfg /rebuild it always gives me an error or something and doesn't let me -_- I'm missing Boot.ini and now i cant seem to get it back.

---

### Post by lilsavalex on 2010-06-04
Everytime i try and boot it says Hal.dll is missing or corrupted. Even though i booted with the live cd into linux and it Hal.dll is there.

---

### Post by oldfred on 2010-06-04
If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Edit Boot.ini
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

The microsoft site has a sample boot.ini but it may require changes depending on what partition you are booting from.

---

### Post by lilsavalex on 2010-06-05
I just realized that boot.ini was removed for vista and 7. If its saying that hal.dll is missing or corrupted it could no longer be that boot.ini is corrupted or anything. Then what could it be? Could vista still depend of boot.ini? Or is bootmgr corrupted?

---

### Post by oldfred on 2010-06-05
Vista & win7 do not use boot.ini but use BCD:

Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

But then you need to repair the bootmgr or the BCD.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

