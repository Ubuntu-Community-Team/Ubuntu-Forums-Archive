---
title: "Problems  booting Ubuntu 10.04 LTS"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by povl on 2010-08-18
When trying to boot "Lucid Lynx"  I get the following message:

                                 Gave up waiting for root device. Common problems:
 -Boot args (cat  /proc/cmdline)
   -Check rootdelay= (did the system wait long enough?)
   -Check root= (did the system wait for the right device?)
 

 -Missing modules (cat  /proc/modules;  1s   /dev)
 

 ALERT!   /dev/disk /by-uuid/4f6abdb 2-579c-4d9d-95e2-fdc2b8433556   does not exist.
 

 Dropping to a shell!
 

 BusyBox v1.13.3  (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
 

 Enter 'help' for a list of built-in commands.
 

 (initramfs)
 

 

However, by writing "exit" after (initramfs) it boots and works correctly!!  How do I correct this boot problem??

---

### Post by MooPi on 2010-08-18
In terminal ```
sudo blkid
```
Check the results and compare to actual devices. Check if you've got an extra disk listed or if the disk uuid=4f6abdb 2-579c-4d9d-95e2-fdc2b8433556 actually exits.You may have to edit your /etc/fstab file 
It would be a good idea to post the results for ```
sudo blkid
```
and the contents of /ect/fstab back here.

---

### Post by povl on 2010-08-21
OK but what does this mean: ??

  	 	 	 	 	 	  paj@Maxi:~$ sudo blkid 
 [sudo] password for paj:  
 /dev/sda1: UUID="0827ac5e-c84f-408b-8c85-1d8a4b16fb7f" TYPE="ext4"  
 /dev/sda5: UUID="bb6b29e4-c0c8-4d4c-95e2-acdfa9b38e58" TYPE="swap"  
 /dev/sda6: UUID="4f6adbd2-579c-4d9d-95e2-fdc2b8433556" TYPE="ext4"  
 /dev/sda7: UUID="4aa7ca94-4e21-40a4-9fc9-61c8461984da" TYPE="swap"  
 /dev/sdb1: SEC_TYPE="msdos" LABEL="D2" UUID="65DF-D014" TYPE="vfat"  
 paj@Maxi:~$  
 

And this: ??



 paj@Maxi:~$ /ect/fstab  
 bash: /ect/fstab: No such file or directory 
 paj@Maxi:~$

---

### Post by Rubi1200 on 2010-08-21
You need to open the file and post the contents here using this command:

```
cat /etc/fstab
```

Just copy and paste into the terminal please.

---

### Post by povl on 2010-08-22
OK the following turns up:

paj@Maxi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4aa7ca94-4e21-40a4-9fc9-61c8461984da none            swap    sw              0       0
paj@Maxi:~$ 


povl

---

### Post by Rubi1200 on 2010-08-22
Hi,
do you have an Ubuntu CD?

If yes, boot the computer choosing to try not install.

Post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by povl on 2010-08-23
[SIZE=3]Here are results of the Boot Script:[/SIZE]


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 568959 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 9237 MB, 9237086208 bytes
255 heads, 63 sectors/track, 1123 cylinders, total 18041184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     8,204,454     8,202,407  83 Linux
/dev/sda2           8,206,334    18,040,831     9,834,498   5 Extended
/dev/sda5          17,172,480    18,040,831       868,352  82 Linux swap / Solaris
/dev/sda6           8,206,336    16,666,623     8,460,288  83 Linux
/dev/sda7          16,668,672    17,158,143       489,472  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 420 MB, 420441600 bytes
16 heads, 52 sectors/track, 986 cylinders, total 821175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             52       819,519       819,468   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bb6b29e4-c0c8-4d4c-95e2-acdfa9b38e58   swap                                     
/dev/sda6        4f6adbd2-579c-4d9d-95e2-fdc2b8433556   ext4                                     
/dev/sda7        4aa7ca94-4e21-40a4-9fc9-61c8461984da   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        65DF-D014                              vfat       D2                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bb6b29e4-c0c8-4d4c-95e2-acdfa9b38e58 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
   1.2GB: boot/grub/grub.cfg
    .2GB: boot/grub/menu.lst
    .6GB: boot/initrd.img-2.6.32-21-generic
   3.3GB: boot/initrd.img-2.6.32-23-generic
    .6GB: boot/vmlinuz-2.6.32-21-generic
    .1GB: boot/vmlinuz-2.6.32-23-generic
   3.3GB: initrd.img
    .6GB: initrd.img.old
    .1GB: vmlinuz
    .6GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4f6adbd2-579c-4d9d-95e2-fdc2b8433556
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0827ac5e-c84f-408b-8c85-1d8a4b16fb7f ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0827ac5e-c84f-408b-8c85-1d8a4b16fb7f
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4f6adbd2-579c-4d9d-95e2-fdc2b8433556 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4aa7ca94-4e21-40a4-9fc9-61c8461984da none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
   8.3GB: boot/initrd.img-2.6.32-21-generic
   8.4GB: boot/initrd.img-2.6.32-23-generic
   8.4GB: boot/initrd.img-2.6.32-24-generic
   4.3GB: boot/vmlinuz-2.6.32-21-generic
   8.3GB: boot/vmlinuz-2.6.32-23-generic
   7.1GB: boot/vmlinuz-2.6.32-24-generic
   8.4GB: initrd.img
   8.4GB: initrd.img.old
   7.1GB: vmlinuz
   8.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff fe 00 20 02 9c be 07  b3 08 ba 9c d7 07 ab 08  |... ............|
00000010  04 06 17 1e c4 03 cc 50  2f 1d 1e d2 fd b4 bf 7a  |.......P/......z|
00000020  da fe da 5f bd 6d 6f ed  2f de b1 df 5e d7 f4 bd  |..._.mo./...^...|
00000030  2a cc 0b ad 40 04 00 40  9c e4 07 b4 08 c1 9a 9c  |*...@..@........|
00000040  fd 07 b3 08 c1 d0 9c 92  08 b3 08 b6 9c ab 08 ab  |................|
00000050  08 ba 9c b7 08 b3 08 c1  9e 9c d0 08 b3 08 b2 9c  |................|
00000060  e9 08 b3 08 c1 e6 9c 82  09 b3 08 04 04 09 0a f8  |................|
00000070  03 e4 6e 07 80 07 80 07  80 07 80 07 00 0f 00 0e  |..n.............|
00000080  00 0e 00 0c 00 1c 00 9c  93 09 c5 08 c1 9a 9c ac  |................|
00000090  09 b3 08 c1 ca 9c c1 09  b3 08 c1 96 9c da 09 b3  |................|
000000a0  08 c1 da 9c 90 0a ab 08  bc 9c a9 0a b4 08 c1 c2  |................|
000000b0  9c ce 0a ab 08 c1 ca 9c  db 0a b3 08 c1 9e 9c f4  |................|
000000c0  0a b3 08 9c 8d 0b b3 08  b2 9c a6 0b b3 08 c1 e6  |................|
000000d0  9c bf 0b b3 08 c1 ce 9c  dc 0b ab 08 ba 9c e9 0b  |................|
000000e0  b3 08 c1 da 9c 81 0c ab  08 c1 96 9c a7 0c b3 08  |................|
000000f0  ba 9c d1 0c b3 08 c1 da  9c ea 0c ab 08 c1 c0 9c  |................|
00000100  8f 0d b3 08 04 06 15 25  fa 03 ac 6f 27 74 e8 f6  |.......%...o't..|
00000110  eb 7a 7f ff 6b 7a b1 56  a3 9f 16 08 3c 3c be e0  |.z..kz.V....<<..|
00000120  9b 8b db fe 66 09 05 ad  12 9f 0b a5 ff af fa ef  |....f...........|
00000130  b6 16 c4 c3 ed 76 10 c0  04 00 40 9c a8 0d a6 08  |.....v....@.....|
00000140  b2 9c ce 0d b4 08 c1 ca  9c e7 0d b3 08 c1 e6 9c  |................|
00000150  80 0e b3 08 c1 98 9c 90  0e b3 08 ba 9c a9 0e b3  |................|
00000160  08 04 06 1f 16 fc 03 e0  70 2e cc cc d2 fa ff ba  |........p.......|
00000170  7e e6 1f 5f d7 f7 dd 5f  dd 75 fd 6f df d5 eb 75  |~.._..._.u.o...u|
00000180  ff d6 fd fd 5e b1 51 fe  fe 9a ff e0 02 00 20 9c  |....^.Q....... .|
00000190  cb 0e b4 08 c1 98 9c ec  0e b3 08 c1 f2 9c 85 0f  |................|
000001a0  ab 08 c1 9a 9c 9e 0f b3  08 c1 ce 9c b3 0f ab 08  |................|
000001b0  c1 ee 9c bf 0f ad 08 c1  98 9c d0 0f b3 08 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 d0  88 00 00 40 0d 00 00 d1  |...........@....|
000001d0  53 fe 05 fe ff ff 01 00  00 00 01 18 81 00 00 00  |S...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


[SIZE=3]I appreciate the help that I am getting - I hope that I can understand it!!
povl[/SIZE] :D

---

