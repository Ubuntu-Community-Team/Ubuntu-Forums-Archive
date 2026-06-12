---
title: "Changed hard drive and now ubuntu won't boot"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by merdok1981 on 2009-05-16
Ok bit of a story to this one.

I had a media center PC which runs Ubuntu 9.04. It was installed on an 80gb hard drive with an additional 750gb hard drive in the PC but (as far as I was aware) not touched by the OS. 

Yesterday my Icybox NAS broke down on me (Power supply failure) and in order to access my media files (which were stored on the NAS in ext2 format) I decided to strip the 1TB drive out of the NAS and replace the blank 750gb drive with that one.

Now Linux will not boot, I get different outcomes depending on the HDD configuration:


[LIST=1]
[*]80gb + 750gb = Boots perfectly
[*]80gb + 1TB = disk boot failure message (regardless of which drive has priority)
[*]750gb + 1TB = message just says 'GRUB'
[*]Just 750gb = Message says 'GRUB hard disk error'
[/LIST]

This seems to suggest to me that for some reason Linux has install essential data to the 80GB AND the 750GB, which is rather annoying.

I don't have a spare SATA slot to add the 1TB hard drive as well as the other two and I have no other way of accessing the data on that drive. 

Any suggestions? I've only been using Linux for a couple of months and I'm not all that accustomed to it yet so if you could dumb your answers down as much as humanly possible that would be great :)

---

### Post by coffeecat on 2009-05-16
Clearly Ubuntu has installed something to the 750G drive, but we need to find out what. Boot up as usual and post the following:

Open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -l
```Also, post the contents of the files /etc/fstab and /boot/grub/menu.lst. If you navigate to them with the file browser and double-click on them, they'll open read-only in a text editor, which is enough to be able to paste them into the reply box. When you do so, please enclose each file in [noparse]```

```[/noparse] tags to keep the formatting.

---

### Post by TJCIB on 2009-05-16
Something definitely is on that second hard drive.

There is a HowTo about grub here [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

Check out the parts about "Changing the Disk Grub is Installed To" and "Reinstalling Grub"

It may be that your /boot directory is on that 2nd hard drive.

Check out the howto

---

### Post by merdok1981 on 2009-05-16
Thank you for replying so quickly :) 

OK, fdisk -l yielded the following information:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e94e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f95b518

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572032   83  Linux

```This is the contents of the fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a29f5061-fa5a-4401-9c9a-e6cdcd0d07c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```and here is the menu.lst file

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
# kopt=root=UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
uuid        64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid        64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, memtest86+
uuid        64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by anewguy on 2009-05-16
Judging by the messages you said you get by trying to boot the different disk configurations, I'd say the mbr on your 750mb disk uses grub, but the OS itself is on the 80gb drive.

I would try the following first:

using the 80gb and 750gb drives, boot normally into Linux.

using the "places" explorer, find your 750gb drive and look to see if anything shows on the drive (be sure you click the show hidden files button).

If nothing shows, I suspect the mbr for booting is on the drive but nothing else, indicating the OS is on the 80gb drive.  To fix this, you would need to install grub to the mbr on the 80gb drive, then remove the 750gb drive.

Dave :)

---

### Post by merdok1981 on 2009-05-16
In places there is a folder called 'Lost + found' which I am unable to access. That is all that shows up.

How do I move my grub then? I took a look at the how to posted earlier but it didnt make a whole lot of sense to me.

---

### Post by NHArticleTen on 2009-05-16
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by coffeecat on 2009-05-16
> **anewguy said:**
> Judging by the messages you said you get by trying to boot the different disk configurations, I'd say the mbr on your 750mb disk uses grub, but the OS itself is on the 80gb drive.

No. Read the output that the OP has posted. It's all there.

**merdock1981**, I don't know what happened when you installed, but it's very odd.

OK. sda is your 80GB drive, sdb is your 750GB drive. Your Linux root partition is sdb1 on the 750GB drive. Your /etc/fstab file is trying to mount a swap partition on sdb5 which doesn't exist. :? The sda partitions on the 80GB drive are completely unused. The only function that sda has is grub stage 1 which is on the mbr. Grub stage 2 is in your sdb1 partition which explains the grub error messages you get.

While you digest that, could you post back with what you remember you did when you installed. Were the drives in a different configuration then?

---

### Post by merdok1981 on 2009-05-16
Yeah the drives were in the exact same configuration, I only did a re-install a few weeks ago so nothing has changed in the interim.

When I installed I selected 'use entire disk (guided)' for the 80gb partition, I figured that this would leave the 750gb drive alone and install everything on the 80gb.

As I only use this as a HTPC it wouldnt be a big stretch to remove the 750gb and just reinstall Jaunty on the 80gb but if there is an easy way to set this right I'd rather do that as I spent a lot of time configuring mythTV and XBMC and the thought of going through all that again makes me feel sleepy :)

---

### Post by merdok1981 on 2009-05-16
In fact, I'd be just as happy to scrap the 80gb and move everything to the 750gb as I was thinking of using my HTPC as a file server anyway. 

Thefore the new configuration would be the primary disk as the 750gb and I'd install the 1tb hard drive as the secondary disk (provided there is a way to do it without losing the data currently on it)

---

### Post by coffeecat on 2009-05-16
> **merdok1981 said:**
> Thefore the new configuration would be the primary disk as the 750gb and I'd install the 1tb hard drive as the secondary disk (provided there is a way to do it without losing the data currently on it)

Yes, you could do this. Remove the 80GB drive and plug the 750GB into the drive 1 SATA connector. It's probably best to leave the 1TB drive out for the time being. Now boot up with a live CD and from the desktop open a terminal, and do:

```
sudo grub
```The prompt will change to the grub one, now do these commands:

```
root (hd0,0)
setup (hd0)
quit
```Obviously, return in between each. Now shutdown from the live CD and you should be able to boot up from the HD. This is the one time that Ubuntu's UUID references in grub's menu.lst and /etc/fstab come in useful.

One problem is that you don't have a swap partition, but you never did anyway. Perhaps we could look at that later once you've got it booting from the 750GB drive. Check that the system boots OK, and then shutdown, fit the 1TB drive and reboot. You should be able to automount it from the Places menu - depending on what filesystem is on it - but if you want it mounted on bootup, you'd need to edit /etc/fstab. But we can come to that later. One step at a time. :)

---

### Post by merdok1981 on 2009-05-16
Thank you for all your help so far, sorry for being such a noob.

Ok I did that and I got the message: Error File not found.

It appears that it could not find Grub stage 1.

---

### Post by coffeecat on 2009-05-16
> **merdok1981 said:**
> Ok I did that and I got the message: Error File not found.

It appears that it could not find Grub stage 1.

Apologies - I took your /etc/fstab file too literally. The commented lines with sdb1, etc misled me. Something doesn't quite add up, so I'm going to read through the thread again to see what I've missed. I think your 80GB drive must have been plugged into the drive 2 connector when that fstab was created.

In the meantime, try exactly what I posted before using the live CD, but this time with just the 80GB drive in the machine connected to the drive 1 SATA connector. I'll post back when I've done some thinking.

**Edit:** sorry, I'm slow tonight. Before you do that, boot up normally with both the 80GB and 750GB drives attached as normal, and post the output of the terminal command:

```
sudo blkid
```

Then we can get this muddle of sda/sdb and UUIDs nailed.

---

### Post by merdok1981 on 2009-05-16
Er. too late, I did it before you posted your edit LOL

On the plus side, linux has now booted perfectly from the 80gb. Which has solved the problem enough for me :) I can always put the 750gb in my other server :)

I've plugged the 1tb hard drive in and that has found it and I can mount it from places. However as you suggested it does not remain mounted when I reboot.

---

### Post by coffeecat on 2009-05-16
OK, I've worked out where my confusion was. At the moment, your 80GB drive is sda, so it is being treated as the primary by the BIOS, whichever port it is plugged into (more of that later). And your 750GB drive is the secondary - sdb. So far, so good. It was the sdb1 and sdb5 entries in fstab that took me in the wrong direction, particularly as the UUID for "sdb1" (your root partition) is the same as the root UUID in menu.lst. The clue was in the missing sdb5 (swap), because you have a sda5 (swap).

When you installed, the 80GB drive **must** (famous last words) have had secondary drive status, and grub stage 1 would have been installed to the 750GB drive (which then would have been sda). Hence the various grub errors.

Which leads on to: how is the boot order configured in the BIOS? If the BIOS is configured to boot from SATA drive 2, goodness only knows how this affects the way the Ubuntu installer sees all the drives and numbers them.

All I can say is that the 80GB drive was sdb when you installed, but is now being seen as sda. And the reason you can boot at all is because of those UUIDs.

Lots of questions. I'm fairly sure that reinstalling grub with the live CD with only the 80GB drive in the machine will work, but you really need to double-check your BIOS settings first. Something doesn't quite add up. 

And to answer a question you made earlier. You could reinstall to either of those drives with the 1TB drive in situ, but you'd need to be very careful at the partitioning stage of the installer. A safer option would be to install with just one drive in place and then fit the 1TB drive later and rely on the gnome automounting utility (or add an entry to fstab).

---

### Post by coffeecat on 2009-05-16
> **merdok1981 said:**
> Er. too late, I did it before you posted your edit LOL

On the plus side, linux has now booted perfectly from the 80gb. Which has solved the problem enough for me :) I can always put the 750gb in my other server :)

I've plugged the 1tb hard drive in and that has found it and I can mount it from places. However as you suggested it does not remain mounted when I reboot.

Excellent. You can read my subsequent witterings at your leisure. :wink: This will be my last post tonight, but I'll check this thread in the morning. So, if you wish and in the meantime, boot up from the 80G drive with the 1TB plugged in, and post the output :p of:

```
sudo fdisk -l
```and

```
sudo blkid
```Then I, or someone, can help you add a line to /etc/fstab to get the 1TB disc mounted on each boot for you.

Oh, and think about what I said about the BIOS boot order. Good night! :)

---

### Post by merdok1981 on 2009-05-16
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e94e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91a8b76b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104422   83  Linux
/dev/sdb2              14      121536   976133497+  83  Linux
/dev/sdb3          121537      121601      522112+  82  Linux swap / Solaris
```


```
/dev/sda1: UUID="64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f" TYPE="ext3" 
/dev/sdb1: UUID="122bf61e-d268-42e9-b82f-9f97719ed1b2" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="a29f5061-fa5a-4401-9c9a-e6cdcd0d07c5" TYPE="swap" 
```

Thank you for all your help coffecat, its much appreciated, I was tearing my hair out before I got to this forum :)

I'm guessing I changed the boot order in the bios recently for some strange reason, definately didnt change the physical plugs though.

BTW the 1tb has two partitions (one created by the NAS -presumably for its linux based os) so thats where there is an sdb2 and an sdb3, i;m not too concerned about that though, I can always find a use for a 100gb partition.

---

### Post by anewguy on 2009-05-16
> **coffeecat said:**
> No. Read the output that the OP has posted. It's all there.

**merdock1981**, I don't know what happened when you installed, but it's very odd.

OK. sda is your 80GB drive, sdb is your 750GB drive. Your Linux root partition is sdb1 on the 750GB drive. Your /etc/fstab file is trying to mount a swap partition on sdb5 which doesn't exist. :? The sda partitions on the 80GB drive are completely unused. The only function that sda has is grub stage 1 which is on the mbr. Grub stage 2 is in your sdb1 partition which explains the grub error messages you get.

While you digest that, could you post back with what you remember you did when you installed. Were the drives in a different configuration then?

Look at the 750mb drive - it's got the boot flag (*).  So it's trying to boot from it, but all of this system stuff, including the grub menu, is on the 80gb drive.  That's why when the 750mb is removed it gets boot disk failure.  What I was trying to say, maybe not clear enough, is that the 750mb is the boot drive, and the mbr is for loading grub, which is on the 80gb disk.  If all he's got is trash on the 750gb, he should be able to just change the mbr on the 80gb drive to be the boot device.

Dave :)

---

### Post by coffeecat on 2009-05-17
**merdok1981**, herewith some ideas for fstab. I'll quote your two last posted outputs, so as not to confuse them with your first fdisk output.
 

 > ```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
 255 heads, 63 sectors/track, 9729 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x0003e94e
 

    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1        9327    74919096   83  Linux
 /dev/sda2            9328        9729     3229065    5  Extended
 /dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
 

 Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x91a8b76b
 

    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1               1          13      104422   83  Linux
 /dev/sdb2              14      121536   976133497+  83  Linux
 /dev/sdb3          121537      121601      522112+  82  Linux swap / Solaris
``` ```
/dev/sda1: UUID="64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f" TYPE="ext3"
/dev/sdb1: UUID="122bf61e-d268-42e9-b82f-9f97719ed1b2" TYPE="ext2"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="a29f5061-fa5a-4401-9c9a-e6cdcd0d07c5" TYPE="swap"
``` And also your current fstab, so we've got everything in one place:
 

 > ```
# /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # /dev/sdb1
 UUID=64e45c7e-33a7-4e0c-8c17-6a4b14e0a62f /               ext3    relatime,errors=remount-ro 0       1
 # /dev/sdb5
 UUID=a29f5061-fa5a-4401-9c9a-e6cdcd0d07c5 none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
``` There's one problem &#8211; the output of blkid is incomplete. There's no line for sdb2 which we'll need for editing /etc/fstab. Did it not appear, or did you miss something when you pasted? Anyway, we'll fill in later.

 When I edit fstab for myself, I much prefer to use '/dev/sda1' or '/dev/sdb2' in the device (first) field, but we'll have to use UUIDs in yours because of the confusion between sda and sdb &#8211; possibly down to BIOS settings. By the way, make a mental marker of the fact that the commented lines (beginning with #) in fstab refer to sdb*, when in fact those partitions are sda*. Just so as you know when you come to fiddle with fstab in the future. :wink:

 Before working on any system file, it's a good idea to make a backup. If you make an error in your editing and the system becomes unbootable, you can always boot up with the live CD and restore from the backup so, from a terminal:

 ```
sudo cp /etc/fstab /etc/fstab.backup
``` You now make mountpoints for the two partitions you want to automount.

 ```
sudo mkdir /media/sdb1
sudo mkdir /media/sdb2
``` I'm slightly nervous about creating mountpoints called /media/sdb* because of the sda/sdb confusion. They will work, but if you prefer you can call them /media/bill and /media/fred &#8211; or whatever you want. Just substitute as appropriate.

 Now you edit fstab. This is where you need the UUID for partition 2 on the 1TB drive. You also need the filesystem type for that partition which blkid will provide. I'm going to assume it's ext3, rather than the ext2 of partition 1 (unfortunately fdisk gives the same 83 code for both ext2 and ext3), but you **must** confirm this before proceeding. Damage could result if you mount with the wrong parameters.

 ```
gksudo gedit /etc/fstab
``` Add these two lines:

 ```
UUID=122bf61e-d268-42e9-b82f-9f97719ed1b2    /media/sdb1    ext2    defaults    0 2
UUID=insertUUIDhere    /media/sdb2    ext3    relatime    0 2
``` And substitute /media/whatever for /media/sdb* if you've chosen something different. Reboot and **hopefully** everything will be well. **Edit**: No don't reboot - not necessary. Just do the command "sudo mount -a" from a terminal.

 If you want some light reading :wink: you might find [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) useful.

 > I can always find a use for a 100gb partition. If you mean sdb1, that's only about 100MB &#8211; probably for the NAS OS. Even Vista doesn't need 100GB &#8211; at least not quite! :) According to my calculations from your fdisk, sdb2 is about 930GB and sdb3 (the NAS swap partition) about 510MB.

 Good luck. I think I've covered most things.

---

### Post by coffeecat on 2009-05-17
> **anewguy said:**
> Look at the 750mb drive - it's got the boot flag (*).  So it's trying to boot from it, but all of this system stuff, including the grub menu, is on the 80gb drive.  That's why when the 750mb is removed it gets boot disk failure.  What I was trying to say, maybe not clear enough, is that the 750mb is the boot drive, and the mbr is for loading grub, which is on the 80gb disk.  If all he's got is trash on the 750gb, he should be able to just change the mbr on the 80gb drive to be the boot device.

Dave :)

Yes, you're mostly right, but for the wrong reason. :wink: So, apologies for misunderstanding your mostly-right bit. In fact the OP has already reinstalled grub to the 80GB mbr and all is well. But it's a bit more complicated than that. Read the bits in the thread about the BIOS order and the fstab references for sdb when it's really sda. It took some time for the penny to drop here, I must admit.

And the wrong reason? The boot flag is irrelevant. Linux (using grub or lilo) neither uses nor needs the boot flag. The boot flag is there for the Windows NTLDR, which must have the boot flag set to be able to boot. Which is why Windows must be on a primary partition, or at least have all the boot files on a primary partition. A limitation not shared by Linux. :)

In fact you can get Windows to boot from a partition without the boot flag - but for that you need grub and the makeactive command. Yet another example of Open Source improving on Windows functionality. :p

A favour please. Would you mind reading through my previous long post? Thanks. I'm sure I've got everything right, but if I've missed anything please say so.

---

### Post by merdok1981 on 2009-05-17
Ok bit of an update, I decided that I wanted that extra space on my server after all so I started again.

The 80gb has been thrown out of the window at a local passer-by and the 750gb now sits on sata-1, I installed Jaunty and then plugged the 1tb into sata-2

My fdisk -l now looks like this:

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f95b518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90285   725214231   83  Linux
/dev/sda2           90286       91201     7357770    5  Extended
/dev/sda5           90286       91201     7357738+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91a8b76b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104422   83  Linux
/dev/sdb2              14      121536   976133497+  83  Linux
/dev/sdb3          121537      121601      522112+  82  Linux swap / Solaris

```and my blkid looks like this:

```
/dev/sda1: UUID="3e69bd77-3275-4970-8b43-2adc50f37518" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b402d863-41dd-40fa-8a26-dcce3827cb2f" 
/dev/sdb1: UUID="311a593f-24c0-4f0f-acb8-ab5c6622577f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="de588655-c57d-47c0-8757-a0b0862d2fc6" TYPE="ext2" 
/dev/sdb3: TYPE="swap" 

```I'm going to take a look at your above posts and see if I can figure out how to mount the drives with the new configuration but I'm feeling a little fuzzy-brained today so its likely that I'll be back grovelling for help again :)

---

### Post by merdok1981 on 2009-05-17
OK after perusing your post I've realised that if I try to 'wing it' with the new information I might end up doing some damage, so I will wait for your advice :)

---

### Post by coffeecat on 2009-05-17
I'm puzzled. Yesterday, blkid gave this for sdb:

> /dev/sdb1: UUID="122bf61e-d268-42e9-b82f-9f97719ed1b2" TYPE="ext2"and no sdb2 or sdb3

But today we get:

> /dev/sdb1: UUID="311a593f-24c0-4f0f-acb8-ab5c6622577f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="de588655-c57d-47c0-8757-a0b0862d2fc6" TYPE="ext2" 
/dev/sdb3: TYPE="swap"See how the UUID and type for sdb1 has changed?

First question: are you sure you didn't have the 750GB plugged in yesterday instead of the 1TB when you did blkid? Because the fdisk output you posted at the same time is clearly from the 1TB disc. If you did have the 1TB drive in when you blkid'd yesterday, that's worrying. UUIDs shouldn't change like that.

The other thing worrying me (slightly) is that the big 930GB partition (sdb2) is showing up as ext2, which is a non-journalled filesystem. That's an odd choice for the data partition on a NAS. I can understand ext2 for the OS partition on a NAS, but that's (sdb1) showing as 'SEC_TYPE="ext2" TYPE="ext3"' which I've never seen before.

OK, I could suggest a fstab line for sdb2, but if I was in your situation, I wouldn't bother. I would use the automount option in the Places menu to get to the data and then copy everything onto another drive. Then I would reformat the whole of the 1TB drive with a journalled filesystem and copy the data back on again. Only then would I add a fstab line.

Alternatively, you can convert ext2 to ext3 (journalled) on the fly so to speak, but I've never done this, and would not even think of attempting it without backing up first. And if you back up, you might as well fix yourself up with a neater partition layout.

I'll await your response before suggesting anything further.

---

### Post by TJCIB on 2009-05-17
Correct me if I'm wrong but:

Assuming all the important data is backed up, and both drives can be totally wiped:

Couldn't he just reformat the 1TB drive to the appropriate file system (ext3 or whatever), and reinstall Ubuntu with both drives hooked up. If everything is double-checked during install, the OS and grub should be installed on the first HD, and all the necessary information from the 2nd HD should be placed in fstab automatically.

I have done many installs with multiple drives of differing types and never came across such a problem.

It seems like what needs to happen is simply a well-performed, everything verified installation. Check the hard drives are installed in the correct order. Be sure BIOS has them in the order you want. Be sure the installer puts everything where you want it, and you should be good to go.

*edit* if your 2nd hard drive doesn't show up in fstab to mount automatically at boot up, follow this link to add it. It is super easy. [https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot]("https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot")

---

### Post by coffeecat on 2009-05-17
> **TJCIB said:**
> Couldn't he just reformat the 1TB drive to the appropriate file system (ext3 or whatever), and reinstall Ubuntu with both drives hooked up.

If I'm reading the first post correctly, the OP has media files on the 1TB drive which he wants to keep/rescue. The whole thread has been about getting the system to boot with just one of the 80GB or 750GB drives so that he can plug the 1TB disc in and access the files without formatting it. He's only got 2 SATA connectors on the m'board.

Simply pointing the OP to a fstab howto misses the worrying point that the 1TB UUIDs seem to have changed overnight.

---

### Post by TJCIB on 2009-05-17
The changing UUIDs is not a problem. They change if you repartition or reinstall or reformat.

Quote "The UUID for a hard disk or partition is calculated from it's properties, size, file system, it's place relative to other partitions and maybe more.
So if you change a partition and/or change other partitions the UUID changes too. Then when you try to boot it fails - your (root) partition has got a new name (new UUID) but neither /boot/grub/menu.lst or /etc/fstab has changed. In essence you try to use a non existent drive!"

Which is why I said fresh install would be good. It would recalculate all the UUIDs and put them in the correct places in the fstab and grub. Just be sure everything is as you want it before you start in the install.

---

### Post by TJCIB on 2009-05-17
link for that quote:

[http://www.linuxmint.com/wiki/index.php/UUID_-what_is_it_and_why_is_it_a_problem]("http://www.linuxmint.com/wiki/index.php/UUID_-what_is_it_and_why_is_it_a_problem")

---

### Post by coffeecat on 2009-05-17
> **TJCIB said:**
> The changing UUIDs is not a problem. They change if you repartition or reinstall or reformat.

For goodness sake, read the thread. **He hasn't reformatted the drive/partition but has posted discrepant UUID values.** There may be a perfectly good explanation but until we get to the bottom of it, I would advise caution.

---

### Post by TJCIB on 2009-05-17
You're probably right, I am just pointing out that the first time he posted the output of blkid he had his 80GB as sda and his 750GB as sdb, whereas the second time around the 750 was sda and the 1TB was sdb.

You are comparing two outputs from two totally different drive configurations, that is all I am saying...
UUIDs are not MAC addresses, they change. He did modify the 750GB drive by installing grub to it, that could have changed the entire UUID setup.

Given the previous posts by the OP, I think worrying about the UUIDs is futile and will cause more problems, especially since his system is working now.

---

### Post by merdok1981 on 2009-05-18
Ok. Hope I'm not creating any tension here LOL :)

Unfortunately I don't have enough space on my network to back up nearly 800gb of data so reformatting the 1TB isnt an option. Is an ext2 filesystem going to cause any problems?

Also I DID have the 750gb and the 1TB plugged in when I did the fdisk and the blkid. The 750gb had been totally reformatted and the 1TB has not been touched.

---

### Post by TJCIB on 2009-05-18
=)

If everything is working how you want it, congrats!
If you are not going to be changing your drive configurations around anymore, you can simply mount your 1TB drive in fstab using "/dev/sdb1" instead of the UUID (See the howto I gave you about fstab in post #24).
If you want an icon to appear on the desktop, you must mount the volume in a subdirectory of the /media folder (ex: /media/drive2), if you don't want that, you can create a mount point virtually anywhere else. The place I use is something like /mnt/drive2

UUIDs are most useful for when drive locations are being changed on purpose.
The only time I worry about UUIDs is if I am running a server, because on personal desktops there is very little drive switching.

The ext2 filesystem should be okay, but you cannot access the drive from Windows (without some work, it actually is possible). IF you do ever reformat, remember there are some file size restrictions on FAT filesystems. If it is a media center drive, that will be important.

Hope that helps.

---

### Post by coffeecat on 2009-05-18
> **merdok1981 said:**
> Unfortunately I don't have enough space on my network to back up nearly 800gb of data so reformatting the 1TB isnt an option.

Don't forget the old adage about data being more valuable than the physical media that it's on. I don't want to worry you :p but you've got 800GB data on only one physical medium - no backups at all. Hard drives do fail, sometimes without warning, sometimes when still quite new. Depending on your budget, do give thought to getting yourself another backup medium, perhaps a 1TB USB drive. They often come pre-formatted with the FAT32 filesystem and **TJCIB** makes an important point - there's a 4GB filesize limit with FAT32.

> **merdok1981 said:**
> Is an ext2 filesystem going to cause any problems?

Maybe not but inevitably it's going to be less robust than a journalled filesystem such as ext3. I'll admit that my view is coloured by an unfortunate incident with Ubuntu on my EeePC with a flash internal drive. I'd formatted it with ext2 - necessary to prevent premature failure caused by the increased writes of a journalled fs. I experienced a sudden, unplanned hard shutdown (long story) and the filesystem was so corrupted I couldn't boot up or repair it. An ext3 fs might have been repairable with fsck.

Moral of story: don't have a hard shutdown with an ext2 fs when it's being written to.

> **merdok1981 said:**
> Also I DID have the 750gb and the 1TB plugged in when I did the fdisk and the blkid. The 750gb had been totally reformatted and the 1TB has not been touched.

Curious. I think I'll let that pass. Life's too short to worry about it.

I've rather lost the plot at this point. :lol: Do you still need help with fstab?

One last thought. If you do reformat the 1TB drive for data storage, it's also worth thinking about the NTFS filesystem. It's journalled and doesn't have the 4GB file limit and is well supported in Ubuntu. One advantage that I like about it is that it **doesn't** support Linux permissions. That sounds an odd thing to say, but it can be useful at times. Downsides - it's prone to fragmentation and if you do get fs corruption, you really need Windows to repair it.

---

### Post by merdok1981 on 2009-05-18
LOL well it took me long enough but its finally all working perfectly, thank you guys.

re: backups, I know I need to do it but at the moment I can't afford a new hard drive. Its on my to-do list though :)

---

### Post by TJCIB on 2009-05-19
Agreed. Good advice coffee...

Just thinkging: Maybe get a converter or something (i've never actually worked with them and don't know their reliability) so you can use all three of your drives. Seems like you could have your OS on the 80GB and use the other two for storage/backup. I think I've seen things that turn as SATA HD into an external USB drive.

But that is a different thread...mark this as solved if you're satisfied =)

---

### Post by merdok1981 on 2009-05-19
Yes I think that may be an option. Thank you.

---

### Post by merdok1981 on 2009-05-19
I can't see an option to mark it as solved I'm afraid.

---

