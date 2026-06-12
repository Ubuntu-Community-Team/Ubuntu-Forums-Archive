---
title: "A Grave Error on My Part.."
date: 2011-05-09
forum: New to Ubuntu
---

### Post by A Ghost In The Machine on 2011-05-09
I may have let my over eagerness get the best of me this time. Upon installing Ubuntu, it asked me to partition some of the disk. In doing so I may have torn my windows Xp from my system. I selected Ext 2  and Swap, and let 'er rip. The only thing is that the computer says I still have a ton of info on the hard drive, so it leads me to believe that Windows is still there, but how can I get back to it?  Everytime I reboot, it goes straight to Ubuntu. I went to the boot menu at start up, and it only shows my external hard drive, and my HDD as optional boots. I wanted to have a dual boot comp..

---

### Post by calerano on 2011-05-09
Mate the first thing you need to do is tell the forum what Ubuntu you have. So that people have an idea of what is going on. But for what you just said, ext2????? mate that is like 10 years old. we are up to ext4 now. And in reality you don't need to partition anything. Ubuntu will do it for you and will install  next to your WinXp.
Just try again and this time select the "install alongside .........."
by the way, last Ubuntu is 11.04.

---

### Post by Hedgehog1 on 2011-05-09
On the theme of giving us enough info to help you, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by scott-ian on 2011-05-09
Even if you did delete the partition, it may be recoverable, at least some of the data.  I would boot off of a live CD to keep damage to a minimum.  If you did not delete it, you should be able to access the files from your install, or from a live CD.  If you cannot, you probably lost all your data, but you should boot off the live CD and see if the data can be recovered.  I do not know how, but tools are available.  Hopefully it is still there, but don't count on it.

---

### Post by A Ghost In The Machine on 2011-05-10
###

Thanks for the replies so quick...alright here's what I got from the boot info script...Oh and Its ubuntu 11.04.  If you guys could explain this to me, it'd be appreciated. I got some of it, but a lot of it, is still foreign...only first year comp sci major!





```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  HP Recovery
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046   469,927,935   469,925,890   5 Extended
/dev/sda5               2,048   465,868,799   465,866,752  83 Linux
/dev/sda6         465,870,848   469,927,935     4,057,088  82 Linux swap / Solaris
/dev/sda2    *    469,929,600   488,391,119    18,461,520  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        494b1648-2915-4c66-a704-f70af0115809   ext2                                     
/dev/sda5        1aba3527-c6bc-47c1-86a7-a53e04309c92   ext4                                     
/dev/sda6        7c699cc8-65d2-4282-8bd8-574e4ae77152   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        68F003B3F0038712                       ntfs       Xanadu                        
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext2       (rw,errors=remount-ro)
/dev/sdb1        /media/Xanadu            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1aba3527-c6bc-47c1-86a7-a53e04309c92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7c699cc8-65d2-4282-8bd8-574e4ae77152 none            swap    sw              0       0

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 494b1648-2915-4c66-a704-f70af0115809
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video


```

---

### Post by Hedgehog1 on 2011-05-10
> **A Ghost In The Machine said:**
> ... In doing so I may have torn my windows Xp from my system...

Well, your instinct was correct.  XP is no longer a part of your 1st disk drive.

Your install of Ubuntu is also, ummmmm... Creative?

I am assuming you need Windows.  If your PC/Laptop still has the (readable) sticker with the Windows Activation Code/Serial Number, you are legally entitled to reload XP on this computer using your activation code.

Hopefully you have access to XP disks.

May I suggest a more controlled install this time?  It would leave the second 320 gig disk drive untouched (and allow it to be used for common data storage for both Windows and Ubuntu).

The 250 gig disk would look like this:

[B]/dev/sda1 ntfs XP install - 90 gigs ('C:' drive in Windows)
/dev/sda2 ntfs common storage ~ 60 gigs ('D: drive in Windows)
/dev/sda3 Extend partition (to the end of the disk)
__/dev/sda5 ext4 '/' (root) for Ubuntu - 25 gigs
__/dev/sda6 ext4 '/home' for Ubuntu - 60 gigs
__/dev/sda7 Swap (Size of RAM + 10%)[/B]


***The Hedge***

:KS

p.s. If you opt to go all Ubuntu, you can do this:

[B]/dev/sda1 ext4 '/' (root) for Ubuntu - 30 gigs
/dev/sda2 ext4 '/home' for Ubuntu ~ 215 gigs
/dev/sda3 Swap (Size of RAM + 10%)[/B]

---

### Post by deconstrained on 2011-05-10
Your Windows installation is still there, just on a different harddrive.

Press escape while starting up to access the GRUB menu. If it was configured correctly, you should be able to select and boot into Windows. Otherwise, there's more work to be done.

---

### Post by Baldrick_NZ on 2011-05-10
> **deconstrained said:**
> Your Windows installation is still there, just on a different harddrive.

Press escape while starting up to access the GRUB menu. If it was configured correctly, you should be able to select and boot into Windows. Otherwise, there's more work to be done.

+1

Interestingly enough, I came to the same conclusion too Deconstrained. Not sure where Hedgehog was going... lol

---

### Post by yetiman64 on 2011-05-10
> **deconstrained said:**
> Your Windows installation is still there, just on a different harddrive.

Press **escape** while starting up to access the GRUB menu. If it was configured correctly, you should be able to select and boot into Windows. Otherwise, there's more work to be done.

Escape was used for grub legacy it is now the **Shift** key to access the grub menu in grub2.

OP. It does appear you have XP on /dev/sdb1 but I can't see any boot files listed there for it. Something unusual is going on.

I think > Your install of Ubuntu is also, ummmmm... Creative?might be right and you have damaged XP as well. 

If windows was detected by grub the grub bootscreen would be visible and you wouldn't need to use **shift** to bring it up. 

It appears your only bootable install there is /dev/sda2, its is marked as an ext2 partition but its Boot Sector type is HP Recovery :confused:. 

You have overwritten or wrongly set the partition type with the installer by the looks of it.  **Edit**: @ Baldrick_NZ Hedgehog1's suggestions are probably related to this strange setup and would address the current messed up setup. The info shows in the bootscript.

Good luck OP.

---

### Post by A Ghost In The Machine on 2011-05-11
No such luck...when enter the grub menu, the only options are Linux, and a memory scan..nothing about Windows...getting worried..

---

### Post by yetiman64 on 2011-05-11
> sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  [COLOR=Red]HP Recovery[/COLOR]
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.imgWhat was your HP Recovery partition previously with XP, now has an install of Natty over the top of it and is a [COLOR=Red]ext2[/COLOR] partition :-( to say. 

Plus > sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   Note no boot files/dirs for the XP partition.

Hedgehog was previously asking if you have an XP install disc, and if you did has given you a possible way to repartition the drive (less "Creative", as he rather tactfully describes the current lay out).

The second partition layout he gives is for Ubuntu only install if you were to go that way :).

Unless someone with more experience than myself comes along with better suggestions, what I'm seeing here is you needing to do a full cleanout and re-install. I agree with Hedgehogs suggestions either with dual booting or Ubuntu only (however you prefer).

---

### Post by wep940 on 2011-05-11
1 of your partitions is listed as an HP recovery partition.  It would do no good for data and programs you would lose, but you should be able to reinstall Windows using the recovery partition and any disks that may have been included (or that you had to burn).  That would put Windows back.  Then you can go back again and reinstall Ubuntu, following the suggestions others have given.

---

### Post by 3177 on 2011-05-11
If you need windows I hope you have a cd.
you'll need it to fix windows.

---

### Post by Hedgehog1 on 2011-05-11
> **Baldrick_NZ said:**
> Interestingly enough, I came to the same conclusion too Deconstrained. Not sure where Hedgehog was going... lol

The ntfs partition on the second drive is a data only partition (despite the boot flag):

```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs: 
```

If it were an operating system partition, there would have been text following the **Operating System:** & **Boot files/dirs:** titles.

This is, however, a case where I wish I was not correct. ***A Ghost In The Machine*** will need to reinstall XP if it is still needed.

***The Hedge***

:KS

---

### Post by A Ghost In The Machine on 2011-05-11
It's what I was afraid of.. Thanks for the help guys. Can someone explain this whole idea of partitioning though? what exactly is ext 2, 3 and 4? and Swap and ntfs? All these terms are foreign to me. I just want to know so I don't do the same mistake over again..

---

### Post by Hedgehog1 on 2011-05-12
There are any number of way that a disk partition can be formatted.

The 'Legacy Windows' ones are FAT (**F**ile **A**llocation **T**able), typically seen as FAT16 and FAT32.

The 'Newer Windows' method as called NTFS (NT Filed System)

Linux uses the EXT method of formatting.  The 'most current' is EXT4. Legacy formats are EXT3 and EXT2.

Linux has the ability to set aside a 'memory storage on disk' area called 'swap space' (because when used, the PC writes a chink of RAM into it and then reads some other chuck off the same partitions, essentially 'swapping' one chuck for another).

So a partition that is call SWAP is where Linux will store real-time memory data when it runs out of RAM.  It also uses this partition to dump RAM during a suspend, so it can read it up and pick up where it left off when you wake the PC up again.

Extended partitions are a extra partitions that holds more partitions. They are a way to get around the Windows limit of 4 'primary' partitions on a hard disk.

For your purposes, I would suggest a partition layout that looks like this:

```
/dev/sda1 NTFS XP Install
/dev/sda2 NTFS Common partition to share Music and data
/dev/sda3 Extended Partition
__/dev/sda5 EXT4 '/' (root) Ubuntu partition
__/dev/sda6 EXT4 '/home'
__/dev/sda7 SWAP (size of your RAM, Plus 10%)

```


***The Hedge***

:KS

---

### Post by A Ghost In The Machine on 2011-05-14
Any idea where I can acquire another copy of xp? I really can't buy windows 7 right now, its way too much. Am I still entitled to a copy of XP from microsoft?

---

### Post by ClientAlive on 2011-05-14
> **A Ghost In The Machine said:**
> I may have let my over eagerness get the best of me this time. Upon installing Ubuntu, it asked me to partition some of the disk. In doing so I may have torn my windows Xp from my system. I selected Ext 2  and Swap, and let 'er rip. The only thing is that the computer says I still have a ton of info on the hard drive, so it leads me to believe that Windows is still there, but how can I get back to it?  Everytime I reboot, it goes straight to Ubuntu. I went to the boot menu at start up, and it only shows my external hard drive, and my HDD as optional boots. I wanted to have a dual boot comp..


For what it's worth - maybe not much - a friend of mine recently turned me on to this:

[http://www.asrdata2.com/](http://www.asrdata2.com/)

I have never used it so don't know how it works. Someone on this forum may have though or may be more skilled with Linux that they would understand it. Maybe it would help.

Another tool some find useful is this:

[http://clonezilla.org/](http://clonezilla.org/)

I don't know if they can be used in connection with one another or not - or even if they need be. Again, someone on this forum may have though or may be more skilled with Linux that they would understand it. Maybe it would help.

:D

---

