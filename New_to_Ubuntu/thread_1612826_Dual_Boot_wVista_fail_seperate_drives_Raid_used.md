---
title: "Dual Boot w/Vista fail seperate drives Raid used"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by jscherer26 on 2010-11-03
I had a machine setup with raid running Vista. I purchased 2 more drives to dual boot with Ubuntu 10.10 utilizing ?software raid0. Ubuntu 10.10 is booting fine but Vista is not. All is see is a "-" when I select it in Grub. I tried to find a solution but was unable, so I'm posting here.

I hopefully attached a RESULTS.txt "Boot Info Script 0.55" as I found that was helpful in some of the other requests.  Thanks in advance.

Jim

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/mapper/nvidia_dijhbgdd

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

nvidia_dijhbgdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

md1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         742,397,952   976,771,071   234,373,120  fd Linux raid autodetect
/dev/sda2         732,633,088   742,397,951     9,764,864  fd Linux raid autodetect
/dev/sda3    *    731,656,192   732,633,087       976,896  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         742,397,952   976,771,071   234,373,120  fd Linux raid autodetect
/dev/sdb2         732,633,088   742,397,951     9,764,864  fd Linux raid autodetect
/dev/sdb3         731,656,192   732,633,087       976,896  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   293,044,223   293,042,176   7 HPFS/NTFS


Drive: nvidia_dijhbgdd ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_dijhbgdd: 150.0 GB, 150039944192 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046766 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_dijhbgdd1   *          2,048   293,044,223   293,042,176   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 2c16ebf7-dac4-40cb-8d7f-1fa86767d476   swap                                     
/dev/mapper/nvidia_dijhbgdd1 7C34F0C134F08006                       ntfs                                     
/dev/mapper/nvidia_dijhbgdd: PTTYPE="dos" 
/dev/md0         c2e2f210-750d-453b-ab1f-343094121aa8   ext4                                     
/dev/sda1        219bc276-f28a-a44c-cbf6-dfd46920264a   linux_raid_member                               
/dev/sda2        adfe4b6f-0c79-c483-612c-ad0096b91d95   linux_raid_member                               
/dev/sda3        5a167d7b-9530-4d4a-bfb7-79cef0e5309e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        219bc276-f28a-a44c-cbf6-dfd46920264a   linux_raid_member                               
/dev/sdb2        adfe4b6f-0c79-c483-612c-ad0096b91d95   linux_raid_member                               
/dev/sdb3        7bb99f2e-41a0-42f7-b7e1-9a09333d8024   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                nvidia_raid_member                               
/dev/sdd                                                nvidia_raid_member                               
error: /dev/sdc1: No such file or directory
error: /dev/sde: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1
nvidia_dijhbgdd
nvidia_dijhbgdd1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb3        /temporary               ext4       (rw,commit=0)
/dev/sda3        /boot                    ext4       (rw,commit=0)


============================= sda3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/md0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5a167d7b-9530-4d4a-bfb7-79cef0e5309e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        5a167d7b-9530-4d4a-bfb7-79cef0e5309e
kernel        /vmlinuz-2.6.35-22-generic root=/dev/md0 ro quiet splash 
initrd        /initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        5a167d7b-9530-4d4a-bfb7-79cef0e5309e
kernel        /vmlinuz-2.6.35-22-generic root=/dev/md0 ro  single
initrd        /initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        5a167d7b-9530-4d4a-bfb7-79cef0e5309e
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        5a167d7b-9530-4d4a-bfb7-79cef0e5309e
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sda3/grub/grub.cfg: =============================

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

insmod raid
insmod mdraid
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set c2e2f210-750d-453b-ab1f-343094121aa8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 5a167d7b-9530-4d4a-bfb7-79cef0e5309e
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 5a167d7b-9530-4d4a-bfb7-79cef0e5309e
    linux    /vmlinuz-2.6.35-22-generic root=UUID=c2e2f210-750d-453b-ab1f-343094121aa8 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 5a167d7b-9530-4d4a-bfb7-79cef0e5309e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=c2e2f210-750d-453b-ab1f-343094121aa8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 5a167d7b-9530-4d4a-bfb7-79cef0e5309e
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 5a167d7b-9530-4d4a-bfb7-79cef0e5309e
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/mapper/nvidia_dijhbgdd1)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/nvidia_dijhbgdd,msdos1)'
    search --no-floppy --fs-uuid --set 7c34f0c134f08006
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

=================== sda3: Location of files loaded by Grub: ===================


 374.8GB: grub/core.img
 374.8GB: grub/grub.cfg
 374.8GB: grub/menu.lst
 374.6GB: initrd.img-2.6.35-22-generic
 374.6GB: vmlinuz-2.6.35-22-generic

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=c2e2f210-750d-453b-ab1f-343094121aa8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=5a167d7b-9530-4d4a-bfb7-79cef0e5309e /boot           ext4    defaults        0       2
# /temporary was on /dev/sdb3 during installation
UUID=7bb99f2e-41a0-42f7-b7e1-9a09333d8024 /temporary      ext4    defaults        0       2
# swap was on /dev/md1 during installation
#UUID=43fa847a-1d0f-4366-8ccd-6ffc9c8d4867 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

==================== md0: Location of files loaded by Grub: ====================


    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1



=======Devices which don't seem to have a corresponding hard drive==============

sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory

```

---

