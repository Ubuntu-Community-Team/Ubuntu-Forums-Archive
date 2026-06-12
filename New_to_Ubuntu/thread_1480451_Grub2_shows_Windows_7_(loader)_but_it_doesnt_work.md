---
title: "Grub2 shows Windows 7 (loader) but it doesnt work"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by cosaki on 2010-05-11
Grub Legacy actually worked perfectly to dual-boot 10.04 and  Windows 7. After Grub2 was installed, Grub went into some kind of test  mode that told me to make sure everything booted properly before  finishing the upgrade. The only problem I had there was that I would  need to select my OS twice. After the first Grub menu (no matter what OS  I chose) it would go to a second Grub menu, but this time there was no  message that told me how to finish the upgrade. I thought that was how  it was supposed to work, so I upgraded the rest of the way. Now my boot  menu shows Windows 7 (loader), Windows Vista (loader) and the various  Ubuntu kernels. I did an upgrade from Vista to 7 last year, and I  haven't seen the Vista option since then. Now Ubuntu loads (but it takes  much longer than it used to), and Windows 7 just reboots the system.
 

I've tried everything I could find on the various  forums, but I am a complete noob in Linux.  Things have gotten worse!  I know Windows 7 is still in  there, because when I'm in Ubuntu I can see the files and such when I  navigate to it. I can even see everything on my Windows desktop still.  Any help would be greatly appreciated!

Here is my boot info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   200,191,563   200,191,501   7 HPFS/NTFS
/dev/sda2         463,186,080   488,392,064    25,205,985   7 HPFS/NTFS
/dev/sda3         200,191,998   463,186,079   262,994,082   5 Extended
/dev/sda5         258,389,523   454,768,019   196,378,497  83 Linux
/dev/sda6         454,768,083   463,186,079     8,417,997  82 Linux swap / Solaris
/dev/sda7         200,192,000   255,897,599    55,705,600  83 Linux
/dev/sda8         255,899,648   258,387,967     2,488,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        32CAE859CAE81B3D                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0137e513-3e41-42c4-9d04-8fe94e172118   ext3                                     
/dev/sda6        e10df765-057c-4449-8721-80670541dcb4   swap                                     
/dev/sda7        f885e3b4-23be-4703-bee3-ff6ba5e19373   ext4                                     
/dev/sda8        9570661a-f9ee-4b72-8a78-4811531bfd0b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=chris)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0137e513-3e41-42c4-9d04-8fe94e172118

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7 (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32cae859cae81b3d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0137e513-3e41-42c4-9d04-8fe94e172118 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e10df765-057c-4449-8721-80670541dcb4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 217.2GB: boot/grub/core.img
 217.1GB: boot/grub/grub.cfg
 217.1GB: boot/grub/menu.lst
 217.2GB: boot/grub/stage2
 217.2GB: boot/initrd.img-2.6.31-17-generic
 217.2GB: boot/initrd.img-2.6.32-21-generic
 217.1GB: boot/initrd.img-2.6.32-22-generic
 217.1GB: boot/vmlinuz-2.6.31-17-generic
 217.1GB: boot/vmlinuz-2.6.32-21-generic
 217.2GB: boot/vmlinuz-2.6.32-22-generic
 217.1GB: initrd.img
 217.2GB: initrd.img.old
 217.2GB: vmlinuz
 217.1GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32cae859cae81b3d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9570661a-f9ee-4b72-8a78-4811531bfd0b none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 106.9GB: boot/grub/core.img
 117.7GB: boot/grub/grub.cfg
 106.9GB: boot/initrd.img-2.6.32-21-generic
 106.9GB: boot/vmlinuz-2.6.32-21-generic
 106.9GB: initrd.img
 106.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e9 2d 2c 91 94 ab 8c 8c  ab 94 91 2c 2d 2b 92 94  |.-,........,-+..|
00000010  ab 8c 8c ab 94 92 fe dc  02 cd fd 33 05 b7 5e b7  |...........3..^.|
00000020  82 50 45 7e fa e6 7e 44  4f 82 b7 5e 5e b7 82 4f  |.PE~..~DO..^^..O|
00000030  44 7e 05 1a 7e 45 50 82  b7 f8 9d 62 00 01 01 6a  |D~..~EP....b...j|
00000040  00 00 06 6b 04 ff 00 05  00 35 b9 00 01 01 d0 40  |...k.....5.....@|
00000050  0c 05 03 02 47 04 05 0a  01 02 47 00 05 bf 01 2a  |....G.....G....*|
00000060  00 06 00 04 01 2a 00 07  01 bc 01 62 00 18 2b 10  |.....*.....b..+.|
00000070  e4 10 f6 3c fd 3c 00 3f  3c fd 3c 10 ed 31 30 01  |...<.<.?<.<..10.|
00000080  33 11 21 15 21 01 6a 64  04 9d fa ff 04 ff fb 65  |3.!.!.jd.......e|
00000090  64 00 00 01 00 c0 00 00  05 01 05 68 00 22 00 48  |d..........h.".H|
000000a0  40 0f 00 01 12 11 12 12  00 00 01 08 1a 3e 09 10  |@............>..|
000000b0  0e b8 03 aa b6 24 17 17  1a 10 3e 13 b8 02 58 b5  |.....$....>...X.|
000000c0  22 3e 02 19 23 9f b9 01  12 00 18 2b 4e 10 f4 4d  |">..#......+N..M|
000000d0  ed f4 fd 4e 45 65 44 e6  4d e4 00 3f ed 3f 3c 10  |...NEeD.M..?.?<.|
000000e0  3c 10 3c 11 39 39 31 30  21 23 11 34 37 3e 03 33  |<.<.9910!#.47>.3|
000000f0  32 1e 02 17 16 15 11 23  11 34 27 2e 03 23 22 0e  |2......#.4'..#".|
00000100  02 07 06 06 15 01 2e 6e  06 0c 40 8c cf 74 70 cc  |.......n..@..tp.|
00000110  96 40 0a 04 6d 06 0b 33  6d a9 5a 4a 8b 63 3d 0e  |.@..m..3m.ZJ.c=.|
00000120  19 16 02 30 f8 42 77 98  93 5c 58 97 aa 7f 32 ee  |...0.Bw..\X...2.|
00000130  fd d0 02 36 da 3f 6f 83  73 4a 33 4b 4f 23 3c ad  |...6.?o.sJ3KO#<.|
00000140  ef 00 00 03 00 26 01 38  04 5d 04 16 00 03 00 07  |.....&.8.]......|
00000150  00 0b 00 57 b3 0b 0a 5d  09 b8 03 9a b3 07 06 5d  |...W...].......]|
00000160  05 b8 03 9a 40 0e 03 02  5d 01 01 00 01 02 02 05  |....@...].......|
00000170  06 06 09 0a b8 03 13 40  09 0d 00 03 03 04 07 07  |.......@........|
00000180  08 0b b8 02 0a b3 0c 9c  5b 18 2b 10 f6 3c 3c 10  |........[.+..<<.|
00000190  3c 3c 10 3c 10 f6 3c 3c  10 3c 3c 10 3c 00 2f 3c  |<<.<..<<.<<.<./<|
000001a0  10 fd 3c f6 fd 3c f6 fd  3c 31 30 13 21 15 21 15  |..<..<..<10.!.!.|
000001b0  21 15 21 15 21 15 21 26  04 37 fb c9 04 37 00 fe  |!.!.!.!&.7...7..|
000001c0  ff ff 83 fe ff ff 15 06  78 03 81 7f b4 0b 00 fe  |........x.......|
000001d0  ff ff 05 fe ff ff 96 85  2c 0f 0c 73 80 00 00 00  |........,..s....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by cosaki on 2010-05-11
This is my grub.cfg:
```

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32cae859cae81b3d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by oldfred on 2010-05-11
Your grub.cfg is in the results.txt. It spits out just about everything related to booting a system.

I do not see anything wrong. You do have two Ubuntu installs one on sda5 and the other sda7. Grub2 boots you into sda7. The install in sda5 shows windows entries but sda7 does not so it would try this:

sudo update-grub

That should find your windows and the other Ubuntu install.

Is the reference to a Vista partition just your recovery or vendor supplied data partition in sda2? It looks like your main win7 is sda1 and it looks ok.

Do you want 2 installs? I would think about converting the partition with the first install to a /home and move /home to that partition but that will be later.

---

### Post by cosaki on 2010-05-11
Hi and thanks for the quick response.  Thanks for letting me know about the grub.cfg being in the results.  I wasn't sure so I posted it anyway.  I tried sudo update-grub and it found everything, but Windows 7 still won't load.

I have two Ubuntu installations because I used the Windows 7 recovery disk to try and see if there were any problems there, and I think it overwrote Grub.  I tried to re-install Ubuntu over the old one to bring Grub back, but I managed to mess that up as well.  I can boot into both now, but the newer kernel is the one on sda5.  Eventually I would like to completely remove the one on sda7 and give that piece of the hard drive back to Windows (not sure if this is even possible, but it's really no big loss).

Is there any other information I could provide that could give anymore insight on this issue?  I don't know if it is something wrong with Grub or Windows, but it worked perfectly until I updated to Grub2.

Thanks again :)

---

### Post by oldfred on 2010-05-11
Usually if it finds windows it says it is ok and will at least get you in with the safe mode or whatever windows does now. I am afraid we will have to run the windows repairs and running fixboot will put that back into the MBR.

We will then reinstall grub to allow you to boot sda5, but you still have parts of old grub that sometimes causes problems. if so we can install grub for sda7 boot into sda5 and clean it up.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


After booting windows several times to make sure it is ok.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Install from LiveCD:
Find linux partition should be sda5 or sda7:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by cosaki on 2010-05-11
Some of the results seemed wrong:

chkdsk /r -- The type of the file system is NTFS.
Cannot lock current drive.
Windows cannot run disk checking on this volume because it is write protected.

bootrec.exe /scanos -- Successfully scanned Windows installations. Total identified Windows installations: 0
The operation completed Successfully.

bootrec.exe /rebuildbcd -- Successfully scanned Windows installations. Total identified Windows installations: 0
The operation completed Successfully.

What does this mean?

---

### Post by cosaki on 2010-05-11
After a reboot it skips the Grub screen and just goes to the blinking cursor in the upper-left-hand corner.  Windows 7 still will not load.  This was the step I was at last time when I re-installed 10.04 instead of Grub.  Do you recommend that I put Grub back in, or should I wait until the Windows 7 side is fixed?

Thanks again!

---

### Post by oldfred on 2010-05-11
I think we need to fix windows, just installing grub will not change how windows is working. How does a hard disk partition become write protected under windows? My old flopppy drives have a little slider to unlock them. I just checked gparted and write protect is not a flag to manage. Did you run this from a windows CD?

This suggested a new driver:
[http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/dbdf9e52-8eb9-4a4f-a10e-2764dc20596d](http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/dbdf9e52-8eb9-4a4f-a10e-2764dc20596d)

Another ran defrag and solved a similar issue.

---

### Post by cosaki on 2010-05-11
OK the Grub installation instructions worked great.  Still no luck with Windows though :(

*** oops I missed your last post before posting this one.  I'll give that a shot and see if anything works.  Thank you!

---

### Post by cosaki on 2010-05-11
> **oldfred said:**
> I think we need to fix windows, just installing grub will not change how windows is working. How does a hard disk partition become write protected under windows? My old flopppy drives have a little slider to unlock them. I just checked gparted and write protect is not a flag to manage. Did you run this from a windows CD?

This suggested a new driver:
[http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/dbdf9e52-8eb9-4a4f-a10e-2764dc20596d](http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/dbdf9e52-8eb9-4a4f-a10e-2764dc20596d)

Another ran defrag and solved a similar issue.

I ran this from a Windows 7 repair CD that I downloaded as an ISO.  I upgraded this system from Vista via a download so I did not have the normal OS CDs that come with new computers.  Is it possible to run chkdsk or defrag without being able to boot into Windows 7?

---

### Post by Blutkoete on 2010-05-11
Have you tried simply selecting the Vista boot option?

On my computer, it works like this:

SDA1 is the actual windows loader that boots what's in SDA2. As you upgraded from Vista to Windows 7, it might still be refered to as Vista. On my computer, that SDA1 is only about 10 MeB in size. Just a guess though.

I had a similar problem at the beginning with the OEM Windows 7 on my computer which I solved the hard way in the end (removed all partitions, reinstalled a clean Windows 7 and then Ubuntu).

---

### Post by cosaki on 2010-05-11
> **Blutkoete said:**
> Have you tried simply selecting the Vista boot option?

On my computer, it works like this:

SDA1 is the actual windows loader that boots what's in SDA2. As you upgraded from Vista to Windows 7, it might still be refered to as Vista. On my computer, that SDA1 is only about 10 MeB in size. Just a guess though.

I had a similar problem at the beginning with the OEM Windows 7 on my computer which I solved the hard way in the end (removed all partitions, reinstalled a clean Windows 7 and then Ubuntu).

I did try this, but unfortunately it does the same thing as selecting the Windows 7 option -- blinking cursor in the upper-left-hand corner :(

I am running the Windows 7 CHKDSK now, so hopefully that will fix everything ](*,)

---

### Post by kansasnoob on 2010-05-12
Any luck yet?

I'm afraid I have nothing to add really, I mean getting Windows repaired needs to be job #1, and I can't really add anything to what oldfred's suggested.

---

### Post by cosaki on 2010-05-12
CHKDSK ran with no errors.... this is so weird.  I know that Windows 7 is in there somewhere.  I read somewhere else that maybe I installed Grub in the NTFS portion of the drive and that could be messing it up?  I think I'm going to call around to a couple of repair shops and see if they'll be able to fix this issue.  I don't have my Windows 7 install DVD since I upgraded through a download.

Thanks again everyone for all the help :)

---

### Post by oldfred on 2010-05-12
the original boot info script shows your windows in sda1 and does not show any issues. Boot sector has windows files.  If you put the windows boot loader into the MBR does it still not boot?

Run the full set of windows repairs:
Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by cosaki on 2010-05-13
Sorry oldfred, I don't understand how to put the boot loader into the MBR.  

I tried all the fixes, but still have the same results.  Does this put the boot loader into the MBR?

---

### Post by Mark Phelps on 2010-05-13
In Win7, the bootloader is put into the MBR by booting from the Win7 DVD (or Win7 Repair CD) and running the bootrec.exe /fixmbr command from a command prompt, or by running Startup Repair three times -- the MBR is replaced on the third pass.

---

### Post by cosaki on 2010-05-13
It seems like the repair CD can't find the Windows installation.  I keep getting the message "Total identified Windows installations: 0
The operation completed successfully".

This happens when I try ```
bootrec /RebuildBCD
``` or ```
bootrec /ScanOS
``` or any of those bootrec options.  Do you have any suggestions?

Thanks

---

### Post by cosaki on 2010-05-13
> **Mark Phelps said:**
> In Win7, the bootloader is put into the MBR by booting from the Win7 DVD (or Win7 Repair CD) and running the bootrec.exe /fixmbr command from a command prompt, or by running Startup Repair three times -- the MBR is replaced on the third pass.

Oh OK I tried this previously, but still no luck :(  Thanks for the info though!

---

### Post by kansasnoob on 2010-05-13
I just saw your addition to that bug report and I think you have a different issue. I also understand you're frustrated but since you have tried a few things please run the Boot Info Script again so I can get a fresh look and I'll try really, really hard to come up with a solution.

If the old RESULTS.txt is still on your computer the new one will be RESULTS1.txt, etc, etc:

```
lance@lance-desktop:~$ ls ~/Downloads
boot_info_script055.sh          RESULTS1.txt
gparted-live-0.4.6-1.iso        RESULTS2.txt
KNOPPIX_V6.2.1CD-2010-01-31-EN  RESULTS2.txt.tar.gz
LinuxMint-7.iso                 RESULTS3.txt
linuxmint-9-gnome-rc-i386.iso   RESULTS.txt
lost+found                      ubuntu-10.04-desktop-i386.iso
lubuntu-10.04.iso               ubuntu-8.04.4-desktop-i386.iso
pclinuxos-gnome-2010.iso        ubuntu-9.04-desktop-i386.iso
pmagic-4.9.iso.zip              ubuntu-9.10-desktop-i386.iso

```

I'll really try to hang in there with you!

---

### Post by cosaki on 2010-05-13
Just leaving work now so I'll get that posted as soon as I get home.  Thanks!

---

### Post by kansasnoob on 2010-05-13
I've also been looking through this and racking my brain (trying to remember past problems and solutions) and it would also be helpful to see a screenshot of Gparted. It's included in the Live CD: System > Administration > Gparted, but it's not included in the final installation so if you want to take a screenshot from your installed Ubuntu you'll have to:

```
sudo apt-get install gparted
```

To post a screenshot first take the screenshot (tool's in Accessories) then click on the paperclip thingy at the top of this reply box. Then click "Browse" > to where it's saved, Upload, and click on paperclip again to attach.

---

### Post by cosaki on 2010-05-13
Here is my new boot info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   200,191,563   200,191,501   7 HPFS/NTFS
/dev/sda2         463,186,080   488,392,064    25,205,985   7 HPFS/NTFS
/dev/sda3         200,191,998   463,186,079   262,994,082   5 Extended
/dev/sda5         258,389,523   454,768,019   196,378,497  83 Linux
/dev/sda6         454,768,083   463,186,079     8,417,997  82 Linux swap / Solaris
/dev/sda7         200,192,000   255,897,599    55,705,600  83 Linux
/dev/sda8         255,899,648   258,387,967     2,488,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        32CAE859CAE81B3D                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0137e513-3e41-42c4-9d04-8fe94e172118   ext3                                     
/dev/sda6        e10df765-057c-4449-8721-80670541dcb4   swap                                     
/dev/sda7        f885e3b4-23be-4703-bee3-ff6ba5e19373   ext4                                     
/dev/sda8        9570661a-f9ee-4b72-8a78-4811531bfd0b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0137e513-3e41-42c4-9d04-8fe94e172118

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        0137e513-3e41-42c4-9d04-8fe94e172118
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7 (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32cae859cae81b3d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0137e513-3e41-42c4-9d04-8fe94e172118 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e10df765-057c-4449-8721-80670541dcb4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 217.1GB: boot/grub/core.img
 217.1GB: boot/grub/grub.cfg
 217.1GB: boot/grub/menu.lst
 217.2GB: boot/grub/stage2
 217.2GB: boot/initrd.img-2.6.31-17-generic
 217.2GB: boot/initrd.img-2.6.32-21-generic
 217.1GB: boot/initrd.img-2.6.32-22-generic
 217.1GB: boot/vmlinuz-2.6.31-17-generic
 217.1GB: boot/vmlinuz-2.6.32-21-generic
 217.2GB: boot/vmlinuz-2.6.32-22-generic
 217.1GB: initrd.img
 217.2GB: initrd.img.old
 217.2GB: vmlinuz
 217.1GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f885e3b4-23be-4703-bee3-ff6ba5e19373
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32cae859cae81b3d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0137e513-3e41-42c4-9d04-8fe94e172118
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=0137e513-3e41-42c4-9d04-8fe94e172118 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=f885e3b4-23be-4703-bee3-ff6ba5e19373 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9570661a-f9ee-4b72-8a78-4811531bfd0b none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 106.9GB: boot/grub/core.img
 117.7GB: boot/grub/grub.cfg
 106.9GB: boot/initrd.img-2.6.32-21-generic
 106.9GB: boot/vmlinuz-2.6.32-21-generic
 106.9GB: initrd.img
 106.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e9 2d 2c 91 94 ab 8c 8c  ab 94 91 2c 2d 2b 92 94  |.-,........,-+..|
00000010  ab 8c 8c ab 94 92 fe dc  02 cd fd 33 05 b7 5e b7  |...........3..^.|
00000020  82 50 45 7e fa e6 7e 44  4f 82 b7 5e 5e b7 82 4f  |.PE~..~DO..^^..O|
00000030  44 7e 05 1a 7e 45 50 82  b7 f8 9d 62 00 01 01 6a  |D~..~EP....b...j|
00000040  00 00 06 6b 04 ff 00 05  00 35 b9 00 01 01 d0 40  |...k.....5.....@|
00000050  0c 05 03 02 47 04 05 0a  01 02 47 00 05 bf 01 2a  |....G.....G....*|
00000060  00 06 00 04 01 2a 00 07  01 bc 01 62 00 18 2b 10  |.....*.....b..+.|
00000070  e4 10 f6 3c fd 3c 00 3f  3c fd 3c 10 ed 31 30 01  |...<.<.?<.<..10.|
00000080  33 11 21 15 21 01 6a 64  04 9d fa ff 04 ff fb 65  |3.!.!.jd.......e|
00000090  64 00 00 01 00 c0 00 00  05 01 05 68 00 22 00 48  |d..........h.".H|
000000a0  40 0f 00 01 12 11 12 12  00 00 01 08 1a 3e 09 10  |@............>..|
000000b0  0e b8 03 aa b6 24 17 17  1a 10 3e 13 b8 02 58 b5  |.....$....>...X.|
000000c0  22 3e 02 19 23 9f b9 01  12 00 18 2b 4e 10 f4 4d  |">..#......+N..M|
000000d0  ed f4 fd 4e 45 65 44 e6  4d e4 00 3f ed 3f 3c 10  |...NEeD.M..?.?<.|
000000e0  3c 10 3c 11 39 39 31 30  21 23 11 34 37 3e 03 33  |<.<.9910!#.47>.3|
000000f0  32 1e 02 17 16 15 11 23  11 34 27 2e 03 23 22 0e  |2......#.4'..#".|
00000100  02 07 06 06 15 01 2e 6e  06 0c 40 8c cf 74 70 cc  |.......n..@..tp.|
00000110  96 40 0a 04 6d 06 0b 33  6d a9 5a 4a 8b 63 3d 0e  |.@..m..3m.ZJ.c=.|
00000120  19 16 02 30 f8 42 77 98  93 5c 58 97 aa 7f 32 ee  |...0.Bw..\X...2.|
00000130  fd d0 02 36 da 3f 6f 83  73 4a 33 4b 4f 23 3c ad  |...6.?o.sJ3KO#<.|
00000140  ef 00 00 03 00 26 01 38  04 5d 04 16 00 03 00 07  |.....&.8.]......|
00000150  00 0b 00 57 b3 0b 0a 5d  09 b8 03 9a b3 07 06 5d  |...W...].......]|
00000160  05 b8 03 9a 40 0e 03 02  5d 01 01 00 01 02 02 05  |....@...].......|
00000170  06 06 09 0a b8 03 13 40  09 0d 00 03 03 04 07 07  |.......@........|
00000180  08 0b b8 02 0a b3 0c 9c  5b 18 2b 10 f6 3c 3c 10  |........[.+..<<.|
00000190  3c 3c 10 3c 10 f6 3c 3c  10 3c 3c 10 3c 00 2f 3c  |<<.<..<<.<<.<./<|
000001a0  10 fd 3c f6 fd 3c f6 fd  3c 31 30 13 21 15 21 15  |..<..<..<10.!.!.|
000001b0  21 15 21 15 21 15 21 26  04 37 fb c9 04 37 00 fe  |!.!.!.!&.7...7..|
000001c0  ff ff 83 fe ff ff 15 06  78 03 81 7f b4 0b 00 fe  |........x.......|
000001d0  ff ff 05 fe ff ff 96 85  2c 0f 0c 73 80 00 00 00  |........,..s....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```I'll work on getting that screen shot now :)

---

### Post by cosaki on 2010-05-13
Here is the gparted screenshot.  Hopefully I attached it correctly :)

---

### Post by cosaki on 2010-05-13
Here is a screenshot when i right-click on the ntfs drive and select "Information".  Thought it might help.

I won't able to do much more today, but I'll be back tomorrow morning.  Thank you again everyone for all the help!

---

### Post by kansasnoob on 2010-05-13
Thanks for the second screenshot!

This begins to answer some questions!

It's looking like the second Ubuntu install (when you tried to just restore the original) pinched Windows to where it has no free space.

But please give me time to look at this closer!

It was also a bad idea to shove an extended partition in between two primary partitions.

I need time to digest this.

---

### Post by kansasnoob on 2010-05-13
First of all we need to get our tools in order.

Since you can't boot into Windows we're going to have to use Gparted and Lucid's Gparted is buggy, do you have any other Ubuntu Live CD's?

It seems to me like the version of Gparted in Karmic is good, in Jaunty it's fair.

What Linux Live CD's do you have?

---

### Post by kansasnoob on 2010-05-13
Something else (very preliminary) ntfsprogs should be installed by default but just in case it's not run:

```
sudo apt-get install ntfsprogs
```

Then reboot and and look at Gparted again.

You can double check the status of "ntfsprogs" by running:

```
aptitude show ntfsprogs|head -4
```

In fact just post the output of that last command. We need to play it safe here.

---

### Post by kansasnoob on 2010-05-13
Hey, I'm getting a bit tired, and I have a couple of "skunked" animals to bathe again, so if you don't hear from me for several hours I didn't disappear :)

There's at least a 50% chance we can recover this. However, if you've not already done so, this would be a good time to see if you can access the files in Windows.

Then look for a good way to back them up! We all have different methods and availability to backup media, etc.

---

### Post by cosaki on 2010-05-13
I tried to install ntfsprogs, but got this message:
```

chris@chris-laptop:~$ sudo apt-get install ntfsprogs
[sudo] password for chris: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@chris-laptop:~$ 
```

Does this mean it didn't install correctly? When I run the next line i get this:
```

chris@chris-laptop:~$ aptitude show ntfsprogs|head -4
Package: ntfsprogs
State: installed
Automatically installed: yes
Version: 2.0.0-1ubuntu4
chris@chris-laptop:~$ 
```

Unfortunately, I don't have any other Live CDs.  My first Ubuntu installation was 8.04 (I think), but i haven't done much with it until recently.  I can access everything in the Windows partition, but there is nothing to backup.  This laptop is just a "play" computer, so all that is on here are some saved games from Warcraft III I think.  I would have just wiped everything and started completely fresh, but I thought it would be difficult since I don't have the Windows DVDs anymore :(

This is also my last post until tomorrow.... I can't thank you enough for all this help!

---

### Post by kansasnoob on 2010-05-13
I'll be back tomorrow also. I won't abandon you!

I think it would be interesting to try and save this.

---

### Post by cosaki on 2010-05-14
Hi,

I just went to the ntfsprogs website, and it said that their servers are currently down due to an attack.  That's probably why it wasn't able to install yesterday.

[http://www.linux-ntfs.org/doku.php]("http://www.linux-ntfs.org/doku.php")

---

### Post by kansasnoob on 2010-05-14
> **cosaki said:**
> Hi,

I just went to the ntfsprogs website, and it said that their servers are currently down due to an attack.  That's probably why it wasn't able to install yesterday.

[http://www.linux-ntfs.org/doku.php]("http://www.linux-ntfs.org/doku.php")

But ntfsprogs is available in the repos. And it's installed:

```
chris@chris-laptop:~$ aptitude show ntfsprogs|head -4
Package: ntfsprogs
State: **[COLOR="Red"]installed[/COLOR]**
Automatically installed: yes
Version: 2.0.0-1ubuntu4
chris@chris-laptop:~$
```

We just need to figure out exactly what is wrong with your Windows partition. How full do you think it was before installing the second Lucid?

BTW it's been a rough day so don't expect any amazing brilliance from me :)

---

### Post by kansasnoob on 2010-05-14
Just a shout out to others ............. if you have any ideas please do post them :)

---

### Post by cosaki on 2010-05-14
My Windows partition was empty before the 2nd Lucid install.  None of the fixes worked before that 2nd install, which is why I ended up doing it (and messing up more in the process).  Does that matter at all?

Also, after the Grub2 update, Lucid takes especially long to load.  After I select it from Grub, I get the same flashing cursor in the corner, and then the screen flashes, then it boots.

Thank you again for the help.... This is pretty interesting stuff, and I'm learning quite a bit about Ubuntu :)

---

### Post by oldfred on 2010-05-15
I did see one post where someone left a CD in the tray and CD was first in boot order. System was trying to fsck the CD and took forever. He removed Cd and boot was very quick. That sounds like a bug but the fix was easy.

---

### Post by kansasnoob on 2010-05-15
**[COLOR="Red"]Please read this all before proceeding![/COLOR]** At this point you should consider this just thinking out loud. Sometimes discussing options openly will result in someone having a true epiphany :)

Regarding the Win7 issue I've been studying, and even though your problem is different look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

When you get to "Sixth   screen:  "BackupBS" this is what you'll see:

[ATTACH]157036[/ATTACH]

Now, mine doesn't show the BackupBS option because the backup is identical, but you'll notice that there are two other options: RebuildBS and RepairMFT. You can read more about that here:

[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Perhaps though, given the error in parted, instead of "Fourth  screen:  "advanced", you should begin with "Analyse":

[ATTACH]157037[/ATTACH]

Much more about that here:

[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Hopefully someone with more testdisk experience will jump into the fray :)

---

### Post by cosaki on 2010-05-16
Thank you for the advice, Kansas.  I won't be able to try this until Monday though.  Not sure if this matters at all, but when I started up Ubuntu today, it ran that check on the drive and didn't find any errors.

I'll get back to you on Monday...  Hope everyone is having a good weekend!

---

### Post by kansasnoob on 2010-05-17
Just wondering how this is going :confused:

I could PM a person or two :)

---

### Post by cosaki on 2010-05-17
Sorry no updates yet... I will keep you posted as soon as possible though :P

---

### Post by cosaki on 2010-05-18
Previously, someone suggested to repair the boot sector.  The first time I got to that screen, the sectors were not identical, so I had testdisk repair them.  Now I get the same screen as you with the boot sector and backup sector both showing "OK".

Testdisk is currently doing an Analyse cylinder check when I asked it to dig deeper.  So far there are not any errors reported, but it's only at 14%.  Should be done in 30 minutes or so.

I was looking back at those screenshots from gparted, and was wondering if you know of any way to fix that error on the NTFS drive? The only thread I could find in the Ubuntu forums with the same error is this one:

[http://ubuntuforums.org/showthread.php?t=877189](http://ubuntuforums.org/showthread.php?t=877189)

and it looks like it was never resolved. :(

Also, should I start a new thread with a different title since this is kind of a different issue now?

---

### Post by cosaki on 2010-05-18
Here is a screenshot of the teskdisk results.  I have no idea what they mean, but it sure found a lot of stuff.  Is this normal?

Also, is it possible to just delete the partition that I made for the second installation of Lucid?  If I did that, would Windows just take it back? :confused:

---

### Post by cosaki on 2010-05-21
Anyone have any advice? :confused:

---

### Post by oldfred on 2010-05-21
Test disk is showing all the partitions that it could see that you ever had. Some may be duplicates or overlaping but it is giving you a choice to change it from deleted to primary or extended which ever it should be.

If you delete a partition you then have to expand another or create another to use the space that then becomes available.


Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by cosaki on 2010-05-21
Thanks Oldfred,

I'll try to remove that partition I made on accident and see if that helps the Windows start-up.

Any idea why every partition other than the "* HPFS" said that it was deleted?  Or does that "D" mean something else?  After I ran a more thorough check (down the line somewhere in TestDisk) it wouldn't let me change the status of NTFS partition.  It would turn the text red and give an error.  Did I lose it forever?

---

### Post by oldfred on 2010-05-21
I think the * on the recovery partition is saying it is not deleted and is a bootable partition.

---

### Post by cosaki on 2010-05-26
Hi,

I've marked this thread as "Solved" because I just did a complete reformat and re-installed Windows 7 + Ubuntu.  Thanks again for all the help!  This is a great community =D>

---

