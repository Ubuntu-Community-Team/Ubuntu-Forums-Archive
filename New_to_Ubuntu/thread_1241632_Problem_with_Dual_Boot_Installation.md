---
title: "Problem with Dual Boot Installation"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by misterspiffy on 2009-08-16
I just installed Ubuntu.  I selected the option to create partitions and dual boot with ubuntu and vista, however when I start it does not give the option to boot into windows...it just boots right into ubuntu.  I can see by looking at places/computer/filesystem that ubuntu is only taking up 250 Gigs of a 300 Gig harddrive so it seems clear that the installation created a 50 gig partition for vista (well clear to me with my beginning knowledge of ubuntu).  I was reading through another post (I'm Toast) and downloaded the recovery remix to try to edit the "grub" settings, however, I have no clue as to how to use command line in ubuntu.  Is there an easier to "turn on" the dual boot?  I guess I would just like to know how to enable the option to dual boot as it said it would give in the ubuntu literature.

Thanks in advance.

---

### Post by presence1960 on 2009-08-16
Boot into Ubuntu and go Applications > Accessories > Terminal. When terminal opens copy and paste this command in there ```
sudo fdisk -l
``` if you type it that is a lowercase L at the end. Hit enter, it will prompt for password. Type password, you will not see any characters when typing password for security reasons. Post the output of that command back here.

Next run in terminal ```
cat /boot/grub/menu.lst
``` 
Post that output also back here.

After looking at that info it should be a one step process to get windows in the GRUB menu for you at boot.

Terminal is your friend, it is a powerful tool. Most of us felt the same way about terminal, but we learned how to use it. If we can do it so can you, but remember that Rome was not built in a day. For now you can copy/paste those commands into terminal.

---

### Post by misterspiffy on 2009-08-16
Ok, when I boot up with P Magic and look at the partitions, there are three.  One is 276g for ubuntu main installation.  And there are two 5 g partitions, one for linux swap and one for linux extension (I hope I said that correctly..I am going from memory).  I guess I don't understand this.  My drive is 300g and while I know you sacrifice some of the space for overhead, there there still seems to be almost 20g missing.  In other words, perhaps it is not showing the windows partition or maybe there is no windows partition.  I read up carefully on the instructions for installation and selected the 2nd option for installing ubuntu which the guide said would create the partitions for me automatically.

Any assistance would be appreciated.  Thanks.

---

### Post by misterspiffy on 2009-08-16
With the first command I get this:

misterspiffy@misterspiffy-laptop:~$ sudo fdisk -1
[sudo] password for misterspiffy: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
misterspiffy@misterspiffy-laptop:~$ 

With the second command I get this:

## ## End Default Options ##

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=c3376f60-f06e-4531-9293-c89af80005bd ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=c3376f60-f06e-4531-9293-c89af80005bd ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by presence1960 on 2009-08-16
I guess you didn't read thoroughly that is ```
sudo fdisk -l
``` That is a lowercase L at the end not the number 1. Run that command and post the output

---

### Post by misterspiffy on 2009-08-16
Edit.  Sorry I did not copy and past everything from the second command.  Here it is in it's entirety:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeaadbab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       35725   286961031   83  Linux
/dev/sda2           35726       36481     6072570    5  Extended
/dev/sda5   *       35726       36481     6072538+  82  Linux swap / Solaris
misterspiffy@misterspiffy-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=c3376f60-f06e-4531-9293-c89af80005bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=c3376f60-f06e-4531-9293-c89af80005bd ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=c3376f60-f06e-4531-9293-c89af80005bd ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by misterspiffy on 2009-08-16
> **presence1960 said:**
> I guess you didn't read thoroughly that is ```
sudo fdisk -l
``` That is a lowercase L at the end not the number 1. Run that command and post the output

My apologies.  Here it is:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeaadbab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       35725   286961031   83  Linux
/dev/sda2           35726       36481     6072570    5  Extended
/dev/sda5   *       35726       36481     6072538+  82  Linux swap / Solaris
misterspiffy@misterspiffy-laptop:~$ sudo fdisk -l

---

### Post by presence1960 on 2009-08-16
```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeaadbab9

Device Boot Start End Blocks Id System
/dev/sda1 1 35725 286961031 83 Linux
/dev/sda2 35726 36481 6072570 5 Extended
/dev/sda5 * 35726 36481 6072538+ 82 Linux swap / Solaris
```

I regret to inform you that you must have chosen the use entire disk option. Your windows is gone as you can see from your partition table above. Hopefully you practiced good computer habits and made backups regularly.

Don't feel too bad a lot of us do this on the first time trying Ubuntu. I did it, but I had everything backed up. Still do to this day. I backup every weekend.

---

### Post by presence1960 on 2009-08-16
you have parted magic. Boot that and try test disk. if you have photos you want to recover try photorec. Do not boot into the hard disk as you will destroy any chance of recovering your data. I have to be honest though, you may not be able to recover anything or only a little...sorry.

---

### Post by misterspiffy on 2009-08-16
Well it looks like onto data recovery now.  I didn't backup.  I will never make this mistake again.  I'd like to recover my mp3s (over 20gigs) and photos.  Everything else is replaceable.  So far I like ubuntu.  It's very fast.  I don't even care to restore vista to be honest as I absolutely hate it.

Any options to recover that data?  I have an external HDD at my disposal (yeah I know I should have used it in the first place ](*,)).

Thanks again.

---

### Post by LewRockwell on 2009-08-16
> **presence1960 said:**
> ```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeaadbab9

Device Boot Start End Blocks Id System
/dev/sda1 1 35725 286961031 83 Linux
/dev/sda2 35726 36481 6072570 5 Extended
/dev/sda5 * 35726 36481 6072538+ 82 Linux swap / Solaris
```

I regret to inform you that you must have chosen the use entire disk option. Your windows is gone as you can see from your partition table above. Hopefully you practiced good computer habits and made backups regularly.

Don't feel too bad a lot of us do this on the first time trying Ubuntu. I did it, but I had everything backed up. Still do to this day. I backup every weekend.

definitely back-ups, clones, and long-term media storage options(CD/DVD/etc) are the way to go!

.

---

