---
title: "Another Dual Boot problem..."
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Fouppy on 2010-12-11
Hi,

I just installed Ubuntu on my laptop with Win 7 already installed.

I guess i did something wrong when i set up the installation. I can't boot into Win 7 anymore, i have the entry in Grub, but when i choose it, it goes back to Grub screen selection.

I still have access to Windows files/datas and to my Data partition when i'm on Ubuntu.

I've searched around for solutions, tried to use Super Grub Disk, but i'm kinda new to Linux, so... I need your help.

Here's the result of boot_info_script :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 138702912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   125,831,167   125,624,320   7 HPFS/NTFS
/dev/sda3         188,745,728   625,141,759   436,396,032   7 HPFS/NTFS
/dev/sda4         125,831,168   188,745,727    62,914,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC06E2D706E2B1A6                       ntfs       System Reserved               
/dev/sda2        54AEF3CFAEF3A79E                       ntfs       Windows                       
/dev/sda3        568661148660F5C1                       ntfs       Data                          
/dev/sda4        37fd27b9-8063-474c-b971-190e50a98f58   ext4       Ubuntu                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37fd27b9-8063-474c-b971-190e50a98f58

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

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        37fd27b9-8063-474c-b971-190e50a98f58
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Seven" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dc06e2d706e2b1a6
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=37fd27b9-8063-474c-b971-190e50a98f58 /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
  71.0GB: boot/grub/grub.cfg
  71.0GB: boot/grub/menu.lst
  65.3GB: boot/initrd.img-2.6.35-22-generic
  65.3GB: boot/initrd.img-2.6.35-24-generic
  65.0GB: boot/vmlinuz-2.6.35-22-generic
  71.0GB: boot/vmlinuz-2.6.35-24-generic
  65.3GB: initrd.img
  65.3GB: initrd.img.old
  71.0GB: vmlinuz
  65.0GB: vmlinuz.old
```Hope this helps.

Thanks for your replies, and sorry for my basic/bad english,

Edit : This is a fresh Seven/Ubuntu installation, so if there is no other solution than wipe all and start again from scratch that's not really a problem. But that would be nice if i could avoid it :p

Fouppy

---

### Post by wilee-nilee on 2010-12-11
sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   **/boot/grub/menu.lst** **/boot/grub/grub.cfg** /etc/fstab 
                       /boot/grub/core.img

Argh laddy it looks like grub-legacy and grub2 be in the mix follow this link.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Make sure your using a 10.10 live cd to do the fix. This is what the line highlighted should look like.
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

no /boot/grub/menu.lst

---

### Post by Fouppy on 2010-12-11
Hi, and thanks for your quick reply.

As i said ive tried several things before posting, and given that i'm rather new to Linux, that's a bit confusing and i did mistakes.

I've reinstalled Grub 2, following the steps you gave me.

Here's the new results :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 138702912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   125,831,167   125,624,320   7 HPFS/NTFS
/dev/sda3         188,745,728   625,141,759   436,396,032   7 HPFS/NTFS
/dev/sda4         125,831,168   188,745,727    62,914,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC06E2D706E2B1A6                       ntfs       System Reserved               
/dev/sda2        54AEF3CFAEF3A79E                       ntfs       Windows                       
/dev/sda3        568661148660F5C1                       ntfs       Data                          
/dev/sda4        37fd27b9-8063-474c-b971-190e50a98f58   ext4       Ubuntu                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37fd27b9-8063-474c-b971-190e50a98f58 ro single 
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 37fd27b9-8063-474c-b971-190e50a98f58
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dc06e2d706e2b1a6
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=37fd27b9-8063-474c-b971-190e50a98f58 /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
  67.0GB: boot/grub/grub.cfg
  65.3GB: boot/initrd.img-2.6.35-22-generic
  65.3GB: boot/initrd.img-2.6.35-24-generic
  65.0GB: boot/vmlinuz-2.6.35-22-generic
  71.0GB: boot/vmlinuz-2.6.35-24-generic
  65.3GB: initrd.img
  65.3GB: initrd.img.old
  71.0GB: vmlinuz
  65.0GB: vmlinuz.old
```

The line is ok this time. However the problem is still here, but changed : i can't boot Win 7, but instead of returning to Grub, there's a blinking underscore in the top left corner and nothing else.

---

### Post by wilee-nilee on 2010-12-11
Your doing great you have grub-legacy out.

So when you installed Ubuntu did you resize W7 first with its disk manager and reboot it to make sure it was working?

Or did you let the Ubuntu install partitioner do the work for you while installing Ubuntu?

If you didn't resize W7 ahead of time can you get to the safe mode to run a chkdsk /r. 
Safe mode is f8 immediately upon choosing W7 at the grub menu.

Here is a recovery you can download to get to the recovery command terminal, notice the W7 forums link and the instructions. You will probably get a do you want to run the chkdsk at next start so say yes and reboot to W7.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following command:

**chkdsk /r**

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Fouppy on 2010-12-11
I didn't resize Windows partition, i only resized/moved the Data partition to make room for Ubuntu.

Thanks for the links, i'll try them later, it's 4:00 AM here and I need to sleep a bit.

I'll give you news about it.

---

### Post by wilee-nilee on 2010-12-11
See next post.

---

### Post by wilee-nilee on 2010-12-11
sda1: _________________________________________________________________________

    File system:       ntfs
  **  Boot sector type:  Grub 2**
**    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and **
                       looks at sector 138702912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Missed this portion earlier my fault here is a link to take care of this.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You don't want grub in any NTFS partition is the basic idea.

This may just be the problem try this fix first and run the script and look to see that grub is gone from this partition.

---

### Post by Fouppy on 2010-12-12
Worked like a charm with testdisk !

W7 did a chdisk when i launched it and everything works fine.

But where's grub now ? It was on sda1 right? But now?

---

### Post by wilee-nilee on 2010-12-12
> **Fouppy said:**
> Worked like a charm with testdisk !

W7 did a chdisk when i launched it and everything works fine.

But where's grub now ? It was on sda1 right? But now?

There are grub.cfg files automatically installed in Ubuntu, but the grub bootloader goes in the mbr=master boot record=first 512 Mib of the HD.

The bootloader always goes to the mbr no matter if a MS bootloader or grub.

You had also mixed the older-grub-legacy and grub2 somehow.

Hey glad it works now, The bootscript if you run it for your self now you will see the difference.

---

