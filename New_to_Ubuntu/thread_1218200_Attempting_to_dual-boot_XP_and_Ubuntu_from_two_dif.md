---
title: "Attempting to dual-boot XP and Ubuntu from two different HDDs"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by MattTheRicker on 2009-07-20
Hi there. I have been using Ubuntu for almost a week now and I absolutely love it. I still want to use XP for some gaming and a few other things. I am having some problems with the GRUB bootloader thing, though.

I have Ubuntu and XP on two different HDDs. Right now the only way I can load XP is through the BIOS, but I understand that using GRUB would be more efficient. The two hard drives are on my primary IDE - the Ubuntu drive is set as master and the XP drive as slave. I just need to know how to go about making the whole thing work.

Thanks!

---

### Post by philcamlin on 2009-07-20
in the bios set it to load the ubuntu hard drive first infront of the xp hdd :popcorn:

---

### Post by MattTheRicker on 2009-07-20
I did that. When I start it up, it loads Ubuntu by default. I am just wondering if there is a way to use GRUB to make it so that I don't have to go into the BIOS every time I want to boot XP.

---

### Post by ~sHyLoCk~ on 2009-07-20
Can you post your menu.lst ?

---

### Post by MattTheRicker on 2009-07-20
I'm not sure how to pull that up. Can you walk me through it?

---

### Post by ~sHyLoCk~ on 2009-07-20
> **MattTheRicker said:**
> I'm not sure how to pull that up. Can you walk me through it?

I think you just have to modify your XP boot option in the grub menu so that it points to the correct HDD containing XP.

You will find it in /boot/grub/menu.lst

---

### Post by Bucky Ball on 2009-07-20
Open a terminal and type in:

```
gksudo gedit /boot/grub/menu.lst
```Copy that and paste it here, thanks. 

Also, post the result of:

```
fdisk -l
```

:)

---

### Post by MattTheRicker on 2009-07-20
Alright. Here is what my menu.lst says as of right now:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3b708a04-a241-4ef6-84ae-b89dd45c417b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b708a04-a241-4ef6-84ae-b89dd45c417b

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        3b708a04-a241-4ef6-84ae-b89dd45c417b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=3b708a04-a241-4ef6-84ae-b89dd45c417b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        3b708a04-a241-4ef6-84ae-b89dd45c417b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=3b708a04-a241-4ef6-84ae-b89dd45c417b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3b708a04-a241-4ef6-84ae-b89dd45c417b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3b708a04-a241-4ef6-84ae-b89dd45c417b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3b708a04-a241-4ef6-84ae-b89dd45c417b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3b708a04-a241-4ef6-84ae-b89dd45c417b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3b708a04-a241-4ef6-84ae-b89dd45c417b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Bucky Ball on 2009-07-20
You need to add an entry for Windows in there (there isn't one). I do not have a windows machine handy at the moment, but I am sure someone else could chime in with a copy of theirs for you to start with (don't quite remember the syntax).

You need to post the result of 'sudo blkid' or 'fdisk -l' so we can advise as to what you should put in the Windows grub boot entry.

*** Okay, it should look something like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        **(hd0,0)**
savedefault
makeactive
chainloader    +1
```

The part in bold is the part you are going to need to change to match where Windows is installed. This is set for first physical drive, first partition (read 0 = 1). So (hd0,1) is second partition.

(hd1,0) is second physical drive, first partition.

---

### Post by MattTheRicker on 2009-07-20
Result of fdisk -l:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac116

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482351593+  83  Linux
/dev/sda2           60051       60801     6032407+   5  Extended
/dev/sda5           60051       60801     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11ca11c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24791   199133676    7  HPFS/NTFS

---

### Post by Bucky Ball on 2009-07-20
Okay read my last post again. You want (hd1,0).

(hd1,0) = second drive, first partition = sd[B]b1

[/B]That is, if it is on there. I notice you have sdc1 set as a primary partition and NTFS also. Which is it? sdc1 would be (hd2,0)

---

### Post by jeppewinther on 2009-07-20
So, to spell it out, at the bottom of that huge list you posted earlier (/boot/grub/menu.lst), you need to add the following:
```

title Windows XP
 root (hd1,0)
 makeactive
 chainloader +1

```

You should then be able to pick using the Grub boot loader, between a number of Ubuntu kernel versions and Windows XP.

You might want to change the options ```
timeout
``` and ```
hiddenmenu
```. Otherwise you will be stuck with the default behavior, which gives you 3 seconds to press escape to access the Grub boot chooser thing.

---

### Post by MattTheRicker on 2009-07-21
Alright, using the code above, when I select "Windows XP" from the GRUB menu on startup, it gives me white text that says "Starting Up....." and a curser beneath it that will sit and blink ad infinitum. I let it blink for five minutes to see if it would do anything, and it did not. I tried both (hd1,0) and (hd2,0), just in case. Anybody have any ideas? I can just use the BIOS to load XP on the occasions when I want it for something. I would rather use GRUB, if we can get this figured out.

---

### Post by URGettingADull on 2009-07-21
Was your windoze drive previously the master drive? I keep windoze 98 on an old FAT32 that dual boots with my ubuntu on a slave NTFS device, no problems loading either os, I would try a reinstall, because during the install there is a step where after you install the grub boot loader it  checks for other operating systems and prompts you to decide to add them to theboot list nor not. At least it did in the alternate installer i used.

---

### Post by MattTheRicker on 2009-07-21
When I installed Ubuntu, I unplugged the other HDD. It seemed a wise precaution at the time - I guess I was afraid of accidentally reformatting it or something.

---

### Post by URGettingADull on 2009-07-21
well now that you have been through it once i guess the second time around should be easy, and i imagine if you are noobish like me it will be the easiest way to accomplish your dual boot machine.

---

### Post by Bucky Ball on 2009-07-21
Try this with the 'savedefault' added:

```
title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1
```* UPDATE: Ah, just read your post! Not having the other drive plugged in during install, that will be why you are having to write the grub menu.lst yourself and there was no entry. I thought that was a bit unusual! ha. Grub would have picked up the windows install and written it in, boot up no problems (usually).

This is educational and sounds like you are getting pretty close; the alternative would be to plug all drives in and go again. Use manual partitioning when it get to that bit and just avoid the other drive. You will see it there, no problem. NTFS, Ubuntu EXT3, totally different. Hard to mix 'em up. 

Good luck, hang in there and welcome. :)

---

