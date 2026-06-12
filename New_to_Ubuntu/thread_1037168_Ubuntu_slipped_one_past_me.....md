---
title: "Ubuntu slipped one past me...."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Thilo Kuhlman on 2009-01-11
This really isn't a problem just a nagging inconvenience. A while ago I installed Ubuntu unsuccessfully, Heron, then made another copy, assuming that the CD that was previously tried was corrupted. No, I was wrong. I got Ubuntu  8.04.? on the  system, then installed a slightly different version, still Heron, just different. Now my BIOS asks which three (XP or the two Ubuntu's) to boot, and I'm pretty sure that the other one is taking up space partition wise. They current Ubuntu I am using is on a 10 GB hard drive, the other version is sharing a 40 GB with XP. It says I have 4 GB left on a 40 GB hard drive and no I realize it must be that other Ubuntu. How do I purge it without hurting XP?

       -Thilo

---

### Post by jimmy the saint on 2009-01-11
It is the bootloader asking what OS to boot.  When you install Ubuntu you get two boot entries.  One boots into the main OS while the other will boot into recovery mode.  This is perfectly normal and perfectly ok.  It is similar to booting into safe mode with windows.  If you would like to be double sure, look at the partition table with gparted though.

---

### Post by Thilo Kuhlman on 2009-01-11
I am aware of that, yet there are two sets of them.

---

### Post by ajcham on 2009-01-11
Could you run ```
df
```and```
sudo fdisk -l
``` in a terminal, and post the results.

Also, the contents of /boot/grub/menu.lst would be useful.

---

### Post by Thilo Kuhlman on 2009-01-16
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1              9459136   6734064   2248348  75% /
varrun                  257788       120    257668   1% /var/run
varlock                 257788         0    257788   0% /var/lock
udev                    257788        64    257724   1% /dev
devshm                  257788        24    257764   1% /dev/shm
lrm                     257788     39792    217996  16% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       9459136   6734064   2248348  75% /home/jerry/.gvfs
/dev/sda1             40009848  33984572   6025276  85% /media/XP PRO SYSTEM


and :

Disk /dev/sda: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2307181d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4981    40009851    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1a570ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2491    20008926    7  HPFS/NTFS

Disk /dev/sdc: 10.2 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eab31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1187     9534546   83  Linux
/dev/sdc2            1188        1246      473917+   5  Extended
/dev/sdc5            1188        1246      473886   82  Linux swap / Solaris


I am no sure that displays the 2 extra sets of Ubuntu (i miss-counted).

---

### Post by ajcham on 2009-01-16
Going by that you only appear to have one Ubuntu installation - on sdc.  The other two drives only have Windows partitions.

It's most likely that the second Grub entry is just an older kernel - when you update the kernel in Ubuntu the old one is retained, and remains bootable, in case there are problems with the new one.

I suspect if you attempt booting from the second one you will find yourself at your ordinary desktop, rather than a different installation.

If you post the contents of menu.lst (I should have asked for thatin the first place) that will show us for certain:
```
cat /boot/grub/menu.lst
```

---

### Post by Thilo Kuhlman on 2009-01-17
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
# kopt=root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c497f91a-a0cf-4943-8056-0d2d7137d970 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
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



________________________________________________
There you go. Thanks.

---

### Post by ajcham on 2009-01-17
This confirms what I mentioned in my previous post:
> **Thilo Kuhlman said:**
> 
```
&#8230; &#8230; &#8230;
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic
&#8230; &#8230; &#8230;
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic 
&#8230; &#8230; &#8230;
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic 
&#8230; &#8230; &#8230;
```

Each Ubuntu option (I notice you have three now, rather than two) is related to exactly the same installation (hd2,0).  The top one boots the last updated kernel (2.6.24-23), whereas the others boot older kernels (2.6.24-22 and 2.6.24-19).

Each kernel you have saved does take up some space; 100-200MB if I remember correctly.  If you'd rather get some space back you can remove older kernels using Synaptic. I would recommend, however, that you retain at least one old kernel, in case of problems.

BTW, it is better if you use the CODE tags when posting output like this.  It makes the files more readable, and prevents the forum code incorrectly rendering some of the text as smilies, as can be seen at the top of your menu.lst output.

---

### Post by Thilo Kuhlman on 2009-01-17
Just for the sake of forum solutions...how would I go about doing that?
Thanks.

---

### Post by earthpigg on 2009-01-17
> **Thilo Kuhlman said:**
> Just for the sake of forum solutions...how would I go about doing that?
Thanks.

i'd like to know how to remove old kernels via synaptic as well ;)

---

### Post by cariboo on 2009-01-17
The easiest way, if Syanptic doesn't list the extra kernels as autoremovable, is to select the status button in the lower left, you should see at least one kernel version as autoremovable.

Jim

---

### Post by Thilo Kuhlman on 2009-01-19
Maybe if I delete the partitions with gPart...
Will that work?

---

### Post by louieb on 2009-01-19
> **Thilo Kuhlman said:**
> Maybe if I delete the partitions with gPart...Will that work?
Which partition? If you mean the Ubuntu install partition, then you need to replace Grub 1st or the computer  will just display **grub error ...** when you reboot. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Thilo Kuhlman on 2009-01-19
In gPart it says I have more than one partition on sda. If I just hit delete on gPart would that solve the problem?

---

### Post by ajcham on 2009-01-20
> **Thilo Kuhlman said:**
> In gPart it says I have more than one partition on sda. If I just hit delete on gPart would that solve the problem?

I don't understand - what problem are you now looking to solve? Deleting the partition on sda will remove Windows from your machine - I don't think this is what you want to do.

If the problem is the extra kernels taking up space (this is only a problem if you are in dire need of more space on /) the packages in synaptic that can be removed are **linux-image-2.6.24-19-generic** and **linux-image-2.6.24-22-generic**. As I said, I would still recommend keeping the latter of these installed.

---

### Post by 3rdalbum on 2009-01-20
> **Thilo Kuhlman said:**
> Maybe if I delete the partitions with gPart...
Will that work?

No, I don't think you understand what's being said. There is only one copy of Ubuntu on your computer, but you have two kernels (the basic low-level bit of the system that talks directly to the hardware) installed. This is normal - you have an old one that Ubuntu shipped with, and you have a new one that was pushed out to you through the Update Manager.

When you start up your computer, the boot menu screen gives you the option of booting Ubuntu with the new kernel, or with the old kernel. Both these kernels identify themselves in the boot menu as "Ubuntu". Each of these kernels only takes up about 100 megabytes, so there's not really any need to remove the old kernel unless you are low on disk space. I have three or more kernels installed at the moment due to the Update Manager, but I only ever boot into the newest one.

The kernels are located in the same partition as the rest of your Ubuntu.

---

### Post by Thilo Kuhlman on 2009-01-20
I was thinking that I might up partitioned it so that each Ubuntu has a gig to play with, losing me 2 extra gigs. But I think I see what you are seeing and I analyzed my HDD and they aren't taking up space :)

But, for reference, would gPart free up space if I deleted them?

---

### Post by ajcham on 2009-01-20
> But, for reference, would gPart free up space if I deleted them?

If I understand you correctly, you want to know if you remove an old kernel using Synaptic, will gparted show an increased amount of free space on your / partition, yes?

If so, then yes, removing an old kernel will free up about 100 or so MB on the partition.

If no, could you rephrase the question so I can better understand it.

---

### Post by Thilo Kuhlman on 2009-01-20
Alright cool you kept me from doing something absolutely dumb :)
Thanks.

---

