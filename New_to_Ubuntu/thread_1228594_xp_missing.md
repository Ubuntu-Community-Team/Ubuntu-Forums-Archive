---
title: "xp missing"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by greatgk on 2009-08-01
i had xp before installig ubuntu..but i cant boot from it coz at the time machine boots it doesnt show me option...here from terminal i see this..post it because may b u understand what is in my pc
amit@amit-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4e574e56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     2040254     1020096   82  Linux swap / Solaris
/dev/sda2         2040255    25398764    11679255    7  HPFS/NTFS
/dev/sda3        25398765   488375999   231488617+   f  W95 Ext'd (LBA)
/dev/sda5        25398828    51199154    12900163+   7  HPFS/NTFS
/dev/sda6        51199218   108535139    28667961    7  HPFS/NTFS
/dev/sda7       133114653   255995774    61440561    7  HPFS/NTFS
/dev/sda8       255995838   378876959    61440561    7  HPFS/NTFS
/dev/sda9       378877023   488375999    54749488+   7  HPFS/NTFS
/dev/sda10      108535203   133114589    12289693+  83  Linux

Partition table entries are not in disk order
amit@amit-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=5425c4b5-0906-4d41-b7cd-78b256346cb0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5425c4b5-0906-4d41-b7cd-78b256346cb0

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        5425c4b5-0906-4d41-b7cd-78b256346cb0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5425c4b5-0906-4d41-b7cd-78b256346cb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        5425c4b5-0906-4d41-b7cd-78b256346cb0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5425c4b5-0906-4d41-b7cd-78b256346cb0 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5425c4b5-0906-4d41-b7cd-78b256346cb0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5425c4b5-0906-4d41-b7cd-78b256346cb0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5425c4b5-0906-4d41-b7cd-78b256346cb0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5425c4b5-0906-4d41-b7cd-78b256346cb0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5425c4b5-0906-4d41-b7cd-78b256346cb0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




what should i do 2 get my xp back

---

### Post by la3875 on 2009-08-01
What are you trying to do here. Is this the output after trying to install Ubuntu in a dual boot scenario on top of XP?

I recommend you head here for detailed assistance recovering and reinstalling - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Good luck!

---

### Post by greatgk on 2009-08-01
plzzzzzz help

---

### Post by lisati on 2009-08-01
> **la3875 said:**
> What are you trying to do here. Is this the output after trying to install Ubuntu in a dual boot scenario on top of XP?

I recommend you head here for detailed assistance recovering and reinstalling - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Good luck!

> **greatgk said:**
> plzzzzzz help

Is what la3875 is saying correct? Did the link help?

---

### Post by jacklinux on 2009-08-01
Did you install Via hardrive, CD, or something like Wubi installer?

---

### Post by Elfy on 2009-08-01
Might be worth following this - [http://ubuntuforums.org/showpost.php?p=7245321&postcount=5](http://ubuntuforums.org/showpost.php?p=7245321&postcount=5)

That will give us more information.

---

### Post by Sef on 2009-08-01
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     2040254     1020096   82  Linux swap / Solaris
/dev/sda2         2040255    25398764    11679255    7  HPFS/NTFS
/dev/sda3        25398765   488375999   231488617+   f  W95 Ext'd (LBA)
/dev/sda5        25398828    51199154    12900163+   7  HPFS/NTFS
/dev/sda6        51199218   108535139    28667961    7  HPFS/NTFS
/dev/sda7       133114653   255995774    61440561    7  HPFS/NTFS
/dev/sda8       255995838   378876959    61440561    7  HPFS/NTFS
/dev/sda9       378877023   488375999    54749488+   7  HPFS/NTFS
/dev/sda10      108535203   133114589    12289693+  83  Linux

I can see a problem or two.   

1) Windows needs to be on the first primary partition.

2) Why is Linux swap set as the boot?  It should be set to Windows.

---

