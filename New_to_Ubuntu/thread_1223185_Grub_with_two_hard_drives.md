---
title: "Grub with two hard drives"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by dr.silly on 2009-07-25
I recently migrated my ubuntu installation from a partition to a seperate hard drive. Now when I boot up I get grub error 22. After some googling I came across [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). I followed the instructions but to no avail. I tried using ```
setup (hd0,0)
``` and ```
grub-install
``` but those didn't work either. After reading up on error 22 I read this: ```
No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 
``` So I opened up my /boot/grub/menu.lst: ```
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
# kopt=root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b82df332-f2fb-459e-b806-5d9c61287962

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b82df332-f2fb-459e-b806-5d9c61287962 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b82df332-f2fb-459e-b806-5d9c61287962
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

So I checked vol_id /dev/sda1:
```
ubuntu@ubuntu:~$ vol_id /dev/sda1
/dev/sda1: error opening volume

```

I tried using uuidgen and tune2fs to assign a uuid but that didn't work either. If it helps here is my fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009dd37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19136   153709888+  83  Linux
/dev/sda2           19137       19457     2578432+   5  Extended
/dev/sda5           19137       19457     2578401   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1        4241    34065801    7  HPFS/NTFS

```

Thanks

---

### Post by louieb on 2009-07-25
Are your drives IDE (aka PATA - flat ribbon cable) or sata or a mix? 

from your fdisk it looks like from the grub>  prompt 
```
sudo grub
```enter
```
root (hd0,0)
setup (hd0)
quit
```from your post look like you may have not done the root command to tell grub which partition holds the main grub program (stage2).


also the reason vol_id failed is you did not  run with admin privileges.

```
sudo vol_id /dev/sda1
``` should work

---

### Post by louieb on 2009-07-25
Also from fdisk your windows entry should have map commands to make windows believe its on the 1st hard drive. 

```
title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```

---

### Post by dr.silly on 2009-07-25
My previously partitioned hard drive is SATA and the newly installed one is IDE.

---

### Post by dr.silly on 2009-07-25
oh darn i tried what you said but i figured i would try it again and now i get error 15 when running "find /boot/grub/stage1"

---

### Post by dr.silly on 2009-07-25
Sorry nvm I got the grub process to work but grub still won't load the uuids in /boot/grub/menu.lst don't match that of the actual drive should I replace those?

---

### Post by KinKiac on 2009-07-25
From what I understand from searching around grub error 22 is when it cant find the partition.  I had this same error when I first installed and it boiled down to my HDD not getting enough power to run properly.  I ended having to switch around my power cables so that my drives and my video card were getting the right amount of power and not only did I fix the grub error I ended up fixing what was an ongoing issue with the video when running to an HDTV via VGA.(I had been working around the video issue by using DVI-HDMI up until then)  

If you go into your Bios settings is it showing both of your HDD's or just one?  

I have 2 HDD's, an 80gig IDE and a 320gig SATA, my Windows XP is on my IDE and my Ubuntu is on a 20gig partition of my SATA drive.  During installation I didnt change any of the settings regarding GRUB and just let it install at the default location and after fixing the issue with my power distribution everything worked just fine.   

I dont know if this applies to your situation, I just thought Id suggest to check because it helped me with a similar problem

EDIT:  Sorry I guess this doesnt apply to your situation

---

### Post by dr.silly on 2009-07-25
hmm no its not a power issue and i can be sure that both drives are recognized by bios

i replaced all of the incorrect uuids in /boot/grub/menu.lst but that didn't work. Im beginning to wonder if the wrong grub is being called bc I originally had grub on the SATA drive but now i have it duplicated on the IDE??

---

### Post by louieb on 2009-07-25
> **dr.silly said:**
> ... uuids in /boot/grub/menu.lst don't match that of the actual drive should I replace those?

Yes they have to match. Thats how the kernel knowns which partition contains the / (root) file-system.

> My previously partitioned hard drive is SATA and the newly installed one is IDE.

The GRUB installer get confused when theres a mix and get it right about half the time.   As you have learned sometimes you just have to do a manual fix.

---

### Post by dr.silly on 2009-07-25
ok that's what i thought im going to try booting off the ide and see if that makes a difference

---

### Post by louieb on 2009-07-25
Are you seeing the GRUB menu? Does it boot windows? or is the problem just with Ubuntu?

---

### Post by presence1960 on 2009-07-25
your UUID for Ubuntu probably changed when you put it on a new partition. Let's get a look at your setup & boot process. Boot off the Ubuntu Live CD. Choose "Try Ubuntu without any changes..." When the desktop loads open firefox and download the Boot Info Script 0.32 from here to your desktop: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)
Once DL'd to the desktop open a terminal & run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

We will see exactly what you have there. this will give all the info requested above and much more.

---

### Post by louieb on 2009-07-25
> **dr.silly said:**
> ok that's what i thought im going to try booting off the ide and see if that makes a difference

Boot order makes a big difference - thats how GRUB tells which drive is which.

BTW: +1 for the previous post. The boot info script gives a lot of useful stuff.

---

### Post by dr.silly on 2009-07-25
Okay, I got it. There were two problems there were two grubs (i was booting into the wrong one) and the uuids were wrong in the grub. What I did was replaced the uuids in the grub and tell grub to boot off of the the new IDE drive as opposed to the default SATA.

Thanks for all of your help very much appreciated!

---

