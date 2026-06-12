---
title: "[SOLVED] Repartition drive for dual-boot with windows"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by walawa on 2009-01-05
Hello,
I am currently running ubuntu 8.10 on an intel pc. I would like to repartition my hard drive so I can make a separate partition to install windows on and a small shared partition. Is there a way of doing this without affecting my current ubuntu setup and personal files? I've heard of using a gparted liveCD but I'm not sure how to do this. What format should I use for the windows partition and the shared one? I do not need a large amount spare space for windows so what is the minimum amount necessary for it's installation?

I've also heard of problems with grub if windows is installed after ubuntu and that it can be fixed with an ubuntu liveCD but I'm not entirely sure how to follow the instructions given here: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu) .

Thank you

---

### Post by Hospadar on 2009-01-05
First off, any ubntu livecd has gparted. once you boot off the livecd, Alt+F2, type "sudo gparted"
gparted is real easy and straigtforward to use.

you'll want to shrink Your ubuntu partition(s) to leave a big enough free space for windows. then install windows into that free space (in the windows installer, make a new partition in that free space)

windows will overwrite GRUB, so you'll need to re-install it with a livecd, using the terminal.

boot off a livecd, then Applications->Accessories->Terminal

now install grub, here are some more straightforward instructions: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by kestrel1 on 2009-01-05
It certainly is easier to install Windows first then Ubuntu, but follow the instructions from the link above you should be OK.
I would personally have a minimum of 15gb for the Windows partition & that would be best formated as NTFS. If you want a partition that both Windows & Ubuntu can read/write to I would also use NTFS to format it. The size of this partition is up to you, just depends on what you are going to have on there.
Gparted is easy enough to use, but make sure you have backed up your important data first.

---

### Post by walawa on 2009-01-05
Thank you for your tips. I'll give it a try and post again if I run into any problems.

---

### Post by bwallum on 2009-01-05
I'm sure you can get Windows onto your current harddrive...but in my experience all goes well until Windows (or more precisely a virus or anti-virus software) makes Windows jib. Then it is a nightmare to get both partitions up and running again, especially if you are running master boot record protection software in the Windows environment. 

I have concluded after many attempts that the best way to dual boot a pc for long term stability is to have seperate hard drives for each operating system. A bitter lesson from hard experience...

---

### Post by walawa on 2009-01-06
So I repartitioned the drive and installed windows without any problem. After that only windows booted, as expected, so I used the liveCD to fix grub. But that didn't work very well. On boot grub said error 17: can't mount partition. In grub's menu I had choices like ubuntu or recovery mode but no windows. I did some research and fixed this by editing /boot/grub/menu.lst. Now I can boot into ubuntu, but windows isn't recognized by grub and doesn't appear in it's menu. When I edited menu.lst I noticed there was no stanza for windows. Could this be the problem? How do I fix it?

---

### Post by Zeroberry on 2009-01-06
Can't help you further than suggesting you reinstall GRUB. It is supposed to auto-detect Windows, which it obviously hasn't.

---

### Post by kestrel1 on 2009-01-07
Post your menu.lst as it stands.
Sounds like the listing for Windows needs inputing.

---

### Post by walawa on 2009-01-07
Here's my menu.lst:

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
# kopt=root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e7b0cb86-87db-4a9a-b67a-801b0566d831 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by caljohnsmith on 2009-01-07
Please also post the output of:
```
sudo fdisk -lu
```
And identify which is your Windows partition. Then we can get a better idea of what entry to add to your Grub menu to boot Windows.

---

### Post by walawa on 2009-01-07
fdisk -lu gives the following:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        20964825   444791654   211913415   83  Linux
/dev/sda3   *   444791655   476246924    15727635    7  HPFS/NTFS
/dev/sda4       476246925   488392064     6072570    5  Extended
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris
```

Windows partition is sda3.

---

### Post by caljohnsmith on 2009-01-07
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom of that file:
```
title Windows XP
root (hd0,2)
chainloader +1
```
Reboot, select Windows XP from the Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by walawa on 2009-01-07
Thanks! Windows appeared in the boot menu and it booted fine.

---

### Post by kestrel1 on 2009-01-08
Can you mark the thread as solved please.

---

