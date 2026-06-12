---
title: "Dual Boot Goes Straight to Windows"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by ptrnrs on 2010-12-08
After several attempts* to install Ubuntu as a dual boot on a Windows Server 2003 PC, I found installation using the Ubuntu 10.10 Alternate CD to be the most (but not completely!) successful.

At the end of the installation process, I was promised that on reboot, I would be presented with the option to dual boot in either Windows or Ubuntu.  However, the PC booted striaght into Windows.

Assuming that the installation had failed, I reinstalled Ubuntu with the same consequence.

On booting the system using the Ubuntu 10.10 Install CD and using the "Try Ubuntu" option (I assume this is what's called "LiveCD"), I find that I have Ubuntu installed twice and neither of them boots.

Without success, I tried [this fix]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") which suggested:-```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdX
```Any other suggestions?

* I tried both Wubi and the Ubuntu Desktop Edition.

---

### Post by zvacet on 2010-12-08
I know it is trivial but did you replace sdXY with your partition number (in tutorial it is *sd**a1) ***and in second command sdX with sda if that is disc on with you want to install grub.

---

### Post by Rubi1200 on 2010-12-08
Hi and welcome to the forums :-)

Run the boot info script linked at the bottom of my post (instructions included).

Do this from a LiveCD and post the results back here to the forum.

Thanks.

---

### Post by ptrnrs on 2010-12-08
zvacet: Yes, I am stupid when it comes to Ubuntu but . . . ;)

Rubi1200: Thanks for your response.  You're clearly very active around here helping idiots like me (refer previous paragraph!) - thanks very much for your good work.

Attached is the requested file.

Minor point - the raw file just went above the (very conservative) file size limit on uploading TXT files (something like 20KB) to this forum,  I pruned a few unimportant bits to get it under the limit.  If many people need to upload similar files, maybe the limit could be set a little higher?

PS: Yes, I know I could have zipped it.

---

### Post by Quackers on 2010-12-08
With large files of code please use code tags - like this ( # in toolbar)

```
               Boot Info Script 0.55    dated February 15th, 2010                    

= Boot Info Summary: =

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/isw_dafaccaicg_RAID_Volume1

sda1: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

isw_dafaccaicg_RAID_Volume11: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

isw_dafaccaicg_RAID_Volume12: _

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

= Drive/Partition Info: =

Drive: sda _ _

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   126,512,624    85,546,875   7 HPFS/NTFS
/dev/sda3         126,513,150   231,389,183   104,876,034   5 Extended
/dev/sda5         162,451,456   231,389,183    68,937,728  83 Linux
/dev/sda6         126,513,152   160,856,063    34,342,912  83 Linux
/dev/sda7         160,858,112   162,449,407     1,591,296  82 Linux swap / Solaris


Drive: sdb _ _

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750   234,436,544   193,470,795   7 HPFS/NTFS


Drive: isw_dafaccaicg_RAID_Volume1 _ _

Disk /dev/mapper/isw_dafaccaicg_RAID_Volume1: 120.0 GB, 120033902592 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dafaccaicg_RAID_Volume11   *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/mapper/isw_dafaccaicg_RAID_Volume12         40,965,750   234,436,544   193,470,795   7 HPFS/NTFS


blkid -c /dev/null: _

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dafaccaicg_RAID_Volume11 A4B45635B4560A66                       ntfs       Program Disk                  
/dev/mapper/isw_dafaccaicg_RAID_Volume12 AA0451AC04517C6F                       ntfs       Data Disk                     
/dev/mapper/isw_dafaccaicg_RAID_Volume1: PTTYPE="dos" 
/dev/sda1        A4B45635B4560A66                       ntfs       Program Disk                  
/dev/sda2        AA0451AC04517C6F                       ntfs       Data Disk                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5f431df7-c07e-4275-8aeb-7b46280e0adc   ext4                                     
/dev/sda6        5512caf0-5cdb-4843-83d7-8030792b0074   ext4                                     
/dev/sda7        d2962fdd-b1de-439b-b4e3-6ccc6d48a0b1   swap                                     
/dev/sda                                                isw_raid_member                               
/dev/sdb1        A4B45635B4560A66                       ntfs       Program Disk                  
/dev/sdb2        AA0451AC04517C6F                       ntfs       Data Disk                     
/dev/sdb                                                isw_raid_member                               

= "mount | grep ^/dev  output: =

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


= sda1/boot.ini: =

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Enterprise" /fastdetect

= sda5/boot/grub/grub.cfg: =

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
search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5f431df7-c07e-4275-8aeb-7b46280e0adc ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5f431df7-c07e-4275-8aeb-7b46280e0adc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a4b45635b4560a66
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

= sda5/etc/fstab: =

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5f431df7-c07e-4275-8aeb-7b46280e0adc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2e5b968c-e406-4b63-af50-735941a8e97b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

= sda5: Location of files loaded by Grub: =


  89.8GB: boot/grub/core.img
  94.1GB: boot/grub/grub.cfg
  83.7GB: boot/initrd.img-2.6.35-22-generic
  89.7GB: boot/vmlinuz-2.6.35-22-generic
  83.7GB: initrd.img
  89.7GB: vmlinuz

= sda6/boot/grub/grub.cfg: =

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5512caf0-5cdb-4843-83d7-8030792b0074 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5512caf0-5cdb-4843-83d7-8030792b0074 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 5512caf0-5cdb-4843-83d7-8030792b0074
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a4b45635b4560a66
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f431df7-c07e-4275-8aeb-7b46280e0adc ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5f431df7-c07e-4275-8aeb-7b46280e0adc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5f431df7-c07e-4275-8aeb-7b46280e0adc ro single
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

= sda6/etc/fstab: =

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5512caf0-5cdb-4843-83d7-8030792b0074 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d2962fdd-b1de-439b-b4e3-6ccc6d48a0b1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

= sda6: Location of files loaded by Grub: =


  71.5GB: boot/grub/core.img
  80.0GB: boot/grub/grub.cfg
  65.4GB: boot/initrd.img-2.6.35-22-generic
  71.3GB: boot/vmlinuz-2.6.35-22-generic
  65.4GB: initrd.img
  71.3GB: vmlinuz

= isw_dafaccaicg_RAID_Volume11/boot.ini: =

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Enterprise" /fastdetect /NoExecute=OptOut
= Unknown MBRs/Boot Sectors/etc =

Unknown BootLoader  on sda3

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  07 00 30 10 00 2c 00 b8  |..........0..,..|
00000020  89 03 00 26 0b 00 00 06  24 00 00 01 1f e8 00 00  |...&....$.......|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 07  00 30 10 00 2c 00 b9 89  |.........0..,...|
00000050  03 00 26 0b 00 00 07 24  00 00 01 6b c8 00 00 00  |..&....$...k....|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 07 00  30 10 00 2c 00 ba 89 03  |........0..,....|
00000080  00 26 0b 00 00 08 24 00  00 01 e3 97 00 00 00 00  |.&....$.........|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 07 00 30  10 00 2c 00 bb 89 03 00  |.......0..,.....|
000000b0  26 0b 00 00 09 24 00 00  01 3c 50 00 00 00 00 00  |&....$...<P.....|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 07 00 30 10  00 2c 00 bc 89 03 00 26  |......0..,.....&|
000000e0  0b 00 00 0a 24 00 00 01  1f e8 00 00 00 00 00 00  |....$...........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 07 00 30 10 00  2c 00 bd 89 03 00 26 0b  |.....0..,.....&.|
00000110  00 00 c2 28 00 00 01 fc  10 00 00 00 00 00 00 00  |...(............|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 07 00 30 10 00 2c  00 be 89 03 00 26 0b 00  |....0..,.....&..|
00000140  00 c3 28 00 00 01 51 11  00 00 00 00 00 00 00 00  |..(...Q.........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 07 00 30 10 00 2c 00  bf 89 03 00 26 0b 00 00  |...0..,.....&...|
00000170  c4 28 00 00 01 d2 c5 00  00 00 00 00 00 00 00 00  |.(..............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  07 00 30 10 00 2c 00 c0  89 03 00 27 0b 00 00 7d  |..0..,.....'...}|
000001a0  2a 00 00 01 bf 7a 00 00  00 00 00 00 00 00 00 00  |*....z..........|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 60  24 02 00 e8 1b 04 00 fe  |.......`$.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 0c 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


= StdErr Messages: =

ERROR: isw: wrong number of devices in RAID set "isw_dafaccaicg_RAID_Volume1" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_dafaccaicg_RAID_Volume1" [1/2] on /dev/sdb
ERROR: creating degraded mirror mapping for "isw_dafaccaicg_RAID_Volume1"
ERROR: isw: wrong number of devices in RAID set "isw_dafaccaicg_RAID_Volume1" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_dafaccaicg_RAID_Volume1" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_dafaccaicg_RAID_Volume1" [1/2] on /dev/sdb
```

---

### Post by Quackers on 2010-12-08
It would appear that you are using a raid array. If so, you need more specialist advice than I can give :-)
I deleted my raid array to avoid these issues.

---

### Post by Rubi1200 on 2010-12-09
Hi ptrnrs,
thanks for posting the results. There is no such thing as an idiot around here! We all need help sometimes and the commands can be confusing at times (especially when a person is worried they may have lost important data etc.)

In any event, like Quackers I know nothing about RAID arrays.

However, did you try changing the boot order priority in BIOS to see if you can boot either sda or sdb?

---

### Post by ptrnrs on 2010-12-09
> However, did you try changing the boot order priority in BIOS to see if you can boot either sda or sdb?Thanks for the suggestion but I can't find any reference to SDA or SDB in BIOS setup.

I also tried disabling RAID option (sorry I forget the exact wording) and installing the Ubuntu Server (which is probably what I should be installing anyway) - same problem.

I looked at getting rid of the RAID array (which I don't really need), but that would delete Windows and I'm not ready to do that yet.

My real problem is this: I'm using this PC as a home file and print server and I want to check that I can get Ubuntu doing that role before deleting Windows.  Catch 22: I can't install Ubuntu untill I delete Windows and I don't want to delete Windows until I've installed Ubuntu.

I'm currently trying to set another PC up as Ubuntu server (just to test it out) and having a few problems with that as well.  You might see a couple of posts elsewhere.

Thanks all for your help.

---

### Post by zvacet on 2010-12-09
@ **ptrnrs**

> zvacet: Yes, I am stupid when it comes to Ubuntu but . . .

I never said you are stupid.I have to ask you trivial (as I said in first place) question,because I don´t know what do you know about Ubuntu and linux in general.In that case I always assume that OP is beginner.Sorry if you get that wrong.From boot script I see thhat you have more experience then I do,because I never try to put raid array.Once again sorry because I can not be much of help to you.Probably somebody else will be.Good luck!

---

### Post by ptrnrs on 2010-12-09
zvacet, my attempt at humour fell a bit flat - sorry about that.

I really do appreciate those of you experts who help out in the beginners forum.  Good on you!

---

### Post by Quackers on 2010-12-09
ptrnrs, do you have a raid0 array or raid1 ? In other words is your data split between 2 hard drives in a striped array or is one hard drive a copy of the other?

---

### Post by ptrnrs on 2010-12-09
> **quackers said:**
> ptrnrs, do you have a raid0 array or raid1 ? In other words is your data split between 2 hard drives in a striped array or is one hard drive a copy of the other?raid1

---

### Post by ptrnrs on 2010-12-11
. . . and the solution is . . .

From the BIOS and, despite the dire warnings that I might lose all my data (everything was backed up anyway), I changed the disk to Non-RAID and immediately everything worked.

---

