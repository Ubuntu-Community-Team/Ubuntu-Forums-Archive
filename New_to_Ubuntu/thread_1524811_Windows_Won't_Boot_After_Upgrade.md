---
title: "Windows Won't Boot After Upgrade"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-05
I just finished upgrading ubuntu on my desktop. During the upgrade, I was prompted to either keep the current installation of grub or install the newest version, and I chose to reinstall it. It asked which partitions to "run grub" for, and I wasn't sure which to choose, so I followed its suggestion of selecting all the options. This didn't work, so I selected sda sda1 and sda5 (I think), and then it was able to finish the installation. When the upgrade finished, however, I tried to boot windows and it kicked me back to the grub boot menu.

I was able to boot ubuntu, thankfully, so I tried to reinstall grub through synaptic package manager. This time I didn't choose SDA (which was the entire hard drive) and instead just chose both partitions.

This didn't change anything: I could boot ubuntu but not windows. So I went back into synaptic pacakage manager and completely removed grub and then reinstalled it. This borked grub. I couldn't even boot ubuntu any longer.

So here's my plea to you. Can I fix grub from a live cd and be able to boot into ubuntu and windows again? If so, how?

---

### Post by kingbirdy on 2010-07-05
do you have a CD for windows or was it preinstalled?

---

### Post by EnigmaticCoder on 2010-07-05
Yes, I have a CD for Windows XP. (However, I don't want to reinstall Windows, if that is, indeed, what you're suggesting)

---

### Post by marshmallow1304 on 2010-07-05
On [this guide]("http://ubuntuforums.org/showthread.php?t=1195275"), see **13. Reinstalling GRUB 2 from LiveCD**.

---

### Post by wilee-nilee on 2010-07-05
Before running any commands post the boot script in my signature in code tags as described.

---

### Post by EnigmaticCoder on 2010-07-05
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 270344315 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,410,239   268,410,177   7 HPFS/NTFS
/dev/sda2         268,414,020   488,392,064   219,978,045   5 Extended
/dev/sda5         268,414,083   482,383,754   213,969,672  83 Linux
/dev/sda6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ABC1981BC195939                       ntfs                                     
/dev/sda5        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd   ext4                                     
/dev/sda6        882e7114-18bd-42d4-a93f-ebfc4d6819e5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

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
# kopt=root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd

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

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
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
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
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
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5abc1981bc195939
    drivemap -s (hd0) ${root}
    chainloader +1
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=882e7114-18bd-42d4-a93f-ebfc4d6819e5 none swap sw 0 0
/dev/scd1 /media/cdrom2 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/5ABC1981BC195939 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 138.4GB: boot/grub/core.img
 138.4GB: boot/grub/grub.cfg
 138.3GB: boot/grub/menu.lst
 138.2GB: boot/initrd.img-2.6.31-17-generic
 138.4GB: boot/initrd.img-2.6.31-19-generic
 138.7GB: boot/vmlinuz-2.6.31-17-generic
 143.7GB: boot/vmlinuz-2.6.31-19-generic
 138.4GB: initrd.img
 138.2GB: initrd.img.old
 143.7GB: vmlinuz
 138.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by wilee-nilee on 2010-07-05
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  **Grub 2 is installed in the boot sector of sda1 and **
                       looks at sector 270344315 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Grub is installed in the Windows partition, use this link to clean it out install the testdisk program and follow the instructions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Grub if asked only goes to the master boot record in this case it would have been sda only no numbers which are partition #'s

---

### Post by EnigmaticCoder on 2010-07-05
Worked like a charm. And it seems that ubuntu could boot before that, but it's taking longer and spitting out a message right after the grub menu screen mount: 

```
mounting none on /dev failed no such device
```

Any idea how to iron out this last issue?

---

### Post by wilee-nilee on 2010-07-05
> **EnigmaticCoder said:**
> Worked like a charm. And it seems that ubuntu could boot before that, but it's taking longer and spitting out a message right after the grub menu screen mount: 

```
mounting none on /dev failed no such device
```

Any idea how to iron out this last issue?

Your not saying whether Ubuntu can boot, if it does just run.
```
sudo update-grub
```

I sometimes see stuff flash on the screen about stuff not being read but if it boots regularly and I have stuff setup correctly I don't pay attention to this.

If your not getting a boot into Ubuntu state this.

I suspect it was booting faster before because it was bypassing the borked windows boot file, how long does it actually take to boot?

---

### Post by EnigmaticCoder on 2010-07-05
Ubuntu boots.

Apparently the error I mentioned was not related to grub. It occurs because the distro upgrade failed halfway through (I was able to finish via command line). I'm trying to download the latest kernal to solve this problem.

Thanks for your help.

(Note: I'm going to keep the as unsolved in case I need help installing the latest kernal. When it works I'll mark this thread as solved.)

---

