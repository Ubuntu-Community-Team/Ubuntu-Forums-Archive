---
title: "Grub sending me back to OS selection"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Nyl0n007 on 2011-01-31
When I boot my computer and come to the Grub OS screen and I choose

Vista, I cannot get into vista. The screen goes blank less than a
 
second and then sends me back to Grub to pick an os. I can get into

Ubuntu 10.10 though. I cannot get internet, as my Netgear WPN111 

wireless USB does not have the correct drivers for Ubuntu. Thanks 

for helping.


Edit: I have internet now with wired connection.

---

### Post by Nyl0n007 on 2011-01-31
bump

---

### Post by matt_symes on 2011-01-31
Hi

You could try reinstalling grub from a LiveCD.

Here's a howto

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Kind regards

---

### Post by Nyl0n007 on 2011-01-31
This did not work. I still cannot get into vista.

When I did the last step,

sudo update-grub

i got this:


Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done


I think my error is with the fourth one, the loader is on the wrong partition?

---

### Post by matt_symes on 2011-01-31
Hi

In my signature there is a boot info script. Run that from a liveCD/USB and post the results back here. The instructions are on the web page.

That will provide a lot more information about what may be happening.

Kind regards

---

### Post by rcayea on 2011-01-31
I must say Matt in the post above is a gem and I have used his script before. 

But, if you can boot into your Ubuntu box then try from synaptic to reinstall grub, that has worked for me, too. 

From the command line I do this: sudo apt-get install grub-pc --reinstall

---

### Post by uRock on 2011-01-31
After you get the grub mess fixed, you can get you Netgear USB working by installing the Linux Firmware Nonfree package with the following command.

I have the same model Netgear.

```
sudo apt-get install linux-firmware-nonfree
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175501&d=1289660118[/IMG]

---

### Post by matt_symes on 2011-01-31
Hi

> I must say Matt in the post above is a gem and I have used his script before. 

I must say i did not write this script. You are right. It is an excellent script.

Kind regards

---

### Post by Nyl0n007 on 2011-01-31
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1446207736 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8064.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,333,025,439 1,333,023,392   7 HPFS/NTFS
/dev/sda2       1,333,026,816 1,427,396,607    94,369,792  83 Linux
/dev/sda3       1,427,398,656 1,448,368,127    20,969,472  83 Linux
/dev/sda4       1,448,370,174 1,465,145,343    16,775,170   f W95 Ext d (LBA)
/dev/sda5       1,448,370,176 1,465,145,343    16,775,168  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,687,679    15,679,616   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d07d5e03-2f85-4d10-ba4b-8fcceb513102   ext3                                     
/dev/sda1        FC6285416285021E                       ntfs                                     
/dev/sda2        a8cf05b3-a5e5-4b25-aee3-32dfbe0f3e8c   ext3                                     
/dev/sda3        ad257132-d4f4-42a6-aaab-abd956dcb0fe   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9faa499c-e6ab-40c0-809b-bfb10c7061de   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1AB5-80B7                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ad257132-d4f4-42a6-aaab-abd956dcb0fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ad257132-d4f4-42a6-aaab-abd956dcb0fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ad257132-d4f4-42a6-aaab-abd956dcb0fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fc6285416285021e
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 740.4GB: boot/grub/core.img
 740.4GB: boot/grub/grub.cfg
 740.4GB: boot/initrd.img-2.6.35-22-generic
 740.4GB: boot/vmlinuz-2.6.35-22-generic
 740.4GB: initrd.img
 740.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f8 00 00 00 00 00  |........>.......|
00000020  80 40 ef 00 b8 3b 00 00  00 00 00 00 02 00 00 00  |.@...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 b7 80 b5 1a 20  20 20 20 20 20 20 20 20  |..)....         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 60 40 16 00  66 ba 00 00 00 00 bb 00  |}.f.`@..f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by matt_symes on 2011-02-02
Hi

Sorry for the late repy. I have been rather busy.

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1446207736 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
```

This seems to be the main problem. The boot sector for your vista partition has been overwritten by Grub but grub has no config files. 
Grub in the MBR looks fine so you want to remove grub from the boot sector of sda1.

What you need to do is repair the windows boot sector of this partition. 

Have a read of this microsoft article  

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

It explains how to use bootrec.exe to fix boot problems. You want the /FixBoot option.

If you have any questions please post them first before attempting any fix.

EDIT: I will double check for any other problems from your boot info file later when i get a bit more time to ensure i have not missed anything.

Kind regards

---

