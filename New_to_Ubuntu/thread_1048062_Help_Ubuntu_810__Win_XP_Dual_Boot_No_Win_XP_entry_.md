---
title: "Help Ubuntu 8:10 / Win XP Dual Boot No Win XP entry in Grub"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by gdbutcher on 2009-01-23
I'm trying to Dual Boot Windows XP and Ubuntu 8:10. (I need XP for work:() whenever I've done it before, it has gone very smoothly but I've been plagued with Grub Boot errors this time round. 

One solution around the Error 18 was to put a small partition at the beginning of the drive but now it boots straight into Ubuntu and doesn't list Windows in Grub.

Theres loads of stuff on Grub Windows MBR but I cant get my head around it. I'm really sorry I'm a noob, Can someone talk me through it??

Output of fdisk -l:-

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000beb86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         127     1020096   83  Linux
/dev/sda2             128       30401   243175905    f  W95 Ext'd (LBA)
/dev/sda5             128        4904    38371221    7  HPFS/NTFS
/dev/sda6            4905        5286     3068383+  82  Linux swap / Solaris
/dev/sda7            5287       30401   201736206   83  Linux

Output of sudo gedit /boot/grub/menu.lst:-

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
timeout		3

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
# kopt=root=UUID=e1e70122-037f-4c31-b3e5-e06e5d249197 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e5c01a59-b33a-43ff-b792-7eee90cde0d1

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e5c01a59-b33a-43ff-b792-7eee90cde0d1
kernel		/vmlinuz-2.6.27-9-generic root=UUID=e1e70122-037f-4c31-b3e5-e06e5d249197 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e5c01a59-b33a-43ff-b792-7eee90cde0d1
kernel		/vmlinuz-2.6.27-9-generic root=UUID=e1e70122-037f-4c31-b3e5-e06e5d249197 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e5c01a59-b33a-43ff-b792-7eee90cde0d1
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e1e70122-037f-4c31-b3e5-e06e5d249197 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e5c01a59-b33a-43ff-b792-7eee90cde0d1
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e1e70122-037f-4c31-b3e5-e06e5d249197 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e5c01a59-b33a-43ff-b792-7eee90cde0d1
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by sleepyjon on 2009-01-23
Windows isn't listed on your menu.lst

It needs to be at the END of your menu.lst, after the automagic. Otherwise it will be overwritten after your next kernel upgrade.

Here's mine:

```

title MS Windows XP Pro 64
root (hd1,0)
savedefault
makeactive
chainloader +1

```

(hd1,0) is the hard drive & partition number that windows is installed on. Hope this helps.

Edit: 

Reading your post again I _THINK_ yours should be:

```

title MS Windows XP 
root (hd1,5)
savedefault
makeactive
chainloader +1

```

---

### Post by cjv8888 on 2009-01-23
or try:

> title MS Windows XP 
root (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by king2007 on 2009-01-23
thanks for the input guys - would be a lot of help for beginners like us when ubuntu created a good bootloader even after installing a new version of windows (version 7) and after installing all the updates and/or newer versions like intrepid ibex

---

### Post by caljohnsmith on 2009-01-23
Gdbutcher, is your Windows on sda5? Because sda5 is a logical partition, not a primary one, and Windows needs to put its boot files in some primary NTFS/FAT partition in order to install. Did you previously have a primary NTFS/FAT partition that you deleted when you install Ubuntu? If so, you probably don't have your Windows boot files any more. 

In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to get Windows booting.

---

### Post by mrbiggbrain on 2009-01-23
> **king2007 said:**
> thanks for the input guys - would be a lot of help for beginners like us when ubuntu created a good bootloader even after installing a new version of windows (version 7) and after installing all the updates and/or newer versions like intrepid ibex


Its actualy not linuxes fault, its microsofts. windows uses the NTLDR bootloader to handle all of its booting needs, where as most OS's follow the same rules (load the kernel, a few other files, then proceed to load yourself)

now we cant really hate microsoft for doing this, but what we can be a little eye rolly at is that MS continues to make it dificult for beginers to use THEIR bootloader to load other OS's, even moreso in vista / windows 7

---

### Post by gdbutcher on 2009-01-24
Many thanks to everyone for your suggestions. You were right caljohnsmith; I had deleted a fat partition with the windows boot files on during installation. Pretty dumb, sorry about that. I really appreciate your help.

After 3 more installs of both XP and Ubuntu I've finally got the Laptop Dual booting again without the Grub 18 errors. 

I used Gparted to set up 3 partitions: 37 GB NTFS for Windows XP Home, 3GB Swap, Remainder as Ext3 for Ubuntu 8:10.

I installed Windows XP Home on the 37 GB Partition. 

Then installed Ubuntu 8:10, I choose manual setup, installing Ubuntu 8:10 and the swap files as above. Setting the Ext3 Ubuntu partition as / 

In the next screen I clicked on "Advanced" . I chose the full name of my hard disk from the list, not hd(0,0), Windows Xp home or the partitions.

I'm still at a complete loss as to why it was so easy before but such a nightmare this time but its sorted now. Thanks very much to everyone for your help! :D

---

