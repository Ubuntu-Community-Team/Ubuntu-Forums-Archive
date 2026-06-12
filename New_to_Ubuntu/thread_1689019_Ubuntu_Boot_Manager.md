---
title: "Ubuntu Boot Manager"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Velinsky on 2011-02-16
Hi all!
I have a problem - on my HDD there were Win7 on C and WinXP on D and E was the additional space. 
I wanted to isntall Ubuntu using the first partition (sda1) previosly used by Win7. The installer checked that I have Win7 installed, but didn't mention WinXP. So, now I have Ubuntu installed as a primary system and other two NTFS drives (first one for WinXP and the second one for additional space). My question is: how to configure Ubuntu because I want to have a boot manager while loading to choose the appropriate os (WinXP or Ubuntu). Any help will be highly appreciated. Thanks in advance!

---

### Post by Eternal_Light on 2011-02-16
So now your computer boots you on ubuntu by default?

When on ubuntu get a terminal up and type the following stuff in there:

sudo update-grub

This should show on the terminal things like 
Ubuntu system found
Windows XP found 

or something similar.


After you do that try doing a reboot. If you still dont get a boot selection screen try restarting and after the bios launches press shift and keep it down. This should bring the bootloader on the screen.

---

### Post by fabricator4 on 2011-02-16
In a terminal, try:

> 
sudo update-grub


and see if it picks up the XP partition

Chris

---

### Post by Velinsky on 2011-02-16
Ok, I've done what you said but nothing happens. It didn't found WinXP, just Ubuntu. After restarting the pc the boot manager also didn't load. So I pressed the shift key and the options were: Linux Ubuntu, Linux Ubuntu (recovery mode) and Test Memory.

I'm still confused...

---

### Post by philinux on 2011-02-16
> **Velinsky said:**
> Ok, I've done what you said but nothing happens. It didn't found WinXP, just Ubuntu. After restarting the pc the boot manager also didn't load. So I pressed the shift key and the options were: Linux Ubuntu, Linux Ubuntu (recovery mode) and Test Memory.

I'm still confused...

You'll need to run this bootinfoscript to see whats going on and for people to try and help.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Velinsky on 2011-02-16
Here is the result from the Bootinfo Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    86,767,064    86,767,002  83 Linux
/dev/sda2          86,767,126   133,741,124    46,973,999   f W95 Ext d (LBA)
/dev/sda5    *     86,767,128   133,741,124    46,973,997   7 HPFS/NTFS
/dev/sda3         133,741,125   625,137,344   491,396,220   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,903,794     3,903,732   b W95 FAT32
/dev/sdb2           3,903,795     3,903,857            63  21 Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1bac50b0-0b72-41a1-ba31-60f3b4b064c6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        01CB738C078B3390                       ntfs                                     
/dev/sda5        01CB738D1B515890                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        40BE-0B5E                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/01CB738C078B3390  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/01CB738D1B515890  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/40BE-0B5E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1bac50b0-0b72-41a1-ba31-60f3b4b064c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1bac50b0-0b72-41a1-ba31-60f3b4b064c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1bac50b0-0b72-41a1-ba31-60f3b4b064c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1bac50b0-0b72-41a1-ba31-60f3b4b064c6 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1bac50b0-0b72-41a1-ba31-60f3b4b064c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  21.8GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-25-generic
  13.1GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: boot/vmlinuz-2.6.35-25-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
  13.1GB: vmlinuz
  13.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  11 64 9d 6f 7d 1d 11 8d  7d 97 43 ad 27 28 18 e4  |.d.o}...}.C.'(..|
00000010  06 6a 88 3c d1 b3 d4 8a  2d a4 61 e3 6d 7c 23 fe  |.j.<....-.a.m|#.|
00000020  a9 45 85 91 da 9d bc 85  19 9e 93 32 03 35 fd 51  |.E.........2.5.Q|
00000030  be 0e 4b 74 cf 49 4e 08  dc 66 dd 7c 1d d9 b1 63  |..Kt.IN..f.|...c|
00000040  4e 72 48 68 17 a7 4e 7f  3f 27 69 32 1f cd ef 64  |NrHh..N.?'i2...d|
00000050  48 4c 1e 5d ca f7 04 fe  77 4f 70 df 89 ae 71 f0  |HL.]....wOp...q.|
00000060  c6 bb 78 8c c2 83 63 14  e4 74 0a 33 e7 24 fb f2  |..x...c..t.3.$..|
00000070  f6 31 36 b3 e7 24 c7 90  94 63 04 d8 8b df 48 35  |.16..$...c....H5|
00000080  46 d1 64 b7 cf 5d a2 01  19 f7 c6 d7 85 4b 78 a2  |F.d..].......Kx.|
00000090  5f d9 89 4a c3 ee 8e 60  80 fd f3 a4 db ec aa 29  |_..J...`.......)|
000000a0  26 36 b8 1d 37 7f c3 37  52 2e e2 4c 73 3a 51 d4  |&6..7..7R..Ls:Q.|
000000b0  7f 7d 44 78 81 27 fa 84  4d a1 d1 de 8e 6c 55 30  |.}Dx.'..M....lU0|
000000c0  e9 4e 3a 28 2d e7 99 ad  cd 19 d4 d4 a4 a9 b5 d0  |.N:(-...........|
000000d0  0f d8 bf bd 41 d6 7b 1a  bf 93 aa f4 43 05 21 28  |....A.{.....C.!(|
000000e0  6a 9d 50 61 ec 95 6b 3c  47 79 23 09 99 ec c8 ad  |j.Pa..k<Gy#.....|
000000f0  1a 9b 7f 4d 1c 54 06 32  8f 13 6d a7 08 b2 fa 37  |...M.T.2..m....7|
00000100  84 d3 7c 4d 4c b0 52 4e  fa 76 fc 66 b3 ce 09 70  |..|ML.RN.v.f...p|
00000110  f3 a4 3f d9 1b 98 07 d2  60 77 81 96 5b 0b 96 8f  |..?.....`w..[...|
00000120  e8 e6 6a b7 b9 dc 3c d4  f9 81 f5 23 49 ca 7a cb  |..j...<....#I.z.|
00000130  fc be 9c f5 56 78 1a f8  cb 33 16 1a ed b2 4e 9c  |....Vx...3....N.|
00000140  20 0b 8d f4 6e 0f 65 ff  0f 0d fe b3 09 70 9e 75  | ...n.e......p.u|
00000150  37 9d 30 26 3c af 26 cc  43 3f 74 5e 3c d5 79 c9  |7.0&<.&.C?t^<.y.|
00000160  42 56 d9 36 45 df e3 90  f8 86 f8 0e 5a e8 f9 a0  |BV.6E.......Z...|
00000170  80 12 73 e7 61 6c dc 6e  ae 96 cd e9 e6 f9 4d 3d  |..s.al.n......M=|
00000180  1f 17 f6 7c 9a db c3 72  73 bf 20 36 66 5b 96 47  |...|...rs. 6f[.G|
00000190  ca ed 31 fe c2 58 4d e4  5a 78 ce a3 79 e5 59 47  |..1..XM.Zx..y.YG|
000001a0  78 86 3e 30 0a 39 64 d0  81 ae dc a7 f1 39 73 33  |x.>0.9d......9s3|
000001b0  15 95 a3 b4 aa f7 8c a6  bf 19 b8 1c f9 30 e7 dd  |.............0..|
000001c0  bc 13 75 67 96 14 71 a8  b4 fe 87 ce 73 f2 ca 0f  |..ug..q.....s...|
000001d0  9f 71 bd 3b cb ab 2c 2a  7a ff ec 48 6f 75 e8 26  |.q.;..,*z..Hou.&|
000001e0  20 71 97 27 0c 87 b1 4a  d6 8d 55 6e 9b ba 6e d6  | q.'...J..Un..n.|
000001f0  ba 82 5c e0 bd 24 70 0f  93 67 5b 39 92 94 2d ad  |..\..$p..g[9..-.|
00000200



```

---

### Post by Velinsky on 2011-02-16
Can anyone help me with this issue?

---

### Post by Eternal_Light on 2011-02-16
Ummm I see there that your windows XP exists, but unfortunately I don't know how to access it as I am a linux newbie myself :(

I would love to help but the only thing i can do is bump this and wish u good luck.
Remember google is our friend tho. It has helped me numerous times, although I had to spend a few hours looking through forums and wikis ^^

---

### Post by philinux on 2011-02-16
> **Velinsky said:**
> Can anyone help me with this issue?

I would reinstall grub.

From within linux.

```
sudo grub-install /dev/sda
```

```
sudo update-grub
```

---

### Post by jimwill on 2011-02-16
I'm not sure, but I think you can manually redirect the boot to /dev/sdb1

If not from normal boots grub menu then you might try the live cd.

This will not fix the problem, but would allow you to run winxp.

---

### Post by oldfred on 2011-02-16
You issue is with windows. When you removed win7 you also removed the boot files from XP as windows can only boot from one partition and per windows it has to be booted from a primary parition. If your XP was in a primary you could repair it with the XP disk but it will not repair a install in a logical partition. But with XP you can do all the repairs (except chkdsk) from Ubuntu.

How windows works:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

meierfra. Repair 2 windows installs to get each to be able to have grub entries XP & Win7 or Vista
[http://ubuntuforums.org/showthread.php?t=1362297](http://ubuntuforums.org/showthread.php?t=1362297)
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)

---

