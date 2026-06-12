---
title: "Which partition is using GRUB???"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by iamgeniusrnti on 2010-08-10
OK, wuick dumb question--I am quadruple booting an Acer Aspire Netbook between Windows XP (sda2), UNR (sda3), BT4 (sda6) and Ubuntu (sda7).  I know sda 3 and 7 have grub installed but I don't know which one the computer is actually booting.  Gparted says sda7 is the boot flag, but it seems when I run update-grub from sda 3, that seems to implement the change...  I really want sda7 to be it because I intend to overwrite sda3 with Fedora or Jolicloud... haven't decided.

Also, in both my partitions, I have a lot of junk kernels, I want to uninstall but I know if I reboot with a bad grub cfg, it will pee on itself and then I wil have to spend hours on google looking up the commands to right it.  

I have read over the tutorial but I think I am misunderstanding Grub perhaps??

---

### Post by oldfred on 2010-08-10
If you have multiple installs it is worthwhile to run this. I run it before and after new system installs just to know what is where and to document the configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by iamgeniusrnti on 2010-08-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a0d38ea

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    14,683,409    14,683,347  12 Compaq diagnostics
/dev/sda2          14,684,160    96,598,844    81,914,685   7 HPFS/NTFS
/dev/sda3          96,598,845   156,440,969    59,842,125  83 Linux
/dev/sda4         156,440,970   300,286,979   143,846,010   5 Extended
/dev/sda5         261,377,550   292,093,829    30,716,280   7 HPFS/NTFS
/dev/sda6         156,441,096   214,371,359    57,930,264  83 Linux
/dev/sda7    *    214,371,423   261,377,549    47,006,127  83 Linux
/dev/sda8         292,093,893   300,286,979     8,193,087  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        8C6CED9C6CED8176                       ntfs       PQSERVICE                     
/dev/sda2        16E4D467E4D44B1F                       ntfs       ACER                          
/dev/sda3        736cda19-db55-4e5a-a944-5bc31fe50779   reiserfs                                 
/dev/sda5        11905ED22EBD8CEC                       ntfs       Shared                        
/dev/sda6        d01f9679-4402-4598-909d-786313a32aec   ext4                                     
/dev/sda7        a7fb89fd-dbeb-4431-bdfb-a113fbe42775   ext4                                     
/dev/sda8        e77b4fc6-96a6-48a6-a208-0850f128021c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/menu.lst: ===========================

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
default        0

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
# kopt=root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=736cda19-db55-4e5a-a944-5bc31fe50779

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
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

splashimage=736cda19-db55-4e5a-a944-5bc31fe50779/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        736cda19-db55-4e5a-a944-5bc31fe50779
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro vga=0x317 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        736cda19-db55-4e5a-a944-5bc31fe50779
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        736cda19-db55-4e5a-a944-5bc31fe50779
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro splash 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-16-generic-pae (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro splash 
initrd        /boot/initrd.img-2.6.31-16-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
initrd        /boot/initrd.img-2.6.31-16-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-16-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro splash 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-21-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro single 
initrd        /boot/initrd.img-2.6.31-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-20-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro single 
initrd        /boot/initrd.img-2.6.31-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-19-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro single 
initrd        /boot/initrd.img-2.6.31-19-generic
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=736cda19-db55-4e5a-a944-5bc31fe50779 /               reiserfs notail,relatime 0       1
# /dev/sda8
UUID=e77b4fc6-96a6-48a6-a208-0850f128021c none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd.img-2.6.30.9
    ??GB: boot/vmlinuz-2.6.30.9
    ??GB: initrd.img
    ??GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro   
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro   
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro   
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro   
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8c6ced9c6ced8176
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 16e4d467e4d44b1f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro vga=0x317
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro single
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a7fb89fd-dbeb-4431-bdfb-a113fbe42775
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a7fb89fd-dbeb-4431-bdfb-a113fbe42775
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro single
    initrd /boot/initrd.img-2.6.31-22-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=d01f9679-4402-4598-909d-786313a32aec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=e77b4fc6-96a6-48a6-a208-0850f128021c none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  84.8GB: boot/grub/core.img
  84.1GB: boot/grub/grub.cfg
  81.6GB: boot/initrd.img-2.6.31-14-generic
  87.2GB: boot/initrd.img-2.6.31-16-generic
  90.3GB: boot/initrd.img-2.6.31-16-generic-pae
  91.0GB: boot/initrd.img-2.6.31-17-generic
  80.6GB: boot/vmlinuz-2.6.31-14-generic
  80.8GB: boot/vmlinuz-2.6.31-16-generic
  81.7GB: boot/vmlinuz-2.6.31-16-generic-pae
  87.0GB: boot/vmlinuz-2.6.31-17-generic
  91.0GB: initrd.img
  90.3GB: initrd.img.old
  87.0GB: vmlinuz
  81.7GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set a7fb89fd-dbeb-4431-bdfb-a113fbe42775
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a7fb89fd-dbeb-4431-bdfb-a113fbe42775
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a7fb89fd-dbeb-4431-bdfb-a113fbe42775
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8c6ced9c6ced8176
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 16e4d467e4d44b1f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro vga=0x317
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/vmlinuz-2.6.30.9 root=UUID=736cda19-db55-4e5a-a944-5bc31fe50779 ro single
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
    insmod reiserfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 736cda19-db55-4e5a-a944-5bc31fe50779
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro
    initrd /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single
    initrd /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d01f9679-4402-4598-909d-786313a32aec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d01f9679-4402-4598-909d-786313a32aec ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=a7fb89fd-dbeb-4431-bdfb-a113fbe42775 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e77b4fc6-96a6-48a6-a208-0850f128021c none            swap    sw              0       0
#192.168.1.3:/media/HomeRepo /media/HomeRepo nfs rsize=8192,wsize=8192,timeo=14,intr
#192.168.1.3:/media/HomeRepo2 /media/HomeRepo2 nfs rsize=8192,wsize=8192,timeo=14,intr
#192.168.1.3:/media/HomeRepoMain /media/HomeRepoMain nfs rsize=8192,wsize=8192,timeo=14,intr
#192.168.1.10:/HomeRepo /media/FreeAgent nfs rsize=8192,wsize=8192,timeo=14,intr
//192.168.1.10/HomeRepo /media/FreeAgent cifs username=root,password=honoluluhi79 0 0
#//ntserver/share /mnt/samba smbfs username=username,password=password 0 0

=================== sda7: Location of files loaded by Grub: ===================


 120.8GB: boot/grub/core.img
 125.2GB: boot/grub/grub.cfg
 112.3GB: boot/initrd.img-2.6.31-22-generic
 124.2GB: boot/vmlinuz-2.6.31-22-generic
 112.3GB: initrd.img
 124.2GB: vmlinuz
```

---

### Post by oldfred on 2010-08-11
The grub in the MBR boots sda6 which is Ubuntu 9.10. But you also have another 9.10 in sda7.

It looks like the grub2 osprober sees backtrack as Ubuntu 8.10 in sda3.

---

### Post by iamgeniusrnti on 2010-08-11
> **oldfred said:**
> The grub in the MBR boots sda6 which is Ubuntu 9.10. But you also have another 9.10 in sda7.

It looks like the grub2 osprober sees backtrack as Ubuntu 8.10 in sda3.

Hmm... therein lies the problem, I want it to look in sda7 so I can install a new os in 6 as I don't really care for UNR.  I thought by flagging sda7 to be the boot, that would fix it.  How do I steer it?

---

### Post by oldfred on 2010-08-11
It is easiest to boot into the sda7 version and install grub from that. Or you can reinstall from a liveCD or other installs.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub


or from your sda6 install or a liveCD:
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda
After booting into sda7:
sudo update -grub

---

