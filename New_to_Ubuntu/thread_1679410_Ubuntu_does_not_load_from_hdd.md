---
title: "Ubuntu does not load from hdd"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by newblackgold on 2011-02-01
The computer lost power and now it won't boot into Ubuntu. It stays stuck at "Loading Operating System..." with a blinking cursur, if left on it's own. It will boot from a usb stick using the "test" option, but will not boot from the hard drive. The screen goes black, then it goes back to the usb menu. Fsck was run through Slax and some errors were found and repaired. The hard drives of the system are available and files seem intact. This is a Ubuntu-only machine.
 
I imagine this is something related to grub but I'm pretty new with Ubuntu so I really don't know.

---

### Post by Hedgehog1 on 2011-02-01
newblackgold,

Did you computer lose power while it was installing Ubuntu?  Or did it lose power as you were running Ubuntu?

---

### Post by newblackgold on 2011-02-01
Running.  It's been up and running for about a month now.

Also, I don't know if this is related, but upon doing a grub-install, it complains with

/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..

Also, this system has (what I believe to be) a hardware RAID, although it does not boot from there.

---

### Post by Hedgehog1 on 2011-02-01
Well, this helps.

So we know that it boots from the USB stick. That tells us that memory, CPU and video card are not the likely culprits.

So, next debugging question - when you boot from the USB stick, can you see your hard drive(s) at all?  This will tell us if you have a hardware issue with the drives or the controller.

---

### Post by newblackgold on 2011-02-01
Yes, all of the drives are mountable and the files are intact.

---

### Post by newblackgold on 2011-02-01
Here's the output of boot info script.  Don't know if it's relevant.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_chdfiibf

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

nvidia_chdfiibf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   140,009,471   140,007,424  83 Linux
/dev/sda2         140,011,518   145,225,727     5,214,210   5 Extended
/dev/sda5         140,011,520   145,225,727     5,214,208  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,049,471 3,907,047,424  83 Linux

/dev/sdb1 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1001 MB, 1001914368 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1956864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     1,956,863     1,956,801   b W95 FAT32


Drive: nvidia_chdfiibf ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_chdfiibf: 2000.4 GB, 2000409591808 bytes
255 heads, 63 sectors/track, 243202 cylinders, total 3907049984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_chdfiibf1              2,048 3,907,049,471 3,907,047,424  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_chdfiibf1 7f2a9d93-df0c-4145-885f-ace7b7793045   ext4       storage                       
/dev/mapper/nvidia_chdfiibf: PTTYPE="dos" 
/dev/sda1        4389fd29-9253-4dd0-b353-9fae470426a8   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f3a74a2a-f9c6-4bba-aa15-93355f69c1bd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        82C8-CCC1                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd                                                nvidia_raid_member                               
error: /dev/sdb1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_chdfiibf
nvidia_chdfiibf1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=4389fd29-9253-4dd0-b353-9fae470426a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=4389fd29-9253-4dd0-b353-9fae470426a8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4389fd29-9253-4dd0-b353-9fae470426a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4389fd29-9253-4dd0-b353-9fae470426a8 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4389fd29-9253-4dd0-b353-9fae470426a8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b8e90b36-ff83-45a6-a932-b175fec52a99
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=b8e90b36-ff83-45a6-a932-b175fec52a99 ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b8e90b36-ff83-45a6-a932-b175fec52a99
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=b8e90b36-ff83-45a6-a932-b175fec52a99 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b8e90b36-ff83-45a6-a932-b175fec52a99
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e90b36-ff83-45a6-a932-b175fec52a99 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b8e90b36-ff83-45a6-a932-b175fec52a99
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e90b36-ff83-45a6-a932-b175fec52a99 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f3a74a2a-f9c6-4bba-aa15-93355f69c1bd none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  13.1GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-22-generic
   1.8GB: boot/initrd.img-2.6.35-24-generic
  25.9GB: boot/vmlinuz-2.6.35-22-generic
  25.9GB: boot/vmlinuz-2.6.35-24-generic
   1.8GB: initrd.img
   1.1GB: initrd.img.old
  25.9GB: vmlinuz
  25.9GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 22 11  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 db 1d 00 6f 07 00 00  00 00 00 00 02 00 00 00  |....o...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c1 cc c8 82 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 08 20 00 00  66 ba 00 00 00 00 bb 00  |}.f.. ..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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


=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
```As a note... there's a few shenanigans in the hard drive section.  It's something I never really figured out and left alone, and has worked fine in the past.  

```
Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb8ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8716    70003712   83  Linux
/dev/sda2            8716        9040     2607105    5  Extended
/dev/sda5            8716        9040     2607104   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058432

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243203  1953523712   83  Linux

Disk /dev/sdc: 1001 MB, 1001914368 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0059c18b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      978400+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 206, 21)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/dm-0: 2000.4 GB, 2000409591808 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00058432

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      243203  1953523712   83  Linux

Disk /dev/dm-1: 2000.4 GB, 2000408281088 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```Ubuntu is installed on sda and that is a 76 gig drive.  Beyond that is a 2 tb RAID.  I don't know why it lists so much stuff, and three 1 tb drives?  There's only 2 physical drives.  I remember having problems partitioning this RAID through Disk Utility and I used GParted and it worked there.

Anyway I don't know if it's relevant to my boot problem but I figured I would mention it.

---

### Post by Hedgehog1 on 2011-02-01
This is good news.  Your data is still there.  In this case, I think the lost power only contributed to the situation in that it forced you to reboot.

I think that your error message from GRUB is relevant:

"/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track."

This is looking like the boot sector is damaged (by software) and needs to be repaired.

This make this issue annoying, but not a disaster.

Here is a thread with all that GRUB does: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

I need to take a look at it to see what option you need - but you may find it first (or other readers my speak up, too).

---

### Post by Hedgehog1 on 2011-02-01
I think section 13 is what you need: Reinstalling GRUB 2 from LiveCD 

You are using a USB stick rather than a CD, but the idea is still the same.

Give it a look-see.

---

### Post by newblackgold on 2011-02-01
This is the same output I have been getting:

```
sudo grub-install --root-directory=/mnt /dev/sda 
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```

Does not seem to fix the problem.

---

### Post by Hedgehog1 on 2011-02-01
Does the computer boot from the hard drive after doing this (even though we are getting the ugly error message)?

If not, the next step is a little more difficult - that would be to purge and reinstall grub:  [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

This has reached the limits of what I have done using GRUB.  If this does not do it, I am out of ideas.

---

### Post by newblackgold on 2011-02-01
Neither solution solved the problem.  In the process of the purge and install of grub, that same error message about sector 33 showed up, although the purge completed without incident.

---

### Post by newblackgold on 2011-02-01
Well, I'm out of ideas.  It seems like such a simple fix?  If only I knew what to do.  Perhaps there is a better section of the forum for this to go under, if a moderator could move it?  Or should I repost it?

---

### Post by alphacrucis2 on 2011-02-01
> **newblackgold said:**
> Well, I'm out of ideas.  It seems like such a simple fix?  If only I knew what to do.  Perhaps there is a better section of the forum for this to go under, if a moderator could move it?  Or should I repost it?

[http://ubuntuforums.org/archive/index.php/t-1605076.html]("http://ubuntuforums.org/archive/index.php/t-1605076.html")

Maybe that thread will help

---

### Post by newblackgold on 2011-02-01
It did, a little.  A previous Photoshop install from years ago was causing that error, I don't know if it was the cause of my boot problem, though.  Here's my post on the other thread:
 
> Well, I "fixed" it.  Did a low level format with this free product:  [http://www.killdisk.com/](http://www.killdisk.com/)
 
Made sure to disconnect my RAID just to make sure I didn't accidentally select it!  Heh.  Went smoothly and reinstalled Ubuntu and all is well.  I spent quite a few hours already on this... could not justify spending more when it would take far less time just to reconfigure a fresh system.
 
This is why I never store important data on the same physical as the OS!  Heh  :)]

---

### Post by Hedgehog1 on 2011-02-02
newblackgold,

I was pondering your problem as I drove home from the office today.

If your system is still not loading off the hard drive (and everything seems to work when booting from the USB stick), I wonder if the kernel is damaged.

If you have been running at least a month (I think you have) you should have 2 kernels on you system thanks to a recent update.

If you would, please force Grub 2 to show the menu on boot up by holding down the Shift key while Grub is starting during a reboot.

If the grub menu shows you two Linux kernels, please arrow down to the older version and boot from that.

If you can boot from the older kernel, that tells us that the newer kernel was being rebuilt when you lost power.

Let me know what you find...

---

### Post by newblackgold on 2011-02-02
Well, I formatted the drive so I won't know for sure what the origional problem was, but I did try the hold-shift trick and it did not force grub to load.  The system seemed to hang immediatly as it tried to load an OS, and with the flexnet error, I really began to question the MBR itself.  It's an older drive.  It's possible it's starting to go out, or maybe it just lost power at a really bad time.

---

### Post by sydbat on 2011-02-02
> **newblackgold said:**
> Well, I formatted the drive so I won't know for sure what the origional problem was, but I did try the hold-shift trick and it did not force grub to load.  The system seemed to hang immediatly as it tried to load an OS, and with the flexnet error, I really began to question the MBR itself.  It's an older drive.  It's possible it's starting to go out, or maybe it just lost power at a really bad time.After reading through this thread (and the one newblackgold also posted in / linked to) I have done a bit of research and found that this "flexnet" garbage is basically a rootkit from an Adobe product. Nice, eh?

What I also found was, the only way to remove it from an existing drive is to do a full, low-level format that basically zero's the entire drive, including those 'bits' outside partitions (like the MBR).

If the format does not work, I suggest getting a new HDD and starting anew.

---

### Post by Hedgehog1 on 2011-02-02
> **newblackgold said:**
> Well, I formatted the drive so I won't know for sure what the origional problem was, but I did try the hold-shift trick and it did not force grub to load. The system seemed to hang immediatly as it tried to load an OS, and with the flexnet error, I really began to question the MBR itself. It's an older drive. It's possible it's starting to go out, or maybe it just lost power at a really bad time.
 
Well - sorry we could not solve it for you without reformatting the drive.
 
I was a good learning experince for me.  The adode damage to the MBR is really annoying, too.

---

### Post by newblackgold on 2011-02-03
I asked a freind about this after the fact and he seemed convinced it was hard drive failure, since a simple hard shut off could not damage the MBR unless it was being written at that exact moment, which really could not happen since I was not using the computer at the time and it would not have had permission to do so.
 
It's hard to say what was wrong, but it's easy to point fingers at Adobe!

---

### Post by sydbat on 2011-02-03
> **newblackgold said:**
> I asked a freind about this after the fact and he seemed convinced it was hard drive failure, since a simple hard shut off could not damage the MBR unless it was being written at that exact moment, which really could not happen since I was not using the computer at the time and it would not have had permission to do so.
 
It's hard to say what was wrong, but **it's easy to point fingers at Adobe**!Yes, it is...especially when the "flexnet" error is specific to an Adobe rootkit.

As for your HDD dying, as you have fully formatted the disc and installed a fresh copy of Ubuntu, only time will tell. Make sure you do regular backups and keep an eye on how your computer performs. I imagine you will have little trouble from now on.

---

### Post by newblackgold on 2011-02-07
I apparently lost power (to the house) as the clocks are flashing, and I go to the newly formatted linux box, try to turn it on, and it does the same problem, where it hangs prior to grub loading.
 
Now I really wonder.  It's not like you can't just restart the machine.  My ideas are, for one, I HAVE allowed it to download all ubuntu updates after the format.  Perhaps I shoulden't.  Second, there may be a motherboard problem where a bios setting and/or update can fix.
 
For now though I just won't update ubuntu, maybe give it a week, then unplug it without shutting down and see what happens, heh.

---

### Post by sydbat on 2011-02-07
> **newblackgold said:**
> I apparently lost power (to the house) as the clocks are flashing, and I go to the newly formatted linux box, try to turn it on, and it does the same problem, where it hangs prior to grub loading.
 
Now I really wonder.  It's not like you can't just restart the machine.  My ideas are, for one, I HAVE allowed it to download all ubuntu updates after the format.  Perhaps I shoulden't.  Second, there may be a motherboard problem where a bios setting and/or update can fix.
 
For now though I just won't update ubuntu, maybe give it a week, then unplug it without shutting down and see what happens, heh.Do you have your computer plugged into a surge protection unit?

If not, every time your home losses power, it is likely creating a power surge that is destroying your electronics.

If you do have surge protection, is it rated at a [high enough level]("http://electronics.howstuffworks.com/surge-protector5.htm")?

My quick thoughts - with all the power outages going on (you mention a few earlier in the thread), I imagine that your computer is getting the snot kicked out of it all the time. If you have left it running during these power outages, your file system could be corrupted, along with motherboard, CPU, RAM, HDD, other component damage.

---

### Post by newblackgold on 2011-02-07
It is protected by a surge protector, but that doesn't really matter here.  Surge protectors only (partially) protect against large surges (lightning) and they do little or nothing against everyday wobbles in the power line.  At least, I'm not going to pay more than $5 for surge protection for computer with parts that cost $140.
 
Very few surge protectors reliably protect against lightning, and if it doesn't, what's the point in having one?  Battery backup is the best option, power goes through the battery as a result the battery always gets nuked.  Better is that it absorbs voltage fluctuations as well.  Brownouts are much more dangerous than blackouts for any electrical device, and surge protectors do nothing against brownouts.
 
I don't claim to be an electrical engineer, but I beleive surge protectors to be somewhat of a fluke object.  To me it's nothing more than "a cord with more plugs on it."  It has to be a battery backup or a line cleaner type to be of any use, and those cost $100-$150 for either at the least, both of which lose their effectiveness as they get old.
 
My TV uses a line cleaner.  If you plug a large draw device into the same wall plug, say a dehumidafier, every time it turns on or off you get distortion on the screen and speakers, which is bad.  Plug it into a surge protector and nothing changes.  A battery backup or a line conditioner, and problem solved.
 
The power supply insulates the computer from power fluctuations as it has a range of input voltage, but a rather stable output voltage, unless it's poor quality or broken.  Any computer device is like this, like a TV, but a computer power supply is much cheaper and easier to replace, and um, less costly than a surge protector which can protect it.
 
I don't think power has anything to do with it, but regardless, I have computers much older than this one uneffected by it.  I've done file system checks though slax and it claims there is no file system damage.  I mean, not to bash linux or anything, but all the ~windows~ computers turn back on with no problem...
 
So.  I highly doubt it is related to power.  You can't say an operating system is ~so~ unstable that if you turn it off without a boot down ~once~ it is destroyed.  It has to be something related to the boot process.
 
Thing is though, it's come back from a hard shut off before with no problems, so what's the difference?  It must be update related.

---

### Post by sydbat on 2011-02-07
> **newblackgold said:**
> It is protected by a surge protector, but that doesn't really matter here.  Surge protectors only (partially) protect against large surges (lightning) and they do little or nothing against everyday wobbles in the power line.  At least, I'm not going to pay more than $5 for surge protection for computer with parts that cost $140.
 
Very few surge protectors reliably protect against lightning, and if it doesn't, what's the point in having one?  Battery backup is the best option, power goes through the battery as a result the battery always gets nuked.  Better is that it absorbs voltage fluctuations as well.  Brownouts are much more dangerous than blackouts for any electrical device, and surge protectors do nothing against brownouts.
 
I don't claim to be an electrical engineer, but I beleive surge protectors to be somewhat of a fluke object.  To me it's nothing more than "a cord with more plugs on it."  It has to be a battery backup or a line cleaner type to be of any use, and those cost $100-$150 for either at the least, both of which lose their effectiveness as they get old.
 
My TV uses a line cleaner.  If you plug a large draw device into the same wall plug, say a dehumidafier, every time it turns on or off you get distortion on the screen and speakers, which is bad.  Plug it into a surge protector and nothing changes.  A battery backup or a line conditioner, and problem solved.
 
The power supply insulates the computer from power fluctuations as it has a range of input voltage, but a rather stable output voltage, unless it's poor quality or broken.  Any computer device is like this, like a TV, but a computer power supply is much cheaper and easier to replace, and um, less costly than a surge protector which can protect it.
 
I don't think power has anything to do with it, but regardless, I have computers much older than this one uneffected by it.  I've done file system checks though slax and it claims there is no file system damage.  I mean, not to bash linux or anything, but all the ~windows~ computers turn back on with no problem...
 
So.  I highly doubt it is related to power.  You can't say an operating system is ~so~ unstable that if you turn it off without a boot down ~once~ it is destroyed.  It has to be something related to the boot process.
 
Thing is though, it's come back from a hard shut off before with no problems, so what's the difference?  It must be update related.Thank you for all the extra info. It would seem that power, in your case, is not the issue.

That said, it could be failing hardware or, as you suspect, an update borked something.

If it was an update, AND you can get Ubuntu to boot, go into Synaptic and check the "History" of updates. From there, you should be able to find the ones around the time your problems started and then remove them.

---

