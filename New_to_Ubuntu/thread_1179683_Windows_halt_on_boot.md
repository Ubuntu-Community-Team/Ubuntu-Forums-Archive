---
title: "Windows halt on boot"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Vichfret on 2009-06-05
When I select Windows in the grub it doesn't boot, it says "starting" but it never start I already did the fixmbr. This is my grub

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=68916ace-ffb5-41f3-916b-557ba4202048 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68916ace-ffb5-41f3-916b-557ba4202048 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=68916ace-ffb5-41f3-916b-557ba4202048 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify     (hd0,0)
makeactive
chainloader +1

```

---

### Post by QIII on 2009-06-05
Save a copy of your menu.lst.

In the section for Windows, change the line 

rootnoverify to root.

See if it gives you an Error 15 when you try to boot to Windows.

---

### Post by tommynz1975 on 2009-06-05
starting but dosent??  do you mean its stuck on the  bar that moves right to left???

---

### Post by Vichfret on 2009-06-05
@QIII

I Didn't got any error when I changed rootnoverify to root

@tommynz1975

it does not stuck, it says "Starting up" but it never start to boot windows

---

### Post by QIII on 2009-06-05
OK.

Change menu.lst back.

In the terminal, type

sudo blkid

and post the results.

---

### Post by Vichfret on 2009-06-05
> /dev/sda1: UUID="F49894AE989470BA" TYPE="ntfs" 
/dev/sda2: UUID="68916ace-ffb5-41f3-916b-557ba4202048" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="dbd087f2-7260-48c4-a380-cb58a66766f1" 

here it is

---

### Post by QIII on 2009-06-05
OK.  In the terminal again type

sudo fdisk -l


and post the results.

---

### Post by Vichfret on 2009-06-06
> Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24859   199679886    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           24860       30254    43335337+  83  Linux
/dev/sda3           30255       30515     2096482+  82  Linux swap / Solaris

hmm

---

### Post by QIII on 2009-06-06
Partition problem . . .

/dev/sda1 * 1 24859 199679886 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.

I'm not exactly sure of the fix, but if you search the forum for 

"Partition 1 does not end on cylinder boundary"

you'll definitely find an answer from someone who does.

---

### Post by theProdiKalson on 2009-06-06
> **QIII said:**
> Partition problem . . .

/dev/sda1 * 1 24859 199679886 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.

I'm not exactly sure of the fix, but if you search the forum for 

"Partition 1 does not end on cylinder boundary"

you'll definitely find an answer from someone who does.
what if "someone" didn't have a partition boundary problem?
but had the same issue?
going to try to change rootverify to root and show the results of the thingey u told the guy to type... 

really new and stuck in uBuNtU world trying to find refuge back in my winXP OS but cant boot into it grr...

---

### Post by theProdiKalson on 2009-06-06
so i dont know what this means but i typed sudo blkid into the terminal and got this...

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0917" TYPE="vfat" 
/dev/sda2: UUID="49c04831-a9f6-411f-9707-f62cb054a99d" TYPE="ext2" 
/dev/sda5: UUID="6C2420A82420776C" LABEL="Media" TYPE="ntfs" 
/dev/sda6: UUID="8E88D93188D91893" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="47ec59ee-34d1-418f-abab-6839a1e7a04a" 
```


and this is my fdisk...

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         990     7815622+  83  Linux
/dev/sda3             991        9729    70196017+   f  W95 Ext'd (LBA)
/dev/sda5            1293        3842    20482843+   7  HPFS/NTFS
/dev/sda6            3843        9729    47287296    7  HPFS/NTFS
/dev/sda7             991        1292     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order

```

and finally my GRUB...
```

title    MS Windows XP
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
root (hd0,5)
chainloader    +1
```


so i got all this going on and this is my first few hours using the OS and i NEED to boot back to windows and dont wanna format... where do i go from here???

---

### Post by QIII on 2009-06-06
First, you can probably dispense with the mapping right now, until all else works OK.

In the terminal type   sudo gedit /boot/grub/menu.lst

You will have to supply your sign-on password.

Change 

title    MS Windows XP
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
root (hd0,5)
chainloader    +1

to:

title    MS Windows XP
root (hd0,5)
chainloader    +1


Then, between the root and chainloader line, add:

makeactive

What you should have is this:

title    MS Windows XP
root (hd0,5)
makeactive
chainloader    +1


Give that a try and let us know how it goes.

---

### Post by theProdiKalson on 2009-06-06
ok just tried the new grub entry you gave me and i got 

Error 12 invalid device

---

### Post by theProdiKalson on 2009-06-06
when i type fdisk -l should the windows partition(sda6) have a * to indicate i can boot from it?

I am so lost right now!

---

### Post by QIII on 2009-06-06
Scratch this, please:


>> If the asterisk is in the "boot" column, I believe so.

Give that a whirl. <<

I just took a look back, and the asterisk is not there.

Your master boot record (MBR) may be borked.

Give me a minute and I'll try to find you some info on repairing it.

---

### Post by QIII on 2009-06-06
Try this to fix your MBR


[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

### Post by theProdiKalson on 2009-06-06
I just got the same advise in another thread....
worst mistake ever!!
now i dont have a computer at all and im running off the live cd!!

i used the windows cd to get to recovery console and just typed fixmbr....
then boom the thing doenst boot into anything anymore...
i dont even remember the error i was crying so hard...
well not literally crying just really flustered... so i went to live cd to find out if i can maybe get grub back.... then get that to work with the windows install..

this is the thread i made...
[http://ubuntuforums.org/showthread.php?t=1179742&highlight=punch](http://ubuntuforums.org/showthread.php?t=1179742&highlight=punch)

---

### Post by QIII on 2009-06-06
Gaaaah!

"Frustrating" would be an understatement!

Can you run fdisk -l from the Live CD and let us know how it looks now?

---

### Post by theProdiKalson on 2009-06-06
> **QIII said:**
> Gaaaah!

"Frustrating" would be an understatement!

Can you run fdisk -l from the Live CD and let us know how it looks now?
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         990     7815622+  83  Linux
/dev/sda3             991        9729    70196017+   f  W95 Ext'd (LBA)
/dev/sda5            1293        3842    20482843+   7  HPFS/NTFS
/dev/sda6            3843        9729    47287296    7  HPFS/NTFS
/dev/sda7             991        1292     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by theProdiKalson on 2009-06-06
i read in another thread a million and one ways to get the grub back i am just getting tired.. ubuntu is so much work i hope this is all worth it..

I am on the liveCD right now and typed grub into the terminal and someone said i should just type root (hd0,X) well 1 in my case then setup (hd0,1) to get it back.

i cant get past "root (hd0,1)" though
 
it is saying error 21 disk does not exist but i know it does... could it be that because i am on the LiveCD hd0 coresponds to the cdrom drive and not the hdd on the laptop?

---

### Post by QIII on 2009-06-06
Negative on the CD drive.  sda/hd0 in your menu.lst denote your hard drives.

I hear you about being tired.

This was really worse back in the days when we had to compile our own kernels.

Things have gotten much better.  You are an unfortunate example that nothing works perfectly for everyone.  I'm genuinely sorry, because Ubuntu is really a great product and a great community.

I only made one attempt to create a dual boot on a single physical drive and swore off of it forever.  Others have absolutely no problems whatsoever.

The fixmbr thing is the "official" answer, if there is such a thing.  Others have had great success with it.

It might be best to take a breather tonight, let some responses come in to your posts and start fresh tomorrow.

A fair number of us will keep doing research so we don't leave you hanging.

---

### Post by theProdiKalson on 2009-06-06
your a kool guy man i appriciate it... i might toss the hdd in the blender tomorrow and just go back to winXP...there is so much to do to get everything back when all i can use now is a liveCD...have a good night and thank you so much for your quick replies and effort...
i really do appriciate it

---

### Post by QIII on 2009-06-06
Don't pitch the drive.

You probably have stuff on it you'd like to keep.  There are ways of getting at it.  Ironically, one of them is to get a buddy to slave it off a Linux machine and use several free tools for doing just that...

Use the Live CD as a coaster for your coffee cup.

Hey.  I love Linux and despise Microsoft.  That's me.

But I'm not a Linux evangelist.  Use whatever OS suits your needs.

---

### Post by theozzlives on 2009-06-06
Try fixboot & fixmbr together, that should write windows to your boot sector, then we can work on reinstalling GRUB. Don't use the Live CD as a coaster.[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

---

### Post by QIII on 2009-06-06
I use Microsoft disks for coasters.

And BTW -- Thanks for upholding my promise to Kalson that he wouldn't be left hanging.

---

### Post by Vichfret on 2009-06-06
fixmbr didn't work for me, as I said when I opened the thread... I think it's a problem with this

> [B]The number of cylinders for this disk is set to 30515.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)[/B]

Command (m for help): q
I get that when I run
> sudo fdisk /dev/sda

---

### Post by QIII on 2009-06-06
I'm still trying to research this.

For the time being, can you try to use the Live CD to see if you are able to access your Windows partitions and at least recover any data you may have there to a USB device or something?

I'm not entirely sure how the Live CD will handle file permissions, but please try that.

At the very worst, you'd have your info and you could just call us all a bunch of tweezers, reinstall XP and try again.

(Don't do that yet.  I'm still working on it.  This is something that would be very beneficial to have marked as SOLVED so others don't go through this frustration later.)

---

### Post by Vichfret on 2009-06-08
I can access the windows files I can read/write from my current ubuntu installation. I think I'm going to backup my data and format my hard disk

---

### Post by LewRockwell on 2009-06-08
sorry if I missed where someone suggested this previously(my eyes blurred starting on page three)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

