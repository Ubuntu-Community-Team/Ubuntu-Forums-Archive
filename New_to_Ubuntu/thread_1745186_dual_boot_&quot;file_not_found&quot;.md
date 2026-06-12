---
title: "dual boot &quot;file not found&quot;"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by beelzebufo on 2011-04-30
so I had 10.10 installed, I have set up tons of dual boots, I wanted to dual with BT4.  did the dual boot and now when I try to get into my 10.10 I get a file not found error, is there any way to recover?  any help would be greatly appriciated, all my stuff is on that partition, I have never had a problem dual booting before, so I didn't back up.. I dum

---

### Post by Ken UK on 2011-04-30
Can't you just use a LiveCD to access and recover your information?

Can't tell from what you have said what happened to your installation though.

---

### Post by beelzebufo on 2011-04-30
I can't seem to figure out how to get to the other partitions in BT4, not real familiar with kde.  I can't figure out what heppened either, I didn't get any errors or anything while installing... perplexed bt4 works, so something happened while resizing the partitions.. I think

---

### Post by Quackers on 2011-04-30
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by beelzebufo on 2011-04-30
gedit wont open the txt for some reason.. I have updated grub to grub 2, I think that may have been the problem.  BackTrack4 uses grub, and I had everything set up with grub 2 before, however now when I try to run ubuntu in grub2, it says I have to start the kernel, any ideas? running my 10.04 live cd now till I get this figured out

---

### Post by beelzebufo on 2011-04-30
there we go, lol couldn't figure out gedit there for a minute

looking in my boot/grub folder, I don't see a menu.lst file either, I have been looking here to see if maybe it will help.. [http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)
nothing yet though, as like I said I can't find the menu.lst file so kinda dead ended on this one

```
                         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  GnackTrack 10.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   389,206,754   389,204,707  83 Linux
/dev/sda2         389,206,879   625,141,759   235,934,881   5 Extended
/dev/sda5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris
/dev/sda6         389,206,881   591,882,794   202,675,914  83 Linux
/dev/sda7         591,882,858   600,557,894     8,675,037  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,620,279    15,620,218   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        83d22434-d14d-4445-8928-2c8023b8a287   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bb552d4e-1f8a-4136-8cb0-702c9f59723e   swap                                     
/dev/sda6        4eaec51c-cfde-42a3-847e-329d3b22b21d   ext3                                     
/dev/sda7        b9985d5a-dc18-4e88-b3c7-423b080f6ea4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CAB-2184                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/83d22434-d14d-4445-8928-2c8023b8a287 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
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
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro   splash quiet vga=0x318
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    echo    'Loading Linux 2.6.39-020639rc3-generic ...'
    linux    /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro   splash quiet vga=0x318
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 83d22434-d14d-4445-8928-2c8023b8a287
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
# / was on /dev/sda1 during installation
UUID=83d22434-d14d-4445-8928-2c8023b8a287 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9dc7f970-4fc3-4042-8af6-07ace18fbbce none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.7GB: boot/grub/core.img
 133.3GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-27-generic
   1.9GB: boot/initrd.img-2.6.39-020639rc3-generic
   3.8GB: boot/vmlinuz-2.6.35-27-generic
   3.8GB: boot/vmlinuz-2.6.39-020639rc3-generic
   1.9GB: initrd.img
   1.5GB: initrd.img.old
   3.8GB: vmlinuz
   3.8GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4eaec51c-cfde-42a3-847e-329d3b22b21d

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
# defoptions=vga=0x317

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
##      altoptions=(single-user) single
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

splashimage=4eaec51c-cfde-42a3-847e-329d3b22b21d/boot/grub/splash.xpm.gz

title        Chainload into GRUB 2
root        4eaec51c-cfde-42a3-847e-329d3b22b21d
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Debian GNU/Linux, kernel 2.6.30.9
root        4eaec51c-cfde-42a3-847e-329d3b22b21d
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d ro vga=0x317
initrd        /boot/initrd.img-2.6.30.9

title        Debian GNU/Linux, kernel 2.6.30.9 (recovery mode)
root        4eaec51c-cfde-42a3-847e-329d3b22b21d
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d ro single
initrd        /boot/initrd.img-2.6.30.9

title        Debian GNU/Linux, kernel memtest86+
root        4eaec51c-cfde-42a3-847e-329d3b22b21d
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.39-020639rc3-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro splash quiet vga=0x318 
initrd        /boot/initrd.img-2.6.39-020639rc3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.39-020639rc3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single 
initrd        /boot/initrd.img-2.6.39-020639rc3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro splash quiet vga=0x318 
initrd        /boot/initrd.img-2.6.35-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single 
initrd        /boot/initrd.img-2.6.35-27-generic
savedefault
boot


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,6)
if font (hd0,6)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.30.9" {
    linux    (hd0,6)/boot/vmlinuz-2.6.30.9 root=UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d ro quiet splash 
    initrd    (hd0,6)/boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu, linux 2.6.30.9 (single-user mode)" {
    linux    (hd0,6)/boot/vmlinuz-2.6.30.9 root=UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d ro single
    initrd    (hd0,6)/boot/initrd.img-2.6.30.9
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd0,6)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.39-020639rc3-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro splash quiet vga=0x318
    initrd /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry "'Ubuntu, with Linux 2.6.39-020639rc3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.39-020639rc3-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single
    initrd /boot/initrd.img-2.6.39-020639rc3-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro splash quiet vga=0x318
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=83d22434-d14d-4445-8928-2c8023b8a287 ro single
    initrd /boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/30_os-prober ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=4eaec51c-cfde-42a3-847e-329d3b22b21d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9985d5a-dc18-4e88-b3c7-423b080f6ea4 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 234.9GB: boot/grub/core.img
 234.9GB: boot/grub/grub.cfg
 234.8GB: boot/grub/menu.lst
 234.9GB: boot/grub/stage2
 234.8GB: boot/initrd.img-2.6.30.9
 234.8GB: boot/vmlinuz-2.6.30.9
 234.8GB: initrd.img
 234.8GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/initrd800.gz
    ??GB: boot/initrdfr.gz
    ??GB: boot/initrd.gz
    ??GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 12 09  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  7a 58 ee 00 77 3b 00 00  00 00 00 00 02 00 00 00  |zX..w;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 84 21 ab 7c 4e  4f 20 4e 41 4d 45 20 20  |..).!.|NO NAME  |
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
00000100  7d 00 66 b8 b8 ab 2f 00  66 ba 00 00 00 00 bb 00  |}.f.../.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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



```

---

### Post by beelzebufo on 2011-04-30
dangit, now I can't even get the grub menu at boot... help!! I destroyed my computer!!

and I get this.. I must have done something unknowingly to unmount something? maybe? or something
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by beelzebufo on 2011-05-01
solved 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Quackers on 2011-05-01
> **beelzebufo said:**
> solved 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

That would do it :-)
Well done!

---

