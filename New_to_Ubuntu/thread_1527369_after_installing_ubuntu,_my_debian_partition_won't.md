---
title: "after installing ubuntu, my debian partition won't boot"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by kazordoon on 2010-07-09
i just got the last ubuntu cd, 10.04, and installed it in one of my paritions (/dev/sda4)
it works fine. my windowsXP on /dev/hda1 also works fine, but my debian partition on /dev/hda2 won't boot. actually starts to boot but the computer freezes when the screen shows the line "mounting root file system".
 
any ideas?

---

### Post by philinux on 2010-07-09
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Run the script and post back the results file.

---

### Post by audiomick on 2010-07-09
> **philinux said:**
> [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Run the script and post back the results file.

+1 for Philinux.
There are some instructions on using the script here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kazordoon on 2010-07-09
ok, here is RESULTS.txt. Please advise:

               ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 129569552 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on the same partition for 
                       /boot/grub/menu.lst.
    Operating System:  Debian GNU/Linux 4.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,482,689    16,482,627   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,963,629    81,963,567   7 HPFS/NTFS
/dev/sdb2          81,963,630   121,017,644    39,054,015  83 Linux
/dev/sdb3         121,017,645   123,122,159     2,104,515  82 Linux swap / Solaris
/dev/sdb4         123,122,160   160,071,659    36,949,500  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        54CC3F23CC3EFEB4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        06407F35407F2B17                       ntfs       Datos                         
/dev/sdb2        7b7f32c9-8a72-4d95-b306-1b8aa6a803b2   ext3                                     
/dev/sdb3        37ad2fd5-37c1-4b14-ab19-328d62299756   swap                                     
/dev/sdb4        dbbd7633-9e49-4ee7-9a3b-ca0b8615c510   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdc4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,3)

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
# defoptions=

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
# altoptions=(single-user mode) single

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

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.18-6-686 (on /dev/hdc2)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.18-6-686 root=/dev/hdc2 ro 
initrd        /boot/initrd.img-2.6.18-6-686
savedefault

title        Debian GNU/Linux, kernel 2.6.18-6-686 (single) (on /dev/hdc2)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.18-6-686 root=/dev/hdc2 ro single
initrd        /boot/initrd.img-2.6.18-6-686
savedefault

title        Debian GNU/Linux, kernel 2.6.18-5-686 (on /dev/hdc4)
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.18-5-686 root=/dev/hdc4 ro 
initrd        /boot/initrd.img-2.6.18-5-686
savedefault

title        Debian GNU/Linux, kernel 2.6.18-5-686 (single)(on /dev/hdc4)
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.18-5-686 root=/dev/hdc4 ro single
initrd        /boot/initrd.img-2.6.18-5-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1









=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sdb2: Location of files loaded by Grub: ===================


  43.8GB: boot/grub/menu.lst
  43.8GB: boot/grub/stage2
  43.8GB: boot/initrd.img-2.6.18-4-686
  43.8GB: boot/initrd.img-2.6.18-4-686.bak
  43.7GB: boot/initrd.img-2.6.18-6-686
  43.7GB: boot/initrd.img-2.6.18-6-686.bak
  43.7GB: boot/vmlinuz-2.6.18-4-686
  43.7GB: boot/vmlinuz-2.6.18-6-686
  43.7GB: initrd.img
  43.7GB: vmlinuz

=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
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
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=dbbd7633-9e49-4ee7-9a3b-ca0b8615c510 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=dbbd7633-9e49-4ee7-9a3b-ca0b8615c510 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dbbd7633-9e49-4ee7-9a3b-ca0b8615c510 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dbbd7633-9e49-4ee7-9a3b-ca0b8615c510 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dbbd7633-9e49-4ee7-9a3b-ca0b8615c510
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 54cc3f23cc3efeb4
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Debian GNU/Linux (4.0) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 7b7f32c9-8a72-4d95-b306-1b8aa6a803b2
    linux /boot/vmlinuz-2.6.18-4-686 root=/dev/sdb2
    initrd /boot/initrd.img-2.6.18-4-686
}
menuentry "Debian GNU/Linux (4.0) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 7b7f32c9-8a72-4d95-b306-1b8aa6a803b2
    linux /boot/vmlinuz-2.6.18-6-686 root=/dev/sdb2
    initrd /boot/initrd.img-2.6.18-6-686
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=dbbd7633-9e49-4ee7-9a3b-ca0b8615c510 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=37ad2fd5-37c1-4b14-ab19-328d62299756 none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


  77.5GB: boot/grub/core.img
  77.6GB: boot/grub/grub.cfg
  77.6GB: boot/initrd.img-2.6.32-21-generic
  77.5GB: boot/initrd.img-2.6.32-23-generic
  77.6GB: boot/vmlinuz-2.6.32-21-generic
  77.5GB: boot/vmlinuz-2.6.32-23-generic
  77.5GB: initrd.img
  77.6GB: initrd.img.old
  77.5GB: vmlinuz
  77.6GB: vmlinuz.old
```

---

### Post by QLee on 2010-07-09
[QUOTE=kazordoon]ok, here is RESULTS.txt. Please advise:[/QUOTE]

I hope you realise that Etch has reached end of life in Feb., one year after it was superseded by Lenny, there aren't any more security upgrades so it isn't advisable to use it. It's your choice on that.

You've hit the problem of the different way old kernels enumerate partitions (drives), frankly, my opinion is that it's not worth fixing for an Etch install. That's my advice.

---

### Post by kazordoon on 2010-07-09
thanks for your answer. yes, i just realised where the problem was. ubuntu calls /dev/sdb2 what debian calls /dev/hdc2.

Ubuntu:
```
menuentry "Debian GNU/Linux (4.0) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 7b7f32c9-8a72-4d95-b306-1b8aa6a803b2
    linux /boot/vmlinuz-2.6.18-6-686 root=[COLOR=Red]/dev/sdb2[/COLOR]
    initrd /boot/initrd.img-2.6.18-6-686
}
```Debian:
```
title        Debian GNU/Linux, kernel 2.6.18-6-686 (on /dev/hdc2)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.18-6-686 root=[COLOR=Red]/dev/hdc2[/COLOR] ro 
initrd        /boot/initrd.img-2.6.18-6-686
savedefault
```I changed these two letters and everything is fine now.
About Etch being obsolete...I know, but I have too many things on that partition and little time for updates :(

---

