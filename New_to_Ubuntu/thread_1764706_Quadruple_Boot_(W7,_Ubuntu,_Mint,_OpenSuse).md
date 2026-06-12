---
title: "Quadruple Boot (W7, Ubuntu, Mint, OpenSuse)"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by CyberNerdz on 2011-05-22
I have been generally happy with Ubuntu 11.04 and continued evaluating different distros this past few weeks to determine which I will be moving my other desktops to. I started with Ubuntu (Wubi) install , which was on the same partition of my laptop's 750GB drive that also ran Windows 7 Ultimate 64.  I was urged this weekend to try other distros and see how I would like it. The third OS I installed was OpenSuSe 11.4 on a separate newly created partition. This went smoothly as it installed Grub 1.5 loader that gave me the choice to go to my Windows bootloader with the option to boot to Windows  7 or Ubuntu 11.04:

[IMG]http://cybernerdz.biz/images/OpenSuSe_grub15.jpg[/IMG]

Pushing my luck even further, I wanted to install Mint on a new partition. After shrinking my Windows partition I  was able to gain another 20GB partition for my Linux Mint 10  install.

Now the problem. I'm suspecting while installing Mint that I should have not have chosen the Windows loader as one of the options during install. What is happening now when I chose Windows 7 or Ubuntu 11.04 from OpenSuSe Grub 1.5, it takes me to GNU Grub 1.98+20100804. This menu gives me options to boot to Mint, OpenSuse or Windows. When I choose Windows it just loops back to the same screen after a few seconds.

[IMG]http://cybernerdz.biz/images/Mint_grub198.jpg[/IMG]

I went to press "e" for edit on the Windows to see the settings:

```
instmod part_msdos
insmod ntfs
set root='(hd0.msdos1)'
search - - nofloppy - - fs-uuid - - set 880cfd860cfd6f94
chainloader +1
```

Choosing Linux Mint is now giving me an error and wont let me boot to Mint anymore. I get this:

```
Gave up waiting for root device
- Boot args (cat /proc/cmdline)
   - check rootdelay
   - Check root= 
- Missing modules ( cat /proc/modules;ls/dev)
Alert! /dev/disk/by-uuid/alff754d-a4343-8b7b-c0c87e755558 does not exist
Dropping Shell!

(init tramfs)
```[B]

From OpenSuse:[/B]
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
rootfs                 15G  4.0G   11G  29% /
devtmpfs              1.8G  196K  1.8G   1% /dev
tmpfs                 1.9G  2.7M  1.9G   1% /dev/shm
/dev/sda6              15G  4.0G   11G  29% /
/dev/sda7             8.1G  1.3G  6.5G  16% /home
/dev/sda1             660G  392G  268G  60% /windows/C
```
I know this is not the best way have a quad-boot OS and quite honestly I blame myself for not planning it more carefully. My question now is, is it possible to recover booting to my Windows bootloader and get a working menu between Windows and Ubuntu? 

Any help will be greatly appreciated and desperately needed.

---

### Post by rolnics on 2011-05-22
You're as bad as me....distro hoping! lol I've had my share of grub / booting problems as well.

First lets get some more info [this thread]("http://ubuntuforums.org/showthread.php?t=1291280") should give us a starting point, post back the results from it.

---

### Post by CyberNerdz on 2011-05-22
Thanks Rolniks! Here's my result:

                ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 1436103552 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 8 for (,msdos8)/grub. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /menu.lst /grldr /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /grldr /grldr.mbr 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/home.disk /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,382,929,152 1,382,929,090   7 NTFS / exFAT / HPFS
/dev/sda2    *  1,382,932,478 1,445,617,663    62,685,186   f W95 Extended (LBA)
/dev/sda5       1,382,932,480 1,387,149,311     4,216,832  82 Linux swap / Solaris
/dev/sda6       1,387,151,360 1,418,700,799    31,549,440  83 Linux
/dev/sda7       1,418,702,848 1,435,829,801    17,126,954  83 Linux
/dev/sda8       1,435,830,272 1,439,651,839     3,821,568  83 Linux
/dev/sda9       1,439,653,888 1,445,617,663     5,963,776  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        880CFD860CFD6F94                       ntfs       
/dev/sda5        a2799c7d-f7b4-410c-bda1-5b7bcad77a6e   swap       
/dev/sda6        91f24c6a-c1f6-4e80-aec9-a941ede124b9   ext4       
/dev/sda7        91f62472-6f6e-4537-8636-712a3936284d   ext4       
/dev/sda8        bb4f39ef-5490-4543-92b1-cc35bdbd0edb   ext4       
/dev/sda9        a1ff754d-a443-43b3-8b7b-c0c87e755556   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered)
/dev/sda7        /home                    ext4       (rw,relatime,user_xattr,acl,barrier=1,stripe=1,data=ordered)


================================ sda1/menu.lst: ================================

--------------------------------------------------------------------------------
hiddenmenu 
timeout 0 
title openSUSE 11.4 installer (LOCAL) 
find --set-root /openSUSE_hitme.txt
kernel /openSUSE/linux devfs=mount,dall ramdisk_size=65536  lang=en splash=silent vga=0x31A
initrd /openSUSE/initrd
--------------------------------------------------------------------------------

========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 880CFD860CFD6F94
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 880CFD860CFD6F94
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=880CFD860CFD6F94 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 880CFD860CFD6F94
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=880CFD860CFD6F94 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 880CFD860CFD6F94
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

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/host/ubuntu/disks/home.disk    /home    ext3    loop    0    0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  12.162113190 = 13.058969600   boot/grub/grub.cfg                             1
   2.048816681 = 2.199900160    boot/initrd.img-2.6.38-8-generic               2
  12.160465240 = 13.057200128   boot/vmlinuz-2.6.38-8-generic                  1
   2.048816681 = 2.199900160    initrd.img                                     2
  12.160465240 = 13.057200128   vmlinuz                                        1

=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Sat May 21 04:39:19 PDT 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.4 - 2.6.37.6-0.5
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.37.6-0.5-desktop root=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part6 devfs=mount,dall resume=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part5 splash=silent quiet showopts vga=0x318 nomodeset
    initrd /boot/initrd-2.6.37.6-0.5-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.37.6-0.5
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.37.6-0.5-desktop root=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part6 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31A
    initrd /boot/initrd-2.6.37.6-0.5-desktop

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows 7 Ultimate OR Ubuntu 11.04
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part6 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part7 /home                ext4       acl,user_xattr        1 2
/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 671.621688843 = 721.148297216  boot/grub/menu.lst                             1
 671.598365784 = 721.123254272  boot/grub/stage2                               2
 662.414062500 = 711.261683712  boot/initrd                                    4
 662.414062500 = 711.261683712  boot/initrd-2.6.37.6-0.5-default               4
 662.370021820 = 711.214395392  boot/initrd-2.6.37.6-0.5-desktop               1
 671.886520386 = 721.432657920  boot/vmlinuz                                   1
 671.886520386 = 721.432657920  boot/vmlinuz-2.6.37.6-0.5-default              1
 671.857574463 = 721.401577472  boot/vmlinuz-2.6.37.6-0.5-desktop              1

============================= sda8/grub/grub.cfg: ==============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set a1ff754d-a443-43b3-8b7b-c0c87e755556
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
set locale_dir=($root)/grub/locale
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
insmod png
if background_image /grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda8)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
    linux    /vmlinuz-2.6.35-22-generic root=UUID=a1ff754d-a443-43b3-8b7b-c0c87e755556 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda8) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=a1ff754d-a443-43b3-8b7b-c0c87e755556 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set bb4f39ef-5490-4543-92b1-cc35bdbd0edb
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 880cfd860cfd6f94
    chainloader +1
}
menuentry "openSUSE 11.4 - 2.6.37.6-0.5 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 91f24c6a-c1f6-4e80-aec9-a941ede124b9
    linux /boot/vmlinuz-2.6.37.6-0.5-desktop root=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part6 devfs=mount,dall resume=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part5 splash=silent quiet showopts vga=0x318 nomodeset
    initrd /boot/initrd-2.6.37.6-0.5-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.5 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 91f24c6a-c1f6-4e80-aec9-a941ede124b9
    linux /boot/vmlinuz-2.6.37.6-0.5-desktop root=/dev/disk/by-id/ata-Hitachi_HTS547575A9E384_J2540054G7RNKE-part6 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31A
    initrd /boot/initrd-2.6.37.6-0.5-desktop
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

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 684.787559509 = 735.285043200  grub/core.img                                  1
 684.788093567 = 735.285616640  grub/grub.cfg                                  1
 684.819877625 = 735.319744512  initrd.img-2.6.35-22-generic                   1
 684.809703827 = 735.308820480  vmlinuz-2.6.35-22-generic                      1

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=a1ff754d-a443-43b3-8b7b-c0c87e755556 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda8 during installation
UUID=bb4f39ef-5490-4543-92b1-cc35bdbd0edb /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a2799c7d-f7b4-410c-bda1-5b7bcad77a6e none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically


```

FYI: I can only boot to SUSE right now

---

### Post by rolnics on 2011-05-22
Hmmm, thought I had the answer for you, but looking at it again, I don't.

I can see now, why openSUSE is booting, but I don't know why its not booting to windows for you, as doing some googling it looks right.

Don't lose hope though, have you posted anything about this on the openSUSE forums?

---

### Post by CyberNerdz on 2011-05-22
Yes, I have also posted on opensuse forum but its not looking good...

I added boot_info result in my post as well and this was the last response I got:

> I don't understand this sufficiently to answer one way or the other.
The writer of the script may be able help (@please_try_again)

Have you tired supergrubdisk
It may help you boot what you cannot currently.                 
Mint forum has total no support... :(

Correct me if I'm wrong but how I'm understanding the problem is that the initial bootloader is run by openSUSE's Grub 1.5, then when Windows is selected it goes to Mint's Grub 1.93. Since Mint's Grub took over Wubi's Grub, selecting Windows from it just loops back. Would this be a correct assumption?

Would removing Mint and its bootloader fix the problem? How do I restore Wubi's Grub in place of Mint's ?

---

### Post by CyberNerdz on 2011-05-30
One thing I look at any distros is the support it gets from the community. Although ubuntu is probably the most popular one for now, support is way below average compared to opensuse and fedora.

Good luck to the ubuntu devs and its community but this distro is out of my choices.

---

### Post by bcbc on 2011-05-31
You installed grub2 to the windows partition boot sector. Which is required to boot windows. You can use testdisk to restore the bootsector from the backup (if it exists).
Otherwise you'd need to get a Windows repair cd or install DVD and repair/rebuild it manually from a repair prompt.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

PS if you use the windows repair, note there is a typo in that link - it should be "bootrec /fixboot" (not bootrect /fixboot)

---

### Post by CyberNerdz on 2011-05-31
Thanks for the response but this issue has already been resolved by another community. My experience with ubuntu support has not been very reliable. Most of the time I don't get any reply but if your interested how this issue was resolve, [click here]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/460252-quadruple-boot-w7-ubuntu-mint-opensuse.html"). 

Thanks anyway.

---

### Post by bcbc on 2011-05-31
> **CyberNerdz said:**
> Thanks for the response but this issue has already been resolved by another community. My experience with ubuntu support has not been very reliable. Most of the time I don't get any reply but if your interested how this issue was resolve, [click here]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/460252-quadruple-boot-w7-ubuntu-mint-opensuse.html"). 

Thanks anyway.

Well that was quite a read. There was a time when this problem was very common on this forum, and you would have had a whole bunch of quick responses pointing out the problem - that was when 10.04 was released and grub2 allowed you to install it to the Windows partition boot sector. Fortunately grub2 (Ubuntu's version anyway) won't allow that anymore - I guess Mint doesn't have the latest version.

Anyway - glad you got it resolved.

---

