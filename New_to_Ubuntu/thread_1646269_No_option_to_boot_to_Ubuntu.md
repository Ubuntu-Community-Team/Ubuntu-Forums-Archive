---
title: "No option to boot to Ubuntu"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by ohrange on 2010-12-15
Hi,
I tried to install Ubuntu 10.10 as a dual boot with Vista but it clearly hasn't worked properly (not too surprising given by complete Ubuntu newbie status). Here's what I did:

I shrank the vista partition and made about 30 gb of available space. Then I used the installer on the live CD to make a 2 gb swap partition and the rest into ext4. I specified the latter as the boot loader installation location. Then the installer ran and took forever getting updates so I left it running over night. It said "installing system" when I left it. In the morning the screen was covered in a repeating error message that I did not write down. When restarted the computer just boots to vista.

---

### Post by wilee-nilee on 2010-12-15
> **ohrange said:**
> Hi,
I tried to install Ubuntu 10.10 as a dual boot with Vista but it clearly hasn't worked properly (not too surprising given by complete Ubuntu newbie status). Here's what I did:

I shrank the vista partition and made about 30 gb of available space. Then I used the installer on the live CD to make a 2 gb swap partition and the rest into ext4. I specified the latter as the boot loader installation location. Then the installer ran and took forever getting updates so I left it running over night. It said "installing system" when I left it. In the morning the screen was covered in a repeating error message that I did not write down. When restarted the computer just boots to vista.

So the bootloader should of gone to the mbr do this so we can find what is where. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by ohrange on 2010-12-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    15,292,415    15,290,368  27 Hidden HPFS/NTFS
/dev/sda2    *     15,292,416   174,772,207   159,479,792   7 HPFS/NTFS
/dev/sda3         174,772,222   234,440,703    59,668,482   5 Extended
/dev/sda5         174,772,224   229,459,967    54,687,744  83 Linux
/dev/sda6         229,462,016   234,440,703     4,978,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2AB8B740B8B70979                       ntfs       SERVICEV002                   
/dev/sda2        EEA66B96A66B5DD9                       ntfs       SW_Preload                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5627e3b4-8030-4373-b82a-bbd6198a5be2   ext4                                     
/dev/sda6        71373553-7b3c-4021-b7a7-3022b2fa4a5b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5627e3b4-8030-4373-b82a-bbd6198a5be2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5627e3b4-8030-4373-b82a-bbd6198a5be2 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5627e3b4-8030-4373-b82a-bbd6198a5be2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2ab8b740b8b70979
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set eea66b96a66b5dd9
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
UUID=5627e3b4-8030-4373-b82a-bbd6198a5be2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=71373553-7b3c-4021-b7a7-3022b2fa4a5b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 100.9GB: boot/grub/core.img
  91.8GB: boot/grub/grub.cfg
  90.5GB: boot/initrd.img-2.6.35-22-generic
 100.9GB: boot/vmlinuz-2.6.35-22-generic
  90.5GB: initrd.img
 100.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  48 30 4c 30 50 30 54 30  58 30 5c 30 60 30 64 30  |H0L0P0T0X0\0`0d0|
00000010  68 30 6c 30 70 30 74 30  78 30 7c 30 80 30 84 30  |h0l0p0t0x0|0.0.0|
00000020  88 30 8c 30 90 30 94 30  98 30 9c 30 a0 30 30 31  |.0.0.0.0.0.0.001|
00000030  34 31 4c 31 50 31 54 31  58 31 5c 31 60 31 64 31  |41L1P1T1X1\1`1d1|
00000040  68 31 6c 31 70 31 74 31  78 31 7c 31 80 31 84 31  |h1l1p1t1x1|1.1.1|
00000050  88 31 8c 31 90 31 94 31  98 31 9c 31 a0 31 a4 31  |.1.1.1.1.1.1.1.1|
00000060  a8 31 ac 31 b0 31 b4 31  b8 31 c4 31 c8 31 cc 31  |.1.1.1.1.1.1.1.1|
00000070  d0 31 d4 31 d8 31 dc 31  e0 31 e4 31 e8 31 ec 31  |.1.1.1.1.1.1.1.1|
00000080  f0 31 f4 31 f8 31 fc 31  00 32 04 32 08 32 0c 32  |.1.1.1.1.2.2.2.2|
00000090  10 32 14 32 18 32 1c 32  20 32 24 32 28 32 2c 32  |.2.2.2.2 2$2(2,2|
000000a0  30 32 34 32 38 32 3c 32  40 32 44 32 48 32 4c 32  |024282<2@2D2H2L2|
000000b0  50 32 54 32 58 32 5c 32  60 32 64 32 68 32 6c 32  |P2T2X2\2`2d2h2l2|
000000c0  70 32 74 32 78 32 7c 32  80 32 84 32 88 32 8c 32  |p2t2x2|2.2.2.2.2|
000000d0  90 32 94 32 98 32 9c 32  a0 32 a4 32 a8 32 ac 32  |.2.2.2.2.2.2.2.2|
000000e0  b0 32 b4 32 b8 32 bc 32  c0 32 c4 32 c8 32 cc 32  |.2.2.2.2.2.2.2.2|
000000f0  d0 32 d4 32 d8 32 dc 32  e0 32 e4 32 e8 32 ec 32  |.2.2.2.2.2.2.2.2|
00000100  f0 32 f4 32 f8 32 fc 32  00 33 04 33 08 33 0c 33  |.2.2.2.2.3.3.3.3|
00000110  10 33 14 33 18 33 1c 33  20 33 24 33 28 33 2c 33  |.3.3.3.3 3$3(3,3|
00000120  30 33 34 33 38 33 3c 33  40 33 44 33 48 33 4c 33  |034383<3@3D3H3L3|
00000130  50 33 54 33 58 33 5c 33  60 33 64 33 68 33 6c 33  |P3T3X3\3`3d3h3l3|
00000140  70 33 74 33 78 33 7c 33  80 33 84 33 88 33 8c 33  |p3t3x3|3.3.3.3.3|
00000150  90 33 94 33 98 33 9c 33  a0 33 a4 33 a8 33 ac 33  |.3.3.3.3.3.3.3.3|
00000160  b0 33 b4 33 b8 33 bc 33  c0 33 c4 33 c8 33 cc 33  |.3.3.3.3.3.3.3.3|
00000170  d0 33 d4 33 d8 33 dc 33  e0 33 e4 33 e8 33 ec 33  |.3.3.3.3.3.3.3.3|
00000180  f0 33 f4 33 f8 33 fc 33  18 34 1c 34 20 34 24 34  |.3.3.3.3.4.4 4$4|
00000190  28 34 2c 34 30 34 34 34  38 34 3c 34 40 34 44 34  |(4,4044484<4@4D4|
000001a0  48 34 4c 34 50 34 54 34  58 34 5c 34 60 34 64 34  |H4L4P4T4X4\4`4d4|
000001b0  68 34 6c 34 70 34 74 34  78 34 7c 34 80 34 00 ef  |h4l4p4t4x4|4.4..|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 78 42 03 00 ef  |...........xB...|
000001d0  ff ff 05 ef ff ff 82 7c  42 03 80 fb 4b 00 00 00  |.......|B...K...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-12-15
So we are going to install the grub bootloader to the mbr boot a live CD of the same Ubuntu distro and run these two commnands. Then reboot to the grub menu choose the Ubuntu install and run the 3rd command.
```
sudo mount /dev/sda5 /mnt
```

then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and in the Ubuntu install run.

```
sudo update-grub
```

---

### Post by ohrange on 2010-12-15
Thank you! :D

---

### Post by wilee-nilee on 2010-12-15
> **ohrange said:**
> Thank you! :D

Figured that would work even with the error messages, got the answers from here.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Have a happy celebration of any sort in the time coming.;)

---

