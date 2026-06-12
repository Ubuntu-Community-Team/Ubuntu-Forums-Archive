---
title: "Accidently removed vmlinuz from /boot directory"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2009-06-16
I managed to accidently remove ALL my vmlinuz and initrd form my /boot directory, and now I cannot boot the system. :(

I have the live CD and dual boot XP so I am able to still see my 8.04 ( hardy ) partition.

How do I reinstall vmlinuz and initrd into /boot so I can get my system booted

---

### Post by PmDematagoda on 2009-06-16
> **Ducatiboy Stu said:**
> I managed to accidently remove ALL my vmlinuz and initrd form my /boot directory, and now I cannot boot the system. :(

I have the live CD and dual boot XP so I am able to still see my 8.04 ( hardy ) partition.

How do I reinstall vmlinuz and initrd into /boot so I can get my system booted

Do you have the Ubuntu 8.04 live CD? If so, you could mount /boot on the live CD session with:-
```
sudo mkdir /media/boot-1
```
and
```
sudo mount /path/to/boot /media/boot-1
```
after mounting the /boot partition, you should be able to simply copy over the vmlinuz and initrd files from the live CD's /boot directory to the one in your 8.04 install.

Edit:- You probably may have to edit the menu.lst file later, but first let's just get the files.

---

### Post by SOULRiDER on 2009-06-16
I dont know if this is helpful, but I believe (i am not sure) that you can chroot into your existing installation from a LiveCD and reinstall a kernel. I did this a while ago when installing Gentoo. The Gentoo handbook is here:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1)
Go tot he section where it says: "Entering the new Environment"

Basically, mount your root partition to say: /mnt/ubuntu and then do:
```
chroot /mnt/ubuntu /bin/bash
source /etc/profile
```

Then try to reinstall a kernel using aptitude.

Someone with more experience might be able to help you further, good luck!

---

### Post by Ducatiboy Stu on 2009-06-16
I was able to copy the vmlinuz file acrross but there was no initrd file that I coould find in the "live CD" file system in /boot

I tried to do a chroot and ugrade that way, but it did not install vmlinux or intrd in my HDD /boot, and  there was still no initrd file on the live CD file system, although the was the latest kernel upgrade..


initrd.img-2.6.24-16-generic is what I require for grub to boot the system..

---

### Post by tgalati4 on 2009-06-17
I believe initrd is compiled as a custom binary for your machine.

Back up your data using the live cd and reinstall.  Had you kept your backup kernels you would still  be able to boot.

Some file system damage is tough to recover from.

---

### Post by nandemonai on 2009-06-17
> **SOULRiDER said:**
> I dont know if this is helpful, but I believe (i am not sure) that you can chroot into your existing installation from a LiveCD and reinstall a kernel. I did this a while ago when installing Gentoo. The Gentoo handbook is here:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1)
Go tot he section where it says: "Entering the new Environment"

Basically, mount your root partition to say: /mnt/ubuntu and then do:
```
chroot /mnt/ubuntu /bin/bash
source /etc/profile
```

Then try to reinstall a kernel using aptitude.

Someone with more experience might be able to help you further, good luck!

That should work fine.

Shouldn't need to reinstall.

---

### Post by Ducatiboy Stu on 2009-06-17
I have manged to chroot but when I go to use synaptics i get the following

```
ubuntu@ubuntu:~$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# source /etc/profile
root@ubuntu:/# synaptic

(synaptic:10180): Gtk-WARNING **: cannot open display: :0.0
root@ubuntu:/# ls
bin   cdrom  etc   initrd  lost+found  mnt  opt   Recycled  sbin  sys  usr
boot  dev    home  lib	   media       Nec  proc  root	    srv   tmp  var
root@ubuntu:/# cd boot
root@ubuntu:/boot# ls
abi-2.6.24-16-generic	      initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic	      memtest86+.bin
config-2.6.24-16-generic      System.map-2.6.24-16-generic
config-2.6.24-19-generic      System.map-2.6.24-19-generic
grub			      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic
root@ubuntu:/boot# 


```
I manged to apt-get install 2.6.24-19 kernell, but when I boot it goeas into a safe mode without any network conection or mouse and a safe mode grapfics

I dont really want to re-install as there are several programs that have taken a while to set up

---

### Post by PmDematagoda on 2009-06-17
> **Ducatiboy Stu said:**
> I have manged to chroot but when I go to use synaptics i get the following

```
ubuntu@ubuntu:~$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# source /etc/profile
root@ubuntu:/# synaptic

(synaptic:10180): Gtk-WARNING **: cannot open display: :0.0
root@ubuntu:/# ls
bin   cdrom  etc   initrd  lost+found  mnt  opt   Recycled  sbin  sys  usr
boot  dev    home  lib	   media       Nec  proc  root	    srv   tmp  var
root@ubuntu:/# cd boot
root@ubuntu:/boot# ls
abi-2.6.24-16-generic	      initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic	      memtest86+.bin
config-2.6.24-16-generic      System.map-2.6.24-16-generic
config-2.6.24-19-generic      System.map-2.6.24-19-generic
grub			      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic
root@ubuntu:/boot# 


```
I manged to apt-get install 2.6.24-19 kernell, but when I boot it goeas into a safe mode without any network conection or mouse and a safe mode grapfics

I dont really want to re-install as there are several programs that have taken a while to set up

Can you go back to the live CD, mount the /boot partition and post the output of the /boot/grub/menu.lst file?

---

### Post by Ducatiboy Stu on 2009-06-17
```

root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
1otgmenu.lst   fat_stage1_5	  menu.lst~		  splashimages
default        installed-version  menu.lst.081209090518~  stage1
device.map     jfs_stage1_5	  minix_stage1_5	  stage2
e2fs_stage1_5  menu.lst		  reiserfs_stage1_5	  xfs_stage1_5
root@ubuntu:/boot/grub# 

```

Menu.lst

```
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

# timeout		10



## hiddenmenu

# Hides the menu by default (press ESC to see the menu)

#hiddenmenu



Pretty colours

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

# kopt=root=UUID=16f0181f-b447-41cd-9da5-ce3c1e87207d ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd0,4)



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



title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16f0181f-b447-41cd-9da5-ce3c1e87207d ro quiet splash

initrd		/boot/initrd.img-2.6.24-19-generic

quiet

 

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16f0181f-b447-41cd-9da5-ce3c1e87207d ro single

initrd		/boot/initrd.img-2.6.24-19-generic



title		Ubuntu 8.04.1, kernel 2.6.24-16-generic

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16f0181f-b447-41cd-9da5-ce3c1e87207d ro quiet splash

initrd		/boot/initrd.img-2.6.24-16-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16f0181f-b447-41cd-9da5-ce3c1e87207d ro single

initrd		/boot/initrd.img-2.6.24-16-generic



# title		Ubuntu 8.04.1, memtest86+

# root		(hd0,4)

# kernel		/boot/memtest86+.bin

# quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

# title		Other operating systems:

# root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

# title		Dell Utility Partition

# root		(hd0,0)

# savedefault

# makeactive

# chainloader	+1





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title		Microsoft Windows XP Professional

root		(hd0,1)

savedefault

makeactive

chainloader	+1


```

---

### Post by Ducatiboy Stu on 2009-06-18
Woooooaaaaahhhhooooo:p

I got it working

when I chroot from the live CD I did "apt-get install linux-image2.6.24-22-generic" which it did, and also updated the Grub menu, then restarted with an fsck and it all came up nicely and fully functional


Thanks guys...owe you big time...

---

