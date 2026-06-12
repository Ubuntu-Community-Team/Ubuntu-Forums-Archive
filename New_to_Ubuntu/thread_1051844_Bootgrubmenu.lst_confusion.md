---
title: "Boot/grub/menu.lst confusion"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-01-27
I have been dual-booting Ubuntu/XP for some years & had set-up my menu.lst just how I wanted it in Hardy with kernel 2.6.24-23. Let me call that U23.
My grub boot screen then started with XP > U23 > U23safe etc.

Recently, I made a live DVD with Remastersys (excellent!) which worked fine as a live DVD.

Then I re-installed from the DVD into a new partition on the same PC.
It's going to be my back-up LTS OS while I try upgrading U23 to Intrepid etc. 
That worked fine too. Let me call that R23.

One thing I noticed was that my grub boot screen now said R23 > R23safe > XP > U23 > U23safe etc.
I wondered why, but did not bother much.
In fact - it corresponds to the menu.lst in R23 which has been completely revised from my original in U23.

But now I have Upgraded U23 to Intrepid & things are not working out...
My grub boot screen is till stuck at Hardy, with R23 > R23safe > XP > U23 > U23safe etc.
No mention of the new Intrepid.
Synapt shows new Intrepid kernel 2.6.27-9 installed OK.
When I look at my menu.lst files, the one in U23 has been updated to include new Intrepid kernels 2.6.27-9 & 9safe.
The menu.lst in R23 is stuck at R23 > R23safe > XP > U23 > U23safe etc.
It seems the grub boot screen is working from the R23 menu.lst & not the U23 one.

I suppose I could just copy U23 to R23 but that way I will not understand what is going on & presumably menu.lst will not get automatically updated with new kernels?

Can anybody explain what is wrong & how to fix it?

Thanks!

---

### Post by Elfy on 2009-01-27
I think that you need to install grub from your new intrepid again - seems like that is what has happened - boot with the livecd and then use this [http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2)

It will find 2 when you find /boot/grub/stage1 - one is Hardy, one Intrepid - pick the Intrepid one.

From the U's and R's I think that you 

had Hardy and XP with Hardy running the boot
then you installed a copy of Hardy and upgraded to Intrepid

If that is so then try installing grub for your new install to the mbr.

Be easier to tell with the output of 

```
sudo fdisk -l
```

If you're not sure - boot the livecd, get the grub info and come back here.

---

### Post by 2CV67 on 2009-01-27
Thanks for that quick response!
> **forestpixie said:**
> 

Be easier to tell with the output of 

```
sudo fdisk -l
```

Here is that output:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eed1eed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10449    83931561    c  W95 FAT32 (LBA)
/dev/sda2           14467       14593     1020127+  82  Linux swap / Solaris
/dev/sda3           13154       14466    10546672+  83  Linux
/dev/sda4           10450       13153    21719880    5  Extended
/dev/sda5           10450       11086     5116671    b  W95 FAT32
/dev/sda6           11856       13153    10426153+  83  Linux
/dev/sda7           11087       11855     6176961   83  Linux

Partition table entries are not in disk order

You said:> From the U's and R's I think that you had Hardy and XP with Hardy running the boot then you installed a copy of Hardy and upgraded to Intrepid

Just to be clear:
I had Hardy (U23 = /dev/sda3 above) & XP OK.
I added a copy of Hardy (R23 = /dev/sda7 above).
I kept the copy (R23) & upgraded the original (U23) to Intrepid.

I have not tried reinstalling grub from Intrepid - I can't get to Intrepid as it does not show in the boot screen...

---

### Post by Elfy on 2009-01-27
You don't need intrepid in the boot screen to resintall grub - bbot the livecd and follow the link I gave earlier.

The find /boot/grub/stage1 command should give you 

hd(0,2) equivalent of sda3
hd(0,6) equivalent of sda7

So if you wanted Intrepid to run grub then root would be hd(0,2) Hardy wouldbe hd(0,6)

Then setup hd(0) 

Personally I would set up Intrepid for grub then chainload Hardy, that way hardy's menu will get updated with kernel changes

I have my intrepid grub installed to hd0 - but Jaunty and xubuntu are chainloaded

> title           --Jaunty Jackalope--
root            (hd2)
chainloader	+1

title		--Xubuntu
root		(hd2,3)
chainloader	+1

---

### Post by johnystevenson on 2009-01-27
thanks, ye have sorted me out

johny

---

### Post by 2CV67 on 2009-01-27
Wish I could say the same...;)

When I see > First, boot into any linux live cd, then once logged in, mount your ubuntu partition, (you can find the /dev block device by sudo fdisk -l, then do sudo mkdir ubuntu then sudo mount /dev/Block device from sudo fdisk -l) my brain turns to jelly!

So I am now wading through a grub tutorial to try to get my ideas straight, before risking anything that could leave me with no boots.
Could take days...

But thanks anyway, forestpixie, for pointing me in the right direction!

---

### Post by Elfy on 2009-01-27
You shouldn't need all that again you have it already - :)Try this one instead - 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

You need to know wher your 2 installs are - sda3 and sda7 as long as you which is supposed to be which and which one to have the main menu list then you should be fine :)

---

### Post by 2CV67 on 2009-01-27
Thanks for your help & patience (so far!) forestpixie.

I have read your posts, your links & Dedoimedo's Grub Tutorial, but I am still hesitating.
I am not in a great hurry & would rather not screw things up by jumping too quickly!

The whole purpose of installing both Hardy & Intrepid was to be able to easily select either at boot.
What I want to achieve is a boot screen which allows me to select XP/Hardy/Intrepid.

When this is finished, should there be 2 separate menu.lst files with uncoordinated content?
Or 2 separate files with synchronised content?
Or one file & a link?
Or what?

Currently, the menu.lst in Hardy includes XP & Hardy kernels.
The boot screen looks like that.
Menu.lst in Intrepid includes XP & Intrepid kernels.
So neither of these is what I want...
..is it?

So pointing grub at one or the other won't solve my problem...   will it?

---

### Post by Elfy on 2009-01-27
Can you do this for me please - run these 2 and post the outputs

```
cat /boot/grub/menu.lst
blkid
```

Just to clear something up - when you boot ubuntu from the menu list you get - it boots Hardy or XP.

Now - all that aside - how mine works is like this

Intrepid controls grub - it has itself, Jaunty and Xubuntu as options.
If I boot either Jaunty _or_ Xubuntu I get their own specific menu.lst, so for instance to boot Xubuntu I have 2 menus. The adavantage here is that they all have their own menus and kernels being updated when the kernels are.

> When this is finished, should there be 2 separate menu.lst files with uncoordinated content?
Or 2 separate files with synchronised content? - [COLOR="Navy"]how I have it set up[/COLOR]
Or one file & a link? 
Or what? - [COLOR="Navy"]the choice as they say, is yours[/COLOR]

---

### Post by Ayuthia on 2009-01-27
> **2CV67 said:**
> 
So pointing grub at one or the other won't solve my problem...   will it?
You are correct.  The OS that does the kernel upgrade will update it's own grub but not the other OS's grub menu.lst.

I currently have Vista, Gentoo, Arch, Mandriva, and Jaunty installed on my laptop.  Arch is the location where I keep grub running.  So if I make a kernel upgrade on any of my other Linux partitions, I go into the Arch partition and update the menu.lst manually.  However, if Arch has a kernel update, it will update the menu.lst file automatically because it has grub installed.

So whichever OS has installed grub most recently will have its menu.lst info used.  If R23 was installed most recently, you should be updating R23's menu.lst when U23 gets a kernel update.

---

### Post by caljohnsmith on 2009-01-27
> **Ayuthia said:**
> You are correct.  The OS that does the kernel upgrade will update it's own grub but not the other OS's grub menu.lst.

I currently have Vista, Gentoo, Arch, Mandriva, and Jaunty installed on my laptop.  Arch is the location where I keep grub running.  So if I make a kernel upgrade on any of my other Linux partitions, I go into the Arch partition and update the menu.lst manually.  However, if Arch has a kernel update, it will update the menu.lst file automatically because it has grub installed.

So whichever OS has installed grub most recently will have its menu.lst info used.  If R23 was installed most recently, you should be updating R23's menu.lst when U23 gets a kernel update.
That's the advantage of using the "configfile" or "chainloader" notation rather than manually copying the new kernel entries to the menu.lst that gets loaded on start up; you can simply link to each distro's menu.lst using "configfile" or "chainloader" so that when that distro's menu.lst gets updated, the changes are shown on start up. One disadvantage of using "configfile" or "chainloader" though is that you have to go through two boot menus, i.e. the main menu.lst that gets loaded on start up, and then when you select the desired distro, its menu.lst gets loaded. In other words, in your main menu.lst you could use something like:
```
title Distro1 on sda8
configfile (hd0,7)/boot/grub/menu.lst

title Distro2 on sda10
root (hd0,9)
chainloader +1
```
If you use the chainloader technique, you have to first make sure Grub is installed to the boot sector of that partition. I actually prefer to do it your way though and just copy the kernel entries over to my main menu.lst, because I don't like to go through two boot menus. But as with everything in Linux, there's usually many choices available for doing things in many different ways. :)

---

### Post by Elfy on 2009-01-27
> I actually prefer to do it your way though and just copy the kernel entries over to my main menu.lst, because I don't like to go through two boot menus.I used to do that - but memory issues prevailed and I rarely remembered to update the list ;)

Of course while I do have 2 menus - the second are 1 sec waits

---

### Post by cariboo on 2009-01-27
If you use the configfile option in grub, you don't have to manually edit grub everyt time there is a kernel update on the other distrubutions, this is what I use on my triple boot system:

```
# This link was added by me to use the grub menu on /dev/sda2
title		Ubuntu 8.10, Intrepid
uuid		da96f95c-3bbb-47f2-8b4e-d27168650688
configfile	/boot/grub/menu.lst
```

the above uses Intrepids /boot/grub/menu.lst.

Jim

---

### Post by 2CV67 on 2009-01-27
I am following this with great interest & it is beginning to make sense...
But I am having a job keeping up!

> **forestpixie said:**
> Can you do this for me please - run these 2 and post the outputs

```
cat /boot/grub/menu.lst
blkid
```

Just to clear something up - when you boot ubuntu from the menu list you get - it boots Hardy or XP.


When I boot without selecting anything, it chooses the first item on the list, which is Ubuntu 8.04.1, kernel 2.6.24-23-generic on hd(0,6) aka sda7.
This is Hardy freshly installed from my Remastersys DVD which I am calling R23.
Below is menu.lst R23 which corresponds with what I now see on the boot screen. 
Below is also blkid R23 from that same R23 environment, which is empty...?

At the boot screen, I can step down about 4 clicks & boot XP OK.

I can also step down a bit further & boot Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3) on hd(0,2) aka sda3.
This is my original, mainline Hardy which I am calling U23.
Yesterday I upgraded this one to Intrepid (maybe aborted???) but can't access any more recent kernels so it is still running (well) on kernel -23.
Below is menu.lst U23 which shows newer kernels & also confusingly calls the -23 kernels 8.10...
Below is also blkid U23 from that environment.

I wonder if that is any clearer - or less so...
..........................
menu.lst R23:
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
# kopt=root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


::::::::::::::::::::::::::::::::::::::::

blkid R23:
chris@chris-desktop:~$ blkid
chris@chris-desktop:~$ 


::::::::::::::::::::::::::::::::::::::::

menu.lst U23:
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
#hiddenmenu

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




::::::::::::::::::::::::::::::::::::::

blkid U23
chris@DESKTOP:~$ blkid
/dev/sda1: UUID="2B1B-1302" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sde1: UUID="2B1B-1302" TYPE="vfat" 
/dev/sda2: UUID="5a626c9d-6484-489b-9a9a-c215110b5952" TYPE="swap" 
/dev/sda3: UUID="f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c" TYPE="ext3" 
/dev/sda5: UUID="48A5-D628" TYPE="vfat" 
/dev/sda6: UUID="e3bbb061-9a3d-4c6e-960a-03d42b490670" SEC_TYPE="ext2" TYPE="ext3" 
chris@DESKTOP:~$

---

### Post by Elfy on 2009-01-28
Ok - so you can boot the first ubuntu ok - which you call R - this is not intrepid - it has not been upgrade yet.

You can also boot Xp and the ubuntu you are calling U which is Hardy.

Boot the first one - your R ubuntu and upgrade it and you will be all set :)

If it is not showing that intrepid is available as an upgrade - open Software Sources from the System Admin menu - go to the Update tab and then at the bottom - Release Upgrade - make sure that si showing Normal Releases, close software sources and it will ask to reload - let it.

Once that's upgrade you should have different kernels in the menu list :)

---

### Post by 2CV67 on 2009-01-28
Hi & Good Morning!

Yesterday, I copied the "Ubuntu 8.10, kernel 2.6.27-9-generic" block from my U23 menu.lst to the R23 menu.lst
Then I could boot to that kernel & it was Intrepid (from System Monitor).
It is a reasonably-functioning Ubuntu, with wireless, mail, Firefox etc so I know now I can use it (haven't tried printing or scanning etc yet).

Out of curiousity, I then booted to the "Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3)" from the R23 menu.lst & was extremely surprised to find that System Monitor also thinks that is Intrepid!

Further curiosity, I booted to "Ubuntu 8.04.1, kernel 2.6.24-23-generic" & System Monitor thinks that is still Hardy...

Anyway, what I intend to do now, is to keep R23 as my Hardy LTS version (fallback) & use U23, updated to Intrepid, for everyday use & 6-monthly upgrades.

Following all your (several contributors) helpful suggestions, I shall be pointing grub to Intrepid & chainloading R23.

That is going to take me a little while (age & caution...) but I will report back soonish!

Thanks again!

---

### Post by 2CV67 on 2009-01-28
OK - grub is now in Intrepid (hd0,2) & boots Intrepid & XP OK.

Next step - chainloading...

Watch this space!

---

### Post by 2CV67 on 2009-01-28
Hmmm..

I added a block to the bottom of my U23 (Intrepid) menu.lst which now finishes as follows:
::::::::::::::::::::::::::

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda7
root (hd0,6)
chainloader +1

#just the end.
::::::::::::::::::::::::::

The boot screen looks OK with Ubuntu LTS on sda7 at the bottom, but when I try to boot LTS I get:
"Error 13 Invalid or unsupported executable format"

I am Googling that, but any hints & tips would be welcome!

Thanks!

---

### Post by Elfy on 2009-01-28
Boot with the livecd open a terminal 

```
sudo grub
grub> find /boot/grub/stage1
```

You will get 2 options - one on hd(0,2) ignore that one it is your intrepid, the other will be hd(0,6) I think - this is the one you need in the next stages- it's the Hardy install

```
grub> root (hd0,6) or whatever it is
grub> setup (hd0,6) or whatever it is 
```

it should say it's succeeded doing it's thing
```
grub> quit
```

If it isn't hd(0,6) then you need to also change

> #Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda7
root [COLOR="Red"](hd0,6)[/COLOR]
chainloader +1

Oh and fyi - I use herman's grub pages - very very long but useful none the less - especially
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)

---

### Post by 2CV67 on 2009-01-28
Thanks forestpixie - that now works perfectly.

I have a big backlog for when the forum "Thanks" button comes back!

Also a couple for "Solved"...

I used Hermans Dual Boot site quite a bit, but had not found his Grub section yet.
I can read it at leasure now :D

Many thanks for all the contributions!

---

### Post by Elfy on 2009-01-28
Excellent :)

---

### Post by 2CV67 on 2009-01-28
Couldn't put it better myself!

---

