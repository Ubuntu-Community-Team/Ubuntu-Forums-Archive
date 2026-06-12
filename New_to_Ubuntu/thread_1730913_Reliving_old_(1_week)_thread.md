---
title: "Reliving old (1 week) thread"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Newsfromthenoob on 2011-04-16
Greetings all,
 
 
As the name implies, i am a total newbie who is trying to understand linux and, as a first step, installed ubuntu 10.10 in my computer. The installation ran perfectly and without any problems, but now a problem has arisen. Everytime i try to boot into ubuntu from the startup OS selection, i get the error message: "too many connections" and my screen stays gray/red with black dots. Cant do anything - have to restart and go from windows.
 
My configuration is as follows:
 
Prozessor AMD Phenom II X4 965 Black Edition, 3,4GHz, Quad-Core,
8 gig DDR3 RAM
Grafikkarte PCI-E 2.1 SAPPHIRE Radeon HD 6870,
Netzteil ATX 550 Watt, CHIEFTEC APS-550S EPS12V, 80Plus
Festplatte SATA II Seagate Barracuda 7200.12, 1 TB, 32MB Cache
DVD-+R/-+RW SATA LITEON iHAS124, schwarz
 
If any of you guys could give me a tip as to how i could get my ubuntu to work, id greatly appreciate it as id love to finally start using and learning it.
 
Thanks in advance!
 
----------------------------------------------------
 
After this message i ran this ([[COLOR=#444444]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")) from the Live CD 
and got the following message.
 
Could you guys point me in the right direction?
 
 
Hi guys,
 
So I finally found the time to try this out at home and ran the Live CD on my computer at home. Everything seems to work fine if I run from the CD (writing on it right now) and id love it if i could just install it and replace windows altogether :smile:
 
I did what you told me and downloaded this script, here are the results:
 
oh and yeah, its a side by side install on another partition created by the ubuntu installation disc
 
Thanks in advance guys :smile:
 ```

Boot Info Script 0.55 dated February 15th, 2010 
 
============================= Boot Info Summary: ==============================
 
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for (,msdos5)/boot/grub.
=> No boot loader is installed in the MBR of /dev/sdb
 
sda1: __________________________________________________ _______________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /bootmgr /Boot/BCD
 
sda2: __________________________________________________ _______________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe
 
sda3: __________________________________________________ _______________________
 
File system: Extended Partition
Boot sector type: -
Boot sector info: 
 
sda5: __________________________________________________ _______________________
 
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
sda6: __________________________________________________ _______________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
sdb1: __________________________________________________ _______________________
 
File system: vfat
Boot sector type: BSD4.4: Fat32
Boot sector info: According to the info in the boot sector, sdb1 starts 
at sector 0. But according to the info from fdisk, 
sdb1 starts at sector 63. According to the info in the 
boot sector, sdb1 has -387942475 sectors.. But 
according to the info from the partition table , it 
has 3907024820 sectors.
Operating System: 
Boot files/dirs: 
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ __________________________________________________ ___
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start End Size Id System
 
/dev/sda1 * 2,048 206,847 204,800 7 HPFS/NTFS
/dev/sda2 206,848 1,466,576,327 1,466,369,480 7 HPFS/NTFS
/dev/sda3 1,466,576,894 1,953,523,711 486,946,818 5 Extended
/dev/sda5 1,466,576,896 1,933,707,263 467,130,368 83 Linux
/dev/sda6 1,933,709,312 1,953,523,711 19,814,400 82 Linux swap / Solaris
 
 
Drive: sdb ___________________ __________________________________________________ ___
 
Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start End Size Id System
 
/dev/sdb1 63 3,907,024,883 3,907,024,821 b W95 FAT32
 
 
blkid -c /dev/null: __________________________________________________ __________
 
Device UUID TYPE LABEL 
 
/dev/loop0 squashfs 
/dev/sda1 D2AA73AFAA738EAB ntfs System Reserved 
/dev/sda2 E008DC0208DBD61E ntfs 
/dev/sda3: PTTYPE="dos" 
/dev/sda5 fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ext4 
/dev/sda6 1a29a61f-3b55-4aa9-bd37-d124a9ab9b68 swap 
/dev/sda: PTTYPE="dos" 
/dev/sdb1 A3F4-1BF6 vfat ELEMENTS 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
 
============================ "mount | grep ^/dev output: ===========================
 
Device Mount_Point Type Options
 
aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)
 
 
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
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro quiet splash
initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
echo 'Loading Linux 2.6.35-28-generic ...'
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
linux /boot/vmlinuz-2.6.35-27-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro quiet splash
initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
echo 'Loading Linux 2.6.35-27-generic ...'
linux /boot/vmlinuz-2.6.35-27-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
echo 'Loading Linux 2.6.35-22-generic ...'
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fa28ff9f-35e8-4455-b5a2-3dc185c4b970
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d2aa73afaa738eab
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
 
=============================== sda5/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=fa28ff9f-35e8-4455-b5a2-3dc185c4b970 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=1a29a61f-3b55-4aa9-bd37-d124a9ab9b68 none swap sw 0 0
 
=================== sda5: Location of files loaded by Grub: ===================
 
 
849.8GB: boot/grub/core.img
882.0GB: boot/grub/grub.cfg
752.2GB: boot/initrd.img-2.6.35-22-generic
752.3GB: boot/initrd.img-2.6.35-27-generic
752.5GB: boot/initrd.img-2.6.35-28-generic
849.8GB: boot/vmlinuz-2.6.35-22-generic
849.8GB: boot/vmlinuz-2.6.35-27-generic
849.8GB: boot/vmlinuz-2.6.35-28-generic
752.5GB: initrd.img
752.3GB: initrd.img.old
849.8GB: vmlinuz
849.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============
```
*Last edited by Newsfromthenoob; 9 Hours Ago at 04:15 AM.. *

---

### Post by jtarin on 2011-04-16
[There's an ongoing thread on this issue here.]("http://ubuntuforums.org/showthread.php?t=1635278")

---

