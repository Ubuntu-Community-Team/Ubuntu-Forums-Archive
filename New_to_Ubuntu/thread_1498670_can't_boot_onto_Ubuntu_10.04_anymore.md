---
title: "can't boot onto Ubuntu 10.04 anymore"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by arnoldiibus on 2010-06-01
Hi there,

First let me apologize for my English as i am french

I'm a new linux user and i don't really know my way around as much as i want to especially with the terminal..
I use Ubuntu on a old HP Pavillon 712A..nothing fancy. It is a dual boot pc with Windows XP on a40 gb hdd and Ubuntu on a 160gb hdd with grub 2 as my boot loader.

Everything was fine for a couple of weeks apart for a few times where ubuntu would freeze and let me no other choice but switch off the pc manually as i couldn't do anything.

I recently updated to Ubuntu 10.04 using Gnome and KDE. One day i decided to get rid of KDE as i don't use it, so i deleted it from the ubuntu software center and i even try a command line, but still no luck KDE was still here. I then try to delete it from the synaptic Package manager, it started fine but ended up freezing, my screen went black and the cursor disapeared....
it stayed like that for about 30mns, i didn't know what to do so i switched off the pc, can't remenber if i unplugged it or press the start button...

since that day, i cannot boot into ubuntu, the loading phase never stop.
grub 2 is working, windows xp too.
one day i even left my pc on all day trying to load ubuntu and it didn't work...

i don't really want to install ubuntu again as i spent a lot of time making it look the way i want, i've got games too. It would be a pain to do it again, a already did it 2 times

what do you guys think? can somebody please help me with that?
i'm really enjoying linux it's way more fun than windows!!:P

Thanks
Arnold
PS: i have an other question: how can i unmount a dingoo A320 in Linux the same way as in windows, i'm always scare to loose data, my dingoo freeze and i have to use a pin to reset it..

PPS: here is my Results.txts in case you need it:
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007f35

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,511,889   300,511,827  83 Linux
/dev/sda2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xda2591eb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    66,027,149    66,027,087   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fca43d6a-8684-4d11-95a3-0be5daf554be   ext4                                     
/dev/sda5        cfec8679-f02a-4a5d-9709-abc5756b82b3   swap                                     
/dev/sdb1        9A1C02921C026999                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fca43d6a-8684-4d11-95a3-0be5daf554be

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Chainload into GRUB 2
root        fca43d6a-8684-4d11-95a3-0be5daf554be
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        fca43d6a-8684-4d11-95a3-0be5daf554be
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
search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
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
search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fca43d6a-8684-4d11-95a3-0be5daf554be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fca43d6a-8684-4d11-95a3-0be5daf554be
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9a1c02921c026999
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fca43d6a-8684-4d11-95a3-0be5daf554be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cfec8679-f02a-4a5d-9709-abc5756b82b3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .3GB: boot/grub/grub.cfg
   5.0GB: boot/grub/menu.lst
   1.0GB: boot/initrd.img-2.6.31-20-generic
   1.3GB: boot/initrd.img-2.6.32-21-generic
   1.8GB: boot/initrd.img-2.6.32-22-generic
    .6GB: boot/vmlinuz-2.6.31-20-generic
   1.0GB: boot/vmlinuz-2.6.32-21-generic
    .8GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: initrd.img
   1.3GB: initrd.img.old
    .8GB: vmlinuz
   1.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by Lampi on 2010-06-01
what happens if you choose the ubuntu recovery mode in grub2?

---

### Post by arnoldiibus on 2010-06-01
wow! that was quick:)
 
i've got several recovery mode...
 
ubuntu with linux 2.6.32.22 generic recovery mode
''          ''       ''    2.6.32.21   ''        ''             ''
''         ''         ''   2.6.31.20
 
 
when linux used to work, i would use the first one (2.6.32.22)
 
when i choose the recovery mode, i get a menu, i tried everything but i still have the same problem...
 
this is my menu: 
resume
clean
dpkg
failsafex
grub
netroot
root
 
 
what do you think i should try to do?

---

### Post by Lampi on 2010-06-01
try resume - like this you should at least make it to a full terminal

---

### Post by arnoldiibus on 2010-06-01
okay but what do i do next?
 
i don't know what command to use..i really need to learn how to use the terminal
 
any idea?
 
thanks for yopur help by the way

---

### Post by mickwombat on 2010-06-01
Hi,

If you can get to the command line then try this,

>sudo apt-get clean
>sudo apt-get update
>sudo apt-get upgrade

That should fix any broken packages, restore missing dependencies etc.

Provided something actually happend with those commands, just reboot and see what happens.

Good luck

---

### Post by arnoldiibus on 2010-06-01
linux seem to work fine using the terminal but what i want to do is to is to get back to the GUI.
My knowlegde of the terminal is none so if somebody out there know what my problem is, please help me out, i would be really grateful
 
thanks in advance
 
Arnold

---

### Post by wilee-nilee on 2010-06-01
> **arnoldiibus said:**
> okay but what do i do next?
 
i don't know what command to use..i really need to learn how to use the terminal
 
any idea?
 
thanks for yopur help by the way

If you get to the terminal you might just run ```
sudo apt-get install ubuntu-desktop
``` or whatever desktop you want, could be lxde, xubuntu, or others but Ubuntu is fairly straight forward and may get you up and running. There is a website run by one of the mods that has the whole desktop list for adding and removing desktops and all the dependencies. I wouldn't mess with that until your up and running, here is a link.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

The instruction to update and upgrade are a good idea to.

---

### Post by arnoldiibus on 2010-06-01
thanks mickwombat and willee nillee, i'll give it a shot and i'll let you know if it works:)

---

### Post by arnoldiibus on 2010-06-01
:( bad luck for me it didn't work...
don't know what to do now, but i'm not too keen in doing a fresh install and loose everything...
hopefully somebody can help me...i'm patient :)

---

### Post by wilee-nilee on 2010-06-01
> **arnoldiibus said:**
> :( bad luck for me it didn't work...
don't know what to do now, but i'm not too keen in doing a fresh install and loose everything...
hopefully somebody can help me...i'm patient :)

I would bump the thread during the day US time so that others who have a better approach might see whats going on and have some solutions. The good thing is everything you want seems to still be there and at the worse can be pulled out using a live cd and saved for a fresh install if needed. This is not difficult but might require a external hard drive if it is a lot of data or a resizing of the partitioning of the computers hard drive, if needed. If you had any errors running any of the commands in the terminal this will be helpful for others to look at.

---

### Post by mickwombat on 2010-06-01
Try doing from terminal, as root,

#startx

If that doesn't work, then it may given some error messages to point you in the right direction.  Try this one also.

#init 5

Post any output that comes up.

---

