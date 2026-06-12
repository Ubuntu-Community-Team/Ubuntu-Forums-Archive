---
title: "&quot;A disk read error occurred&quot;: AFTER dual boot Ubuntu &amp; XP Install"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-20
Ubunteros!

I just finished installing XP Home Edition and Ubuntu 8.04 as dual boot machine.

XP install went without issues as did 8.04. HOWEVER, When I try to launch XP from the boot-up menu I get:

Starting up . . .

A disk read error occurred

Press Ctrl+Alt+Del to restart

This latter comand brings me back to the boot up menu

When I go to Places->Computer the Windows XP files are in folder called 39.6 GM Media. Yes,my HD is small. Only 80 GB!

Could somebody walk me through what I should do to resolve this problem.

Thank You!

---

### Post by suomalainen on 2009-03-20
If this helps here is info from my

/boot/grub/menu.lst 

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
# kopt=root=UUID=a183239f-87c5-4f81-a3f5-e27aa7a27084 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a183239f-87c5-4f81-a3f5-e27aa7a27084 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a183239f-87c5-4f81-a3f5-e27aa7a27084 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by suomalainen on 2009-03-20
I found this piece of help but not sure if it will work for me or exactly what I must type into terminal.

Any help would be appreciated. Thanks!


ran into this problem when resigning a ntfs partition using ntfsresize from kubuntu 7.04.

Of course, after installing kubuntu, windows xp would not boot and gave the infamous

A Disk Read Error Occurred.
Press Ctrl+Alt+Del

As an interim solution, and found a cdrom which would boot windows: fixntldr.iso.zip seemed to do the trick.

It seems that it is a problem with the geometry combined with the hard coding of the geometry into the partition by windows xp.

The solution I used was this:

sfdisk -d /dev/hda | sfdisk --force -no-reread -H255 /dev/hda
hexedit /dev/hda1 (/dev/hda1 was my windows partition)
[press enter]
7e1a
FF
ctrl-x, "y"

and that's it.

---

### Post by meierfra. on 2009-03-20
> I found this piece of help but not sure if it will work for me or exactly what I must type into terminal.


You might have the same problem. But instead of editing the boot sector manually I suggest to use "testdisk" to do the work for you:


Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:


```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Fat 32 partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot into XP.

(If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and testdisk RebuildBS won't be able to solve your problem)

If this did not solve your problem, come back  here and report any error messages you got.

---

### Post by suomalainen on 2009-03-20
Hello meierfra.!

Where are you downloading this from exactly?

I found one site to install using sudo apt-get install testdisk but it isn't working. It install using different method than what you described.

Also, Can you tell me the command I need to remove the version of testdisk I just installed?

Thanks for your help!!!

---

### Post by suomalainen on 2009-03-20
meierfra.!


Thank You for the information you supplied. I eventually got the version of "testdisk" I installed removed. I found a previous post by You with the necessary link and got your version installed.

I followed your well written instructions and XP now boots as required.

Your the best!!!!!

Thanks for responding as quickly as you did!!!!!

T H A N K  Y O U  A G A I N!!

---

### Post by meierfra. on 2009-03-20
> Where are you downloading this from exactly?


Oops, I had forgotten to insert the link, but the link should be there now.


> I need to remove the version of testdisk I just installed?

No need to remove it. Just run it with

```
sudo testdisk /dev/sda
```

The version I linked is a little bit newer. But the version you installed should work  just fine.
(If you really want to remove it, use "sudo apt-get purge testdisk")

---

### Post by meierfra. on 2009-03-20
Seems our messages crossed in cyberspace.


> I followed your well written instructions and XP now boots as required.

Great. Have fun with XP and Ubuntu.

---

### Post by surml on 2009-04-27
thanx meierfra. !!!

you just saved my day!

---

