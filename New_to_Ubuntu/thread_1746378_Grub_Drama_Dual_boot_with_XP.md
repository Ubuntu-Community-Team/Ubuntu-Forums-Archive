---
title: "Grub Drama Dual boot with XP"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by meneathiel on 2011-05-01
I am sure everyone is sick to death of Dualboot problems so I apologize for bringing another one up. I have used several Linux versions of the years but have had very few issues with GRUB or booting so I consider myself a beginner with this problem.

Stupidity by me caused a failure of GRUB yesterday. I  shut off the computer rather then doing a normal shut down (It was frozen and I was in a hurry and as I said not thinking)

This morning only XP would boot. I have spent the day getting GRUB to start Ubuntu (I was accessing Ubuntu through SuperGrub) and I finally succeeded. Now however I have lost XP. I am sadly on my last brain cell and cannot face starting from scratch with this new/related problem. 

I have helpful ..stuff

```
~$ blkid
/dev/sda6: UUID="2373437f-1af5-4ee7-bcd4-cb2f2169ba6f" TYPE="ext4" 
blah@damien:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe50fe50f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2   *        6375       48641   339508833+   f  W95 Ext'd (LBA)
/dev/sda5           26481       48641   178008201    c  W95 FAT32 (LBA)
/dev/sda6            6375       25729   155461632   83  Linux
/dev/sda7           25729       26480     6037504   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaff9aff9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14588   117178078+   7  HPFS/NTFS
```and...


```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 425401263.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 178345984 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2    *    102,399,998   781,417,664   679,017,667   f W95 Ext d (LBA)
/dev/sda5         425,401,263   781,417,664   356,016,402   c W95 FAT32 (LBA)
/dev/sda6         102,400,000   413,323,263   310,923,264  83 Linux
/dev/sda7         413,325,312   425,400,319    12,075,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,356,219   234,356,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CAF88F7EF88F6811                       ntfs       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4565-D09B                              vfat                                     
/dev/sda6        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f   ext4                                     
/dev/sda7        d76bc7cc-98da-4623-813b-a2e683e318be   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2038D08C38D061F8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f

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
# howmany=4

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro quiet splash
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic (recovery mode)
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro quiet splash
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro quiet splash
initrd        /boot/initrd.img-2.6.32-29-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic (recovery mode)
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single
initrd        /boot/initrd.img-2.6.32-29-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro quiet splash
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
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
search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2373437f-1af5-4ee7-bcd4-cb2f2169ba6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2038d08c38d061f8
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=2373437f-1af5-4ee7-bcd4-cb2f2169ba6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d76bc7cc-98da-4623-813b-a2e683e318be none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  91.2GB: boot/grub/core.img
 205.6GB: boot/grub/grub.cfg
 205.9GB: boot/grub/menu.lst
  91.3GB: boot/grub/stage2
  91.4GB: boot/initrd.img-2.6.32-21-generic
  91.6GB: boot/initrd.img-2.6.32-24-generic
  91.6GB: boot/initrd.img-2.6.32-25-generic
  91.6GB: boot/initrd.img-2.6.32-26-generic
  91.6GB: boot/initrd.img-2.6.32-27-generic
  92.0GB: boot/initrd.img-2.6.32-28-generic
  91.9GB: boot/initrd.img-2.6.32-29-generic
  91.7GB: boot/initrd.img-2.6.32-30-generic
  91.7GB: boot/initrd.img-2.6.32-31-generic
  52.5GB: boot/vmlinuz-2.6.32-21-generic
  91.6GB: boot/vmlinuz-2.6.32-24-generic
  91.6GB: boot/vmlinuz-2.6.32-25-generic
  91.6GB: boot/vmlinuz-2.6.32-26-generic
  91.6GB: boot/vmlinuz-2.6.32-27-generic
  91.6GB: boot/vmlinuz-2.6.32-28-generic
  91.6GB: boot/vmlinuz-2.6.32-29-generic
  91.6GB: boot/vmlinuz-2.6.32-30-generic
  91.7GB: boot/vmlinuz-2.6.32-31-generic
  91.7GB: initrd.img
  91.7GB: initrd.img.old
  91.7GB: vmlinuz
  91.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1e 30 af 03 0c b6 02 10  25 0f 05 07 1c 59 0a 05  |.0......%....Y..|
00000010  0b 08 30 92 01 0b 08 04  01 08 3a 0f 11 08 0b 00  |..0.......:.....|
00000020  82 01 14 11 95 01 39 8e  0a 90 01 06 39 03 52 2e  |......9.....9.R.|
00000030  1b 38 09 02 30 03 e7 01  0b 04 09 1c a3 06 09 11  |.8..0...........|
00000040  e1 01 fc 02 02 04 0b 03  02 02 06 02 0e 05 03 08  |................|
00000050  36 02 c6 02 07 22 5c 0e  0b 1d 05 02 19 80 01 3f  |6...."\........?|
00000060  45 05 08 eb 01 02 05 04  36 2d b0 03 6b 2b 17 06  |E.......6-..k+..|
00000070  0d 04 1b 12 3a bc 02 1b  a4 01 26 30 39 67 46 92  |....:.....&09gF.|
00000080  01 48 03 07 01 04 05 16  01 12 08 12 00 05 08 cd  |.H..............|
00000090  01 3f 04 ac 03 df 02 8a  01 0b 47 b2 02 15 10 06  |.?........G.....|
000000a0  4d 28 22 03 12 e2 01 95  03 08 02 11 08 0d 0a 05  |M(".............|
000000b0  0d 0e 06 0c 04 04 6a 1d  1e 14 0d 64 00 02 06 03  |......j....d....|
000000c0  08 09 02 1d 05 0c 0e 09  0c 0e fa 01 0f ba 01 b2  |................|
000000d0  01 49 32 64 1e 05 14 4a  02 06 16 4a 13 0b 0c 77  |.I2d...J...J...w|
000000e0  00 02 04 03 02 03 03 12  06 07 0b 04 16 98 01 61  |...............a|
000000f0  03 ba 01 8e 01 11 08 06  12 09 22 45 14 04 04 05  |.........."E....|
00000100  17 17 0c 6b 77 26 28 09  03 0c 0e 1a 0b 03 0e 10  |...kw&(.........|
00000110  17 0a 04 0c 0e 1c 09 03  05 0d 10 90 01 7e 07 13  |.............~..|
00000120  46 06 14 8d 01 df 02 dc  02 1c a9 01 b9 01 a0 10  |F...............|
00000130  26 a0 01 4b 04 00 00 00  c7 03 02 00 c7 03 02 00  |&..K............|
00000140  56 88 16 00 57 88 16 00  a4 81 00 00 01 00 00 00  |V...W...........|
00000150  d0 10 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  bd 72 5f 4c d3 69 3c 4c  c5 72 5f 4c 10 00 00 00  |.r_L.i<L.r_L....|
00000170  44 01 00 00 55 88 16 00  a4 81 00 00 01 00 00 00  |D...U...........|
00000180  6d 07 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |m...............|
00000190  bd 72 5f 4c d3 69 3c 4c  c5 72 5f 4c 08 00 00 00  |.r_L.i<L.r_L....|
000001a0  44 01 00 00 7a 8f 49 00  a4 81 00 00 01 00 00 00  |D...z.I.........|
000001b0  b5 08 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  c1 ff 0c fe ff ff b1 9b  40 13 12 61 38 15 00 fe  |........@..a8...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 88 12 00 00  |...........P....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Any help would be very much appreciated.

---

### Post by spikoley on 2011-05-06
Try running *update-grub*. 

```
sudo update-grub
```

---

### Post by meneathiel on 2011-05-07
Thanks I did figure it up between this command and adding  to the grub file I was finally able to solve this.

---

