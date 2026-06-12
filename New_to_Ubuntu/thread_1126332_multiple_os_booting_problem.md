---
title: "multiple os booting problem"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by anthonyleamy on 2009-04-15
Up to recently I had had mint and windows installed on my Pentium 4 pc operating a dual booting system. Wishing however to run Xubuntu as well, I "successfully" installed it on a separate partition on the same hard disk. 
However when I tried to recover from Mint my music collection to copy to Xubuntu, I found that after selecting Mint from the grub window the Mint splash window appears only to be followed by the Xubuntu os.
Is this a Grub defect? Should I reinstall it? And how?
Or have I inadvertently written over my Mint files when installing Xubuntu?


:DOh I really love Xubuntu and would highly recommend it. It loads in a flash and seems very stable. It allows me to connect very easily with my Huawei 3 dongle (sometimes problematical with some distros) The Xfce worktop is very pleasant and efficient to work with. An excellent distro not only for lower spec machines.

---

### Post by jucas_lo on 2009-04-15
Enter Xubuntu, and try rebuilding the grub configuration file

```
sudo update-grub
```

and then again 

```
sudo update-grub
```

If it doesn't work try editing your grub config file:

```
sudo vi /boot/grub/menu.lst
```

Look for the entry for Mint and check if the root for that entry corresponds to the correct partition.

Grub uses a different naming scheme for hard disks and partitions, for instance take:

(hd0,1)

hd0 means that the partitions is in the first hard drive, and 1, is the partition number (beginning with 0).

Post back if you find any trouble. ):P

---

### Post by halitech on 2009-04-15
whats the output of
```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.list
```

---

### Post by bodhi.zazen on 2009-04-15
See this thread :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

lots of tips / advice.

---

### Post by anthonyleamy on 2009-04-15
> **jucas_lo said:**
> Enter Xubuntu, and try rebuilding the grub configuration file

```
sudo update-grub
```

and then again 

```
sudo update-grub
```

If it doesn't work try editing your grub config file:

```
sudo vi /boot/grub/menu.lst
```

Look for the entry for Mint and check if the root for that entry corresponds to the correct partition.

Grub uses a different naming scheme for hard disks and partitions, for instance take:

(hd0,1)

hd0 means that the partitions is in the first hard drive, and 1, is the partition number (beginning with 0).

Post back if you find any trouble. ):P

The teminal gave me the following:

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title           Linux Mint Universal Edition, kernel 2.6.27-7-generic (on /dev/sda5)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
savedefault
boot

Am I right in saying that grub is booting to sda6 the location of Xubuntu rather than sda5?
If so how would you recommend I proceed. I need to recoup my music files before removing Mint.

---

### Post by anthonyleamy on 2009-04-15
> **halitech said:**
> whats the output of
```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.list
```

Here is the output 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4358    35005603+   7  HPFS/NTFS
/dev/sda2            4359       19457   121282717+   f  W95 Ext'd (LBA)
/dev/sda5            7188       15689    68292283+  83  Linux
/dev/sda6           15690       19457    30266428+  83  Linux
/dev/sda7            4359        4844     3903732   82  Linux swap / Solaris

Partition table entries are not in disk order

anthony@anthony-desktop:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory

---

### Post by meierfra. on 2009-04-15
> cat /boot/grub/menu.list

It needs to be

```
cat /boot/grub/menu.[COLOR="Red"]lst[/COLOR]
```

---

### Post by anthonyleamy on 2009-04-15
> **meierfra. said:**
> It needs to be

```
cat /boot/grub/menu.[COLOR="Red"]lst[/COLOR]
```

anthony@anthony-desktop:~$ cat /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=dbe2a278-6576-4599-b9a1-5b16ef311804 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dbe2a278-6576-4599-b9a1-5b16ef311804

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dbe2a278-6576-4599-b9a1-5b16ef311804
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dbe2a278-6576-4599-b9a1-5b16ef311804 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dbe2a278-6576-4599-b9a1-5b16ef311804
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dbe2a278-6576-4599-b9a1-5b16ef311804 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dbe2a278-6576-4599-b9a1-5b16ef311804
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint Universal Edition, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint Universal Edition, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Linux Mint Universal Edition, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

anthony@anthony-desktop:~$

---

### Post by meierfra. on 2009-04-15
If you want to boot into Linux Mint,  open menu.lst in Xubuntu via

```
gksudo mousepad /boot/grub/menu.lst
```

and change

```
title Linux Mint Universal Edition, kernel 2.6.27-7-generic (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
boot
```

to

```
title Linux Mint Universal Edition, kernel 2.6.27-7-generic (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=/[COLOR="Red"]dev/sda5 [/COLOR]ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
boot
```

( so just change /dev/sda6 to /dev/sda5)

But you don't need to boot into Linux Mint to copy the files.

You could just mount /dev/sda5 via

```
mkdir Mint
sudo mount /dev/sda5 Mint
```
and then you can access all the Linux Mint files in the folder "Mint" in your home directory

---

### Post by anthonyleamy on 2009-04-15
The booting problem is now resolved and I have learned how to access my Mint files while working in Xubuntu. Fantastic. Linux is really cool. 
Thanks for the help.):P:-D

---

### Post by meierfra. on 2009-04-16
> The booting problem is now resolved 
Great. Have fun with Ubuntu.

---

