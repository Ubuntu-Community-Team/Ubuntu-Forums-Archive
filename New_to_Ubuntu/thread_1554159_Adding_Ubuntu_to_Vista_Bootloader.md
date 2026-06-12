---
title: "Adding Ubuntu to Vista Bootloader"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by dpilot83 on 2010-08-16
I hope I am not triple posting now. I have tried adding this thread to the Installation forum twice now and it didn't show that I had anything there so I'm going to try here. Please pardon my ignorance if I'm doing something obviously wrong and spamming the boards.

I have Windows XP, Vista and Ubuntu (10.04) all installed on my single hard drive. I re-installed XP and then ran the Vista CD to repair the Vista bootloader so that I could boot into XP and Vista. I can't figure out how to boot into Ubuntu now. I tried using EasyBCD (I believe an older version, maybe 1.72) to add Ubuntu to the Vista bootloader but I didn't have any luck. Ubuntu is in the menu, but when I select it, it goes to a screen that has GRUB in the upper left corner and does not load Ubuntu.

If it helps, before I re-installed XP and re-installed the Vista bootloader I was using GRUB for XP, Vista and Ubuntu because Ubuntu was the last thing to get installed.

Here are the results from boot_info_script055.sh. Thanks in advance for any help.

Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /NST/menu.lst /boot.ini /bootmgr /Boot/BCD /ntldr
/NTDETECT.COM

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /Windows/System32/winload.exe

sda3: __________________________________________________ _______________________

File system: ext2
Boot sector type: Grub
Boot sector info: Grub 0.97 is installed in the boot sector of sda3 and
looks at sector 97577074 of the same hard drive for
the stage2 file. A stage2 file is at this location on
/dev/sda. Stage2 looks on partition #3 for
/boot/grub/menu.lst.
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda5 starts
at sector 63.
Operating System:
Boot files/dirs:

sda6: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda6 starts
at sector 63.
Operating System:
Boot files/dirs:

sda7: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda7 starts
at sector 63.
Operating System:
Boot files/dirs:

sda8: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda8 starts
at sector 63.
Operating System:
Boot files/dirs:

sda9: __________________________________________________ _______________________

File system: ext2
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sda10: __________________________________________________ _______________________

File system: ext2
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sda11: __________________________________________________ _______________________

File system: ext2
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sda12: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 63 31,455,269 31,455,207 7 HPFS/NTFS
/dev/sda2 31,455,270 94,365,809 62,910,540 7 HPFS/NTFS
/dev/sda3 94,365,810 115,330,634 20,964,825 83 Linux
/dev/sda4 115,330,696 312,576,704 197,246,009 5 Extended
/dev/sda5 115,330,698 146,785,904 31,455,207 7 HPFS/NTFS
/dev/sda6 146,785,968 188,731,619 41,945,652 7 HPFS/NTFS
/dev/sda7 188,731,683 203,415,029 14,683,347 7 HPFS/NTFS
/dev/sda8 203,415,093 274,711,499 71,296,407 7 HPFS/NTFS
/dev/sda9 274,711,563 283,097,429 8,385,867 83 Linux
/dev/sda10 283,097,493 287,290,394 4,192,902 83 Linux
/dev/sda11 287,290,458 308,255,219 20,964,762 83 Linux
/dev/sda12 308,255,283 312,576,704 4,321,422 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda10 6e225d34-107f-4aec-9758-d485a259ecea ext2
/dev/sda11 7f612132-5c2f-4d16-bc2c-b321a6513315 ext2
/dev/sda12 ac3bd55c-e0d1-480f-a2dc-1cdbe1f54447 swap
/dev/sda1 824890844890791D ntfs
/dev/sda2 C084F1BE84F1B6CE ntfs
/dev/sda3 0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ext2
/dev/sda4: PTTYPE="dos"
/dev/sda5 D480C7E080C7C768 ntfs Windows_Stuff
/dev/sda6 A094A43294A40D3A ntfs Programs
/dev/sda7 387441397440FB60 ntfs Files_and_Documents
/dev/sda8 DC6C8B8B6C8B5EE0 ntfs Music_Videos
/dev/sda9 3d524a69-ae3d-406d-8941-9280159fdf39 ext2
/dev/sda: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at D:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)



find --set-root --ignore-floppies /boot/grub/menu.lst

configfile /boot/grub/menu.lst



# All your boot are belong to NeoSmart!
================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro quiet splash
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
echo 'Loading Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
linux /boot/vmlinuz-2.6.32-23-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro quiet splash
initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
echo 'Loading Linux 2.6.32-23-generic ...'
linux /boot/vmlinuz-2.6.32-23-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 0f263866-756e-4fd7-892b-3c6ec1ab1ad1
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 564089074088ef55
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda3 during installation
UUID=0f263866-756e-4fd7-892b-3c6ec1ab1ad1 / ext2 errors=remount-ro 0 1
# swap was on /dev/sda12 during installation
UUID=ac3bd55c-e0d1-480f-a2dc-1cdbe1f54447 none swap sw 0 0

=================== sda3: Location of files loaded by Grub: ===================


55.5GB: boot/grub/core.img
55.6GB: boot/grub/grub.cfg
55.5GB: boot/initrd.img-2.6.32-21-generic
55.5GB: boot/initrd.img-2.6.32-23-generic
55.4GB: boot/initrd.img-2.6.32-24-generic
55.4GB: boot/vmlinuz-2.6.32-21-generic
55.4GB: boot/vmlinuz-2.6.32-23-generic
55.4GB: boot/vmlinuz-2.6.32-24-generic
55.4GB: initrd.img
55.5GB: initrd.img.old
55.4GB: vmlinuz
55.4GB: vmlinuz.old

---

