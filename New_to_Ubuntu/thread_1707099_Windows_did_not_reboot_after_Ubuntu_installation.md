---
title: "Windows did not reboot after Ubuntu installation"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by hiramj5077 on 2011-03-14
I installed Ubuntu 10.04.1 in a partition alongside the Windows XP.  When I tried to reboot the system in Windows it did not boot. 

What can I do?
:p

---

### Post by Hedgehog1 on 2011-03-15
We need to get a look at your disk partition layout.

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by mastablasta on 2011-03-15
also use this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the webstie and post the results here.
 
this will tell us how system is booting and why there is an error.

---

### Post by johnnyzee on 2011-03-15
HELP PLEASE
I am having the same problem after loading Ubuntu 10.10 alongside my XP Pro OS. I was able to log onto the internet wireless several hours ago but somehow have lost that ability now so have not tried the other script solution.Here is the info from the fdisk -l query. Am hoping somebody can help. I get the option to open Win XP but when selected nothing happens. I even have the option to edit the GRUB (??) on the opening screen.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9e6a9e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14607   117326927    7  HPFS/NTFS
/dev/sda2           14607       19458    38962177    5  Extended
/dev/sda5           14607       19253    37318656   83  Linux
/dev/sda6           19253       19458     1642496   82  Linux swap / Solaris

---

### Post by mastablasta on 2011-03-15
please also do the "script solution". script will tell how it is installed and indicate possible issues to people that can read it. :-)
 
this shouldn't happen. not in winXP. and not if you followed all the rules/precautions. you data seems to be still there. so we will juct need to somehow fix the boot sector. to do that info is needed on how the computer boots.

---

### Post by johnnyzee on 2011-03-15
Here are the results of the Bootinfoscript test.

You help is most appreciated.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 276892320 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,653,916   234,653,854   7 HPFS/NTFS
/dev/sda2         234,655,742   312,580,095    77,924,354   5 Extended
/dev/sda5         234,655,744   309,293,055    74,637,312  83 Linux
/dev/sda6         309,295,104   312,580,095     3,284,992  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56946E25946E07B7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        da0959b3-8c95-473d-99fc-8063b0778a0f   ext4                                     
/dev/sda6        37dcdd3f-7f6d-40d1-9131-802c8760b939   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=da0959b3-8c95-473d-99fc-8063b0778a0f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=da0959b3-8c95-473d-99fc-8063b0778a0f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set da0959b3-8c95-473d-99fc-8063b0778a0f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 56946e25946e07b7
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=da0959b3-8c95-473d-99fc-8063b0778a0f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=37dcdd3f-7f6d-40d1-9131-802c8760b939 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 141.7GB: boot/grub/core.img
 124.6GB: boot/grub/grub.cfg
 121.2GB: boot/initrd.img-2.6.35-27-generic-pae
 141.7GB: boot/vmlinuz-2.6.35-27-generic-pae
 121.2GB: initrd.img
 141.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ef fe a8 66 ff 00 19 58  7f be af 7f e9 02 ef fe  |...f...X........|
00000010  a8 60 2d 6b cd f6 32 69  f7 28 23 bd ab 43 20 15  |.`-k..2i.(#..C .|
00000020  b1 ba 03 75 3d 49 86 83  e9 c4 fc bb e6 eb 18 b4  |...u=I..........|
00000030  9b 38 da 3b c2 56 de 20  78 d8 dd 30 d9 07 46 58  |.8.;.V. x..0..FX|
00000040  48 23 dc 61 8f f8 ca c3  fd f5 7b ff 00 48 17 7f  |H#.a......{..H..|
00000050  f5 43 37 f8 ca c3 fd f5  7b ff 00 48 17 7f f5 43  |.C7.....{..H...C|
00000060  37 f8 ca c3 fd f5 7b ff  00 48 17 7f f5 43 37 f8  |7.....{..H...C7.|
00000070  ca c3 fd f5 7b ff 00 48  17 7f f5 43 37 f8 ca c3  |....{..H...C7...|
00000080  fd f5 7b ff 00 48 17 7f  f5 43 37 f8 ca c3 fd f5  |..{..H...C7.....|
00000090  7b ff 00 48 17 7f f5 43  37 f8 ca c3 fd f5 7b ff  |{..H...C7.....{.|
000000a0  00 48 17 7f f5 43 37 f8  ca c3 fd f5 7b ff 00 48  |.H...C7.....{..H|
000000b0  17 7f f5 43 09 bc e9 e6  cb 29 fc bf a8 c4 91 de  |...C.....)......|
000000c0  06 7b 3b 85 05 ac ae 51  6a 63 61 f1 33 42 15 47  |.{;....Qjca.3B.G|
000000d0  89 24 01 df 06 68 be 6f  b1 8f 4f b6 43 1d ed 56  |.$...h.o..O.C..V|
000000e0  18 c1 a5 8d d1 1b 28 e8  44 34 3f 46 0d ff 00 19  |......(.D4?F....|
000000f0  58 7f be af 7f e9 02 ef  fe a8 66 ff 00 19 58 7f  |X.........f...X.|
00000100  be af 7f e9 02 ef fe a8  66 ff 00 19 58 7f be af  |........f...X...|
00000110  7f e9 02 ef fe a8 66 ff  00 19 58 7f be af 7f e9  |......f...X.....|
00000120  02 ef fe a8 66 ff 00 19  58 7f be af 7f e9 02 ef  |....f...X.......|
00000130  fe a8 66 ff 00 19 58 7f  be af 7f e9 02 ef fe a8  |..f...X.........|
00000140  66 ff 00 19 58 7f be af  7f e9 02 ef fe a8 66 ff  |f...X.........f.|
00000150  00 19 58 7f be af 7f e9  02 ef fe a8 66 ff 00 19  |..X.........f...|
00000160  58 7f be af 7f e9 02 ef  fe a8 64 67 f2 db cd 36  |X.........dg...6|
00000170  76 9e 58 b0 82 48 ee cb  24 20 12 96 77 32 2f 53  |v.X..H..$ ..w2/S|
00000180  d1 d2 26 56 fa 0e 49 bf  c6 56 1f ef ab df fa 40  |..&V..I..V.....@|
00000190  bb ff 00 aa 19 bf c6 56  1f ef ab df fa 40 bb ff  |.......V.....@..|
000001a0  00 aa 19 bf c6 56 1f ef  ab df fa 40 bb ff 00 aa  |.....V.....@....|
000001b0  19 bf c6 56 1f ef ab df  fa 40 bb ff 00 aa 00 fe  |...V.....@......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 72 04 00 fe  |............r...|
000001d0  ff ff 05 fe ff ff 02 e0  72 04 00 28 32 00 00 00  |........r..(2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Hedgehog1 on 2011-03-15
> **mastablasta said:**
> also use this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the webstie and post the results here.
 
mastablasta - I think I will switch to using the  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) for helping folks as well.
 
I am seeeing:
 
**sda1**: "but core.img can not be found at this location." 
 
**sda5** has the core.imgL Boot files/dirs: /boot/grub/grub.cfg /etc/fstab [B]/boot/grub/core.img
[/B]
**Unknown BootLoader on sda2**; sda2 is the extended partition.

But I don't quite know what to make of it; are any of these even the cause?
 
***The Hedge***

---

### Post by garvinrick4 on 2011-03-15
*I would say grub2 was installed in sda1 instead of sda and that caused a lot of errors.
#Put Windows grub back in place using link I give you.
#After Windows boots now put grub2 into sda and then boot into ubuntu and:
```
sudo update-grub
```
That will cause grub2's OS prober find your Windows install and put it in
grub2's menuentry and config file and you will be set to go.
Follow links instructions. Your linux install is in sda5
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
Use live CD method of installing grub2 into your mbr

---

### Post by johnnyzee on 2011-03-19
Thanks for the assistance. I finally ended up reloading Ubuntu from Live CD and that fixed the problem.

---

