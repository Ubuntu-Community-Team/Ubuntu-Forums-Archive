---
title: "Recover Win XP after Ubuntu 10.04 install"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by bsmith52 on 2010-11-21
I recently installed 10.04 with on my Win XP machine.  I resized the partition (to allow room for ubuntu), then installed it. I generated a 3gb swap partition, and allowed the remainder to be ubuntu. This is what Boot info script says I have:

************************************************************************

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,902   156,301,311    74,385,410   5 Extended
/dev/sda5          81,915,904    87,775,231     5,859,328  82 Linux swap / Solaris
/dev/sda6          87,777,280   156,301,311    68,524,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D8AC7CDDAC7CB818                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c2c52373-9846-4ca3-9e6d-5eca1a64796e   swap                                     
/dev/sda6        99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================


********************************************************************

I did a similar proceeure when I had Win XP and Ubuntu 8.10. There, I had an option to boot into Windows at system boot time. I no longer see this option with 10.04. 

I can see all my Win XP files, in the 42gb file system in ubuntu. Is there a way to boot into Win XP? Or do I need to start from scratch, and attempt a dual boot in another way?

Thanks for your help.

---

### Post by sikander3786 on 2010-11-21
You boot files for Windows XP seem intact so that should not be an issue here. And also the boot flag is properly set to the Windows partition.

You didn't post the complete output of bootinfoscript as it contained something informative towards the end.

Please post it again and use the proper code tags # this time from the post menu.

And also do this command and see if it picks up Windows.

```
sudo update-grub
```

If Windows XP is mentioned in the output, you are good to go.

---

### Post by wilee-nilee on 2010-11-21
post whole script as suggested. Click on the # in the reply panel and paste all the text in between the code tags.

---

### Post by bsmith52 on 2010-11-21
Thanks for the solution! I now have back access to Win XP.

For practice, here is the Boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,902   156,301,311    74,385,410   5 Extended
/dev/sda5          81,915,904    87,775,231     5,859,328  82 Linux swap / Solaris
/dev/sda6          87,777,280   156,301,311    68,524,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D8AC7CDDAC7CB818                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c2c52373-9846-4ca3-9e6d-5eca1a64796e   swap                                     
/dev/sda6        99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=99fe9def-f4f5-4c4d-8d6f-3f8ea870b9ce /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c2c52373-9846-4ca3-9e6d-5eca1a64796e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  59.0GB: boot/grub/core.img
  59.1GB: boot/grub/grub.cfg
  59.1GB: boot/initrd.img-2.6.32-21-generic
  59.1GB: boot/initrd.img-2.6.32-22-generic
  59.0GB: boot/initrd.img-2.6.32-23-generic
  59.1GB: boot/vmlinuz-2.6.32-21-generic
  59.1GB: boot/vmlinuz-2.6.32-22-generic
  59.1GB: boot/vmlinuz-2.6.32-23-generic
  59.0GB: initrd.img
  59.1GB: initrd.img.old
  59.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ed e1 b5 d3 74 cb bd 3c  5c 0b 94 d5 24 9d e4 9e  |....t..<\...$...|
00000010  e4 24 66 dd 22 58 f1 26  e1 f9 1f e2 cf f8 29 3f  |.$f."X.&......)?|
00000020  ed 73 e2 b9 25 11 7c 42  d3 7c 23 03 ae 52 2f 06  |.s..%.|B.|#..R/.|
00000030  f8 57 45 d2 e5 40 49 c2  ad ee a1 6f ab 6a 39 51  |.WE..@I....o.j9Q|
00000040  91 bc 5e 2b 02 14 e4 67  8f 68 ff 00 82 b4 7c 47  |..^+...g.h....|G|
00000050  d1 f5 dd 73 e0 5c 76 69  72 8d 0e 8b e3 f8 98 ca  |...s.\vir.......|
00000060  8a 16 66 6b ff 00 0c 3a  88 b6 92 4a a2 a9 dc 4f  |..fk...:...J...O|
00000070  39 e9 d0 93 f9 0b 16 ad  0b 91 cf 07 82 49 19 c9  |9............I..|
00000080  3c 02 38 39 18 23 1d 40  23 a7 15 f9 8e 7f 98 e3  |<.89.#.@#.......|
00000090  a3 99 62 a8 43 17 5e 95  0a 6e 92 84 29 54 95 35  |..b.C.^..n..)T.5|
000000a0  67 42 8c a4 ef 0e 57 25  cf 29 36 db 7a b7 a5 95  |gB....W%.)6.z...|
000000b0  9f b3 94 60 f0 95 30 18  7a d2 a1 46 a5 49 fb 47  |...`..0.z..F.I.G|
000000c0  29 ce 2a 4d f2 d6 9c 62  ed 2e 68 ab 45 25 65 14  |).*M...b..h.E%e.|
000000d0  b6 76 6e f7 f5 9f 89 bf  1b be 32 fc 41 82 e0 f8  |.vn.......2.A...|
000000e0  bb e2 d7 c4 8d 75 99 65  99 d2 f7 c6 5a eb db 48  |.....u.e....Z..H|
000000f0  62 06 56 84 d9 25 ea 59  2d bc db 04 72 c6 96 ca  |b.V..%.Y-...r...|
00000100  ad 1b 14 50 bd 47 e1 2f  ec 5f fb 6e f8 0b e0 d7  |...P.G./._.n....|
00000110  c2 6d 76 d7 e2 d7 c1 a9  ff 00 68 dd 7e db e2 65  |.mv.......h.~..e|
00000120  ec 7a 6c 2d f1 1f c5 1a  3f 8b 34 5f 0a 1d 0e d2  |.zl-....?.4_....|
00000130  d2 d3 48 87 4e 8f c2 9a  b6 98 9a 05 96 a7 69 73  |..H.N.........is|
00000140  a8 26 a5 16 ba 6f da 6b  cf b2 36 98 23 56 9e bf  |.&...o.k..6.#V..|
00000150  5b b5 6d 48 34 4c 14 83  fb 89 c1 ce 0e 37 c6 fd  |[.mH4L.......7..|
00000160  73 d3 27 d4 e3 3c 63 ad  7e 49 ff 00 c1 37 be 24  |s.'..<c.~I...7.$|
00000170  7f c1 42 fc 1f f0 97 c6  da 67 ec 53 f0 aa fb e2  |..B......g.S....|
00000180  55 8c ff 00 19 75 2d 4f  c4 b1 cd f0 c3 c2 1e 2f  |U....u-O......./|
00000190  d1 ec b5 66 f0 be 91 a6  cc a3 58 d6 fc 67 a7 6a  |...f......X..g.j|
000001a0  67 51 5d 31 ac de 4d 18  78 72 4d 2a d9 26 b3 d4  |gQ]1..M.xrM*.&..|
000001b0  7f b6 de f2 51 6d 69 8e  0e 86 1f 19 91 e7 00 fe  |....Qmi.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 68 59 00 00 fe  |...........hY...|
000001d0  ff ff 05 fe ff ff 02 68  59 00 00 a0 15 04 00 00  |.......hY.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thanks again for your solution.

---

### Post by sikander3786 on 2010-11-22
You are welcome :-)

Glad to know that it worked for you.

You can mark the thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

Edit: I assume that the Results of bootinfoscript above are those generated before running the update-grub command as there is nothing listed here.

```
### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###
```

---

