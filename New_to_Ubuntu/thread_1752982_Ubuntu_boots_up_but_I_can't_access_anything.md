---
title: "Ubuntu boots up but I can't access anything"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by sprogmeister on 2011-05-08
I was having some trouble getting ubuntu to boot, but solved that. Having got it to boot up and through the log on the system will not allow me to do anything else. The arrow appears and I can move it around but I try and click on anything and nothing happens. Can anyone help?

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> I was having some trouble getting ubuntu to boot, but solved that. Having got it to boot up and through the log on the system will not allow me to do anything else. The arrow appears and I can move it around but I try and click on anything and nothing happens. Can anyone help?

Which OS release?

Is it a fresh install or a upgrade?

Do you have a live cd of this install, and does it work?

You are missing a lot of information here, these questions are a start.

---

### Post by sprogmeister on 2011-05-08
Which OS release? 11.04

Is it a fresh install or a upgrade? upgrade

Do you have a live cd of this install, and does it work? I do have a cd of it.

You are missing a lot of information here, these questions are a start.

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> Which OS release? 11.04

Is it a fresh install or a upgrade? upgrade

Do you have a live cd of this install, **and does it work? **I do have a cd of it.

You are missing a lot of information here, these questions are a start.

And.

So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us the information overall that may be needed with a thread becoming way to long with only sort answers.

This is free help remember that and work with us.

---

### Post by sprogmeister on 2011-05-08
Deleted

---

### Post by wilee-nilee on 2011-05-08
Repost of script for easier reading, OP in my signature and my instructions are code tags instructions did you notice this

```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #6 for cbdc4.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /ntldr /ntdetect.com

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sda6: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu natty (development
branch)
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 63 14,651,279 14,651,217 12 Compaq diagnostics
/dev/sda2 * 14,651,280 117,194,174 102,542,895 7 HPFS/NTFS
/dev/sda3 117,194,236 488,392,064 371,197,829 5 Extended
/dev/sda5 117,194,238 121,290,749 4,096,512 82 Linux swap / Solaris
/dev/sda6 121,290,813 488,392,064 367,101,252 83 Linux


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 63 488,392,064 488,392,002 7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 9ECCDDF0CCDDC327 ntfs Recovery Partition
/dev/sda2 4C54A5A254A58EF0 ntfs VAIO
/dev/sda3: PTTYPE="dos"
/dev/sda5 f5771dba-99f3-45ab-9961-5ddebe9ece57 swap
/dev/sda6 0cdde98f-ca59-46ac-9121-124e8eb87469 ext3
/dev/sda: PTTYPE="dos"
/dev/sdb1 BAA81135A810F21D ntfs Iain Backup
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sdb1 /media/Iain Backup fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windo ws XP Media Center Edition" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
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
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.38-8-generic ...'
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.35-28-generic ...'
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.32-19-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.32-19-generic ...'
linux /boot/vmlinuz-2.6.32-19-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.31-20-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.31-20-generic ...'
linux /boot/vmlinuz-2.6.31-20-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux /boot/vmlinuz-2.6.28-16-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
echo 'Loading Linux 2.6.28-16-generic ...'
linux /boot/vmlinuz-2.6.28-16-generic root=UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.28-16-generic
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
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0cdde98f-ca59-46ac-9121-124e8eb87469
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ECCDDF0CCDDC327
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 4C54A5A254A58EF0
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=0cdde98f-ca59-46ac-9121-124e8eb87469 / ext3 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=f5771dba-99f3-45ab-9961-5ddebe9ece57 none swap sw 0 0

=================== sda6: Location of files loaded by Grub: ===================


224.1GB: boot/grub/core.img
224.2GB: boot/grub/grub.cfg
224.1GB: boot/initrd.img-2.6.28-16-generic
225.6GB: boot/initrd.img-2.6.31-20-generic
224.2GB: boot/initrd.img-2.6.32-19-generic
100.6GB: boot/initrd.img-2.6.32-24-generic
226.1GB: boot/initrd.img-2.6.35-28-generic
227.7GB: boot/initrd.img-2.6.38-8-generic
225.5GB: boot/vmlinuz-2.6.28-16-generic
225.1GB: boot/vmlinuz-2.6.31-20-generic
224.1GB: boot/vmlinuz-2.6.32-19-generic
104.5GB: boot/vmlinuz-2.6.32-24-generic
159.4GB: boot/vmlinuz-2.6.35-28-generic
104.5GB: boot/vmlinuz-2.6.38-8-generic
227.7GB: initrd.img
226.1GB: initrd.img.old
104.5GB: vmlinuz
159.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda3

00000000 c1 d7 ab ea df 88 af ec d5 50 7a 7f dd bf b8 b9 |.........Pz.....|
00000010 77 f6 c2 a3 fa 75 ef af f2 a5 bd 24 e3 9a 01 36 |w....u.....$...6|
00000020 ef 79 55 c2 ea cf 58 8b bf 7f 32 b7 d0 60 9c 96 |.yU...X...2..`..|
00000030 fc a8 ab f5 f0 51 ec e4 46 50 54 70 c6 53 b7 01 |.....Q..FPTp.S..|
00000040 a5 4d 38 81 e9 21 f9 2c c2 ae e6 a2 74 d7 5d 69 |.M8..!.,....t.]i|
00000050 ef bf ff dc 0e 3a 8c 12 b7 ce dc 7f fd 85 37 bb |.....:........7.|
00000060 35 dd 67 7e f7 eb aa 7a e4 3c 0f a1 7b ac ef 7e |5.g~...z.<..{..~|
00000070 3b 81 7c e7 88 73 5a fd 70 c4 4c 89 65 fe 77 f1 |;.|..sZ.p.L.e.w.|
00000080 d3 8e f5 dc e4 cb 89 ad 69 68 f7 ce b6 e9 e5 7d |........ih.....}|
00000090 6e 54 ee f3 7e 3b db b7 f9 e7 77 ca 59 1c 29 8e |nT..~;....w.Y.).|
000000a0 aa a3 ef 51 81 b3 49 fa 97 5c fb 47 2d 76 e4 7e |...Q..I..\.G-v.~|
000000b0 fc a7 ff d0 47 8c dd 8d 65 f7 f7 8e 6c c9 7f ac |....G...e...l...|
000000c0 5c 72 bf f5 5c 7f 15 77 71 ee 29 0b ed 8f db b8 |\r..\..wq.).....|
000000d0 77 eb 54 a0 ab 05 6d 78 09 a1 e3 63 7e a5 a7 48 |w.T...mx...c~..H|
000000e0 dd 45 c4 87 cb 1e fa ff b4 ce f4 75 b1 6e 54 a2 |.E.........u.nT.|
000000f0 f6 25 f3 fe f9 b0 7d 7b f5 28 8b c1 ea 3f 7a d0 |.%....}{.(...?z.|
00000100 8f ff d3 de fe d5 8a 7c 05 91 6d 90 f3 70 dc da |.......|..m..p..|
00000110 f5 c5 bb e3 c5 27 ef ef 77 fc 7b 5c 6b fd 9f 74 |.....'..w.{\k..t|
00000120 9d fb 6b b9 d3 7d 7b 3f 2a e9 b5 f3 cd 6b cf b7 |..k..}{?*....k..|
00000130 e7 6a d6 d6 54 cb db e2 0d 96 d4 0c 7e 94 b7 2d |.j..T.......~..-|
00000140 c4 ef 49 ad f1 20 cd 30 7b 5c ff 99 96 b6 d6 f5 |..I.. .0{\......|
00000150 c5 b5 a0 e5 6e 20 6b ef 86 19 a4 e1 06 13 93 04 |....n k.........|
00000160 00 99 90 92 3e 23 e6 9f a8 ec 4f 53 73 37 fb bc |....>#....OSs7..|
00000170 11 5f 3c cc de eb 5b e0 f3 6e ef bd bc cb 97 70 |._<...[..n.....p|
00000180 03 92 48 07 ea 41 45 2c de 9f 02 1a f6 c8 c1 19 |..H..AE,........|
00000190 0f 19 1d 5d 22 a5 7a dc d6 99 f3 0f bd a7 76 04 |...]".z.......v.|
000001a0 eb 45 ce c9 63 26 3b de 40 0c 74 26 f2 14 27 f4 |.E..c&;.@.t&..'.|
000001b0 b8 43 90 a3 4c 15 50 00 f7 0b 00 00 04 d7 00 fe |.C..L.P.........|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 82 3e 00 00 fe |............>...|
000001d0 ff ff 05 fe ff ff 02 82 3e 00 83 85 e1 15 00 00 |........>.......|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
```

---

### Post by sprogmeister on 2011-05-08
I'm sorry I don't understand what you want me to do. I don't understand OP either. I am very grateful for the help and will provide the information, can you rephrase the request?

---

### Post by wilee-nilee on 2011-05-08
The script looks good I wanted to know what else is on the HD, and if we were dealing with a wubi install.

Can you use the classic desktop by choosing it at the login in window?

If you had a clean upgrade,(insert any error's you might have had but haven't shared) it may be just a need of a graphic driver?

Do you know which video card you have?

> **sprogmeister said:**
> I'm sorry I don't understand what you want me to do. I don't understand OP either. I am very grateful for the help and will provide the information, can you rephrase the request?

Not a problem, so I have reposted your script in a standard method, remove the original to shorten up the thread. You need at least a single letter in the scripts place to save the edit.

---

### Post by sprogmeister on 2011-05-08
I am sorry I do not know the graphics card I have, I think it is an NVidia.
When it boots up I get to the screen as it was before the upgrade, I just cannot access anything. I hope this answers your questions.

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> I am sorry I do not know the graphics card I have, I think it is an NVidia.
When it boots up I get to the screen as it was before the upgrade, I just cannot access anything. I hope this answers your questions.

Okay so lets get to the classic desktop, at the login screen after choosing your name, but before the password; look in the bottom panel, there is a button for choosing other then Ubuntu which is unity, try classic and/or the failsafe low graphic something like that, I don't remember every word lol.

If you get, in go to the menu-systems-administration-additional drivers...lok to see if any thing is there for install. 

You may need to run a 
sudo apt-get update
in the terminal to get the repositories linked with your setup to show availability.

You are doing fine here it is just getting to the needed facts.;)

---

### Post by sprogmeister on 2011-05-08
All the drivers are installed but the safe mode did not see the internet. I am rebooting it now to see if I can get in another way

---

### Post by sprogmeister on 2011-05-08
Just started the version I am having issues with and when I clicked on one of the icons on the new left hand bar something tried to start. It seems now that it is unresponsive again.

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> Just started the version I am having issues with and when I clicked on one of the icons on the new left hand bar something tried to start. It seems now that it is unresponsive again.

run in the terminal, copy and paste it if you want.
```
sudo apt-get update && sudo apt-get upgrade 
```

This will get you up to date, there may be something missing with the original upgrade

then in terminal, I'm assuming your getting to some thing with a mention of the side bar. crtl-alt-t brings up a terminal.
```
lspci
```

---

### Post by sprogmeister on 2011-05-08
I can't get into terminal on the version that is having dramas and in safe mode there is no intenet connection so I am unsure on what to do. Is there a shortcut I can try to start terminal with on the dodgey ubuntu? Or can I override the lack of wireless in safe mode?

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> I can't get into terminal on the version that is having dramas and in safe mode there is no intenet connection so I am unsure on what to do. Is there a shortcut I can try to start terminal with on the dodgey ubuntu? Or can I override the lack of wireless in safe mode?

You don't need a terminal to run the lspci command. Lets see that.

Sorry you need a terminal not internet access.

---

### Post by sprogmeister on 2011-05-08
I've got he terminal up and running and am typing on this computer. What do you need to know from the read out. The graphics card is Nvidia GeForce Go 7400.

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> I've got he terminal up and running and am typing on this computer. What do you need to know from the read out. The graphics card is Nvidia GeForce Go 7400.

Post the whole lspci command.

You also have a wireless problem the card for that will be listed, everything will be there for us too work with.

Can you get to the internet plugged in?

---

### Post by sprogmeister on 2011-05-08
Hot at the minute. I will have a play around and see if I can get it connected up. it may take a while. Is that okay?

---

### Post by wilee-nilee on 2011-05-08
> **sprogmeister said:**
> Hot at the minute. I will have a play around and see if I can get it connected up. it may take a while. Is that okay?

No problem, sorry if I was cold, I just got up and needed a little chill time.;)

Coffee cig, the regular wake up stuff.

---

### Post by sprogmeister on 2011-05-08
No worries it's almost 11 at night here

---

### Post by sprogmeister on 2011-05-09
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by sprogmeister on 2011-05-09
Thank you all for your time and patience, the problem is now resolved. Once I had got chroot correct, it was a case of hardwire into the router and update from the booted safe mode. All is working!!!!

---

### Post by wilee-nilee on 2011-05-09
> **sprogmeister said:**
> Thank you all for your time and patience, the problem is now resolved. Once I had got chroot correct, it was a case of hardwire into the router and update from the booted safe mode. All is working!!!!

That is great, I was not sure of the next step honestly.;)

---

### Post by sprogmeister on 2011-05-09
Wilee-Nilee many thanks!

---

