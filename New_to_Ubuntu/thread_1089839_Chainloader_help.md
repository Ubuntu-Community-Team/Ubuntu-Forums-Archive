---
title: "Chainloader help"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Ouia on 2009-03-07
Hi

I have two partition. One with Hardy and one with Ubuntustudio.
I want to chainload them, but I don't no exactly how.

I also have a few question.

* The default OS is Hardy. Do I put studio before Hardy or after it? Or doesn't it matter?
* The "chainloader +1" sentence. Is it always +1? or can it be +2 etc?
* Is "chainloader +1" put with default kernel in menu.lst or the secondary kernel?
* How can I tell the chainloading is working?

thanks in advance

---

### Post by thtrgremlin on 2009-03-07
I am not sure what you mean by chain loading, but lets check. Chainloading means you can have grub installed on /dev/sda AND /dev/sda1 AND /dev/sda2 where when the computer starts, it loads grub from /dev/sda then your menu entries will take you to the grub on /dev/sda1 or /dev/sda2 using 'chainloader'.

chainloading is really only necessary in order to allow grub to start up another boot loader that is necessary for starting another OS that can't be started by grub, like windows.

If you really want two installations of ubuntu, you can just have grub on /dev/sda have all your menu options right there.

Further, Ubuntu-studio isn't so different from regular ubuntu that you oculd not just have two different logins. The biggest difference is that ubuntu-studio uses the realtime kernel be default which is useful for certain video editing applications. But even then, you can have more than one kernel, and then just tweak each user account with different menu options as you desire.

At very least, I would recommend using just one instance of grub for everything.  Does this possibly solve the problem, or was there something else you wanted to accomplish I may have over looked? Also, I'd be happy to help you organize those grub menu entries if that is the route you want to go, if need be.

---

### Post by Ouia on 2009-03-07
Well, the problem is that I can't use my wireless in Ubuntustudio. So I can't get updates etc. I was advised to add a chainloader to the new partition from the first grub to save myself a lot of potential troubles.

For clarifaction, my first install was 8.04, which I upgraded to Studio with RT kernel. But that killed my wireless. After switching back to the generic kernel, my internet access came back, but that gave lots of other problems regarding Studio.

So now I did two fresh installs on two partitions on 1 harddrive. One of 8.04 and one of Studio.
But I still have no internet on Studio, which brings me to the advise that I got to add a chainloader.

My problems would be solved by having internet access with studio, but that is going to be troublesome for now. So I'm looking into this possibility now.

---

### Post by The Cog on 2009-03-07
Chainloading is where the main bootloader (on the bootsector of the hard disk) loads a second bootloader which is located at the front of a selected partition. So for instance, the bootloader on /dev/sda chainloads and boots the first sector of /dev/sda1.

You can install GRUB on /dev/sda1 (or whichever partition your system is on) with the command:
sudo grub-install /dev/sda1
so that now if that partition gets chainloaded, it will launch GRUB and present the normal GRUB menu. 

Of course, if you want to use GRUB as the initial bootloader too, it will probably want its own /boot/grub partition somewhere, so maybe one of your Linux installs will not be chainloaded, but will be the home of the primary bootloader. I assume you realise that GRUB needs access to /boot/grub on a partition somewhere, both to hold most of the bootloader code and the menu definition file.

When you are installing Ubuntu, you can choose to install the bootloader on a partition instead of the main bootsector. You will then have to configure the main bootloader by adding the chainload option. I find it easier just to add lines like:
```
title           Kubuntu 8.10 Intrepid
root            (hd0,5)
kernel          /vmlinuz ro 
initrd          /initrd.img
savedefault
boot
```
which use the symlinks rather than specific kernel version filenames, so the file doesn't need editing when there's an update to the target OS.
> The default OS is Hardy. Do I put studio before Hardy or after it? Or doesn't it matter?
Doesn't matter which order.
> The "chainloader +1" sentence. Is it always +1? or can it be +2 etc?
I think it says how many blocks of the partition to read into memory. It's normally just the one first sector.
```
Is "chainloader +1" put with default kernel in menu.lst or the secondary kernel?
```In the menu.lst of whichever OS partiton the main bootloader is reading. This might be the first one installed (if you install the second bootloader into a partition rather than the MBR), or might be the second OS installed (if you allowed it to overwrite the original GRUB on the MBR).
> How can I tell the chainloading is working?
You will get a second GRUB menu if the chainloading works.

---

### Post by Elfy on 2009-03-07
Hi - I installed grub to each my kubuntu/xubuntu/intrepid partitions then reinstalled grub for jaunty to sda - in this way I have each using their menus and jaunty runs grub.

The 'extras' on my menu list look like
> ### END DEBIAN AUTOMAGIC KERNELS LIST
title 		---OTHER OPERATING SYSTEMS---
root

title		---KDE Jaunty---
root		(hd0,3)
chainloader 	+1

title 		---Intrepid---
root		(hd0,1)
chainloader	+1

title		---Xubuntu
root		(hd2,3)
chainloader	+1

Edit - > which use the symlinks rather than specific kernel version filenames, so the file doesn't need editing when there's an update to the target OS would be easier and I would have done similar if I'd known :)

---

### Post by Ouia on 2009-03-07
If I start my computer now I get a screen where I can choose between several kernels. I can change that by changing /media/disk/boot/grub/menu.lst.

(I had to change that, as I installed my default OS first. I did manage to get Hardy booted as default by changing that file)

There is also a boot/grub/menu.lst, but I'm not sure whether that does anything.

I hope that helps to get a better picture of what is already on my computer, because it slightly confusing at this point in time for me :)

---

### Post by Ouia on 2009-03-09
This is what it looks like now
Adding a chainloader line to the rt \-kernel gives an error 13 message.
Tried it in several varieties.





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
timeout		5

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
# kopt=root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro

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
# defoptions=splash vga=773

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro splash vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet
chainloader	(hd0,4)+1

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

---

### Post by Elfy on 2009-03-09
> ### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu 8.04.1, kernel 2.6.24-19-rt
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-rt
quiet
chainloader (hd0,4)+1

Try

> title Ubuntu 8.04.1, kernel 2.6.24-19-rt
root (hd0,4)
chainloader (hd0,4)

But did you actually install grub for it to hd0,4?

Or add a stanza based on The Cog's post.

---

### Post by Ouia on 2009-03-09
Stanza?

So you mean without 

```
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-rt
quiet
chainloader (hd0,4)+1
```
?


I installed Hardy (hd0,0) first, than installed studio (hd0.4). Which overwrote my grub file, if I understand it correctly.

Yesterday I did 
```

sudo grub
grub>find /boot/grub/stage1
grub>geometry (hd0)
grub>geometry (hd1)
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
$exit
```

Now I can control the menu at boot again with /boot/grub/menu.lst. Which should mean that Hardy is controlling grub again, right?

But from here on it's all somewhat confusing for me. Is there a way to see if I installed grub on hd0,4.


Maybe this helps btw.
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd0,4)

```

---

### Post by philinux on 2009-03-09
You can also use config file if grub is installed on another partition or drive.

For instance.
title        Whatever's on sdb
configfile   (hd1,0)/boot/grub/menu.lst


This will bring up the grub menu on my second hard drive. This way when Jaunty on sdb gets a kernel update, it's menu.lst gets updated.

---

### Post by Ouia on 2009-03-09
Is that another way to edit your file or does that do something completely else?

And where would I place that?

---

### Post by bumanie on 2009-03-09
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5632a4d8-d571-4750-b433-d3ef788785ae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5632a4d8-d571-4750-b433-d3ef788785ae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5632a4d8-d571-4750-b433-d3ef788785ae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5632a4d8-d571-4750-b433-d3ef788785ae ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title	Jaunty Jackalope 9.04
root	(hd1,4)
chainloader +1

This is how I chainloaded jaunty alpha with intrepid being the main OS. The highlighted part is what I manually added. During the installation of jaunty I chose 'advanced' at the grub stage and told grub to install to (hd1,4).
Hope that helps you out.

---

### Post by philinux on 2009-03-09
This is the relevant bit of my menu.lst of the first hard drive sda. The end bit shows the config file entry. It does the same as chainloading. The advantage of useing chainloader or configfile is that it keeps each menu.lst tidy. I had to install grub to sdb to make this work, otherwise Jaunty's kernels would be listed in the one menu.lst on sda and would have to be manually updated.

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		9c1adaab-aa22-4638-96f3-5d4a3081e6b6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9c1adaab-aa22-4638-96f3-5d4a3081e6b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9c1adaab-aa22-4638-96f3-5d4a3081e6b6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9c1adaab-aa22-4638-96f3-5d4a3081e6b6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9c1adaab-aa22-4638-96f3-5d4a3081e6b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c1adaab-aa22-4638-96f3-5d4a3081e6b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9c1adaab-aa22-4638-96f3-5d4a3081e6b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c1adaab-aa22-4638-96f3-5d4a3081e6b6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9c1adaab-aa22-4638-96f3-5d4a3081e6b6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
title        Jaunty 64 SDB
configfile   (hd1,0)/boot/grub/menu.lst 
```

---

### Post by Ouia on 2009-03-09
Oh man, looks like I'm missing some point here. 

I am 1) assuming you have to install grub on each partition and then connect 1 grub to another.
Then I assume 2) that the grub from the default OS, is the one controlling the booting. And 3) that I have to chain the second grub to the default one.
4) root (hdx,y) is always the root from the partition the OS is on. So in my case hd0,0 for Hardy and hd0,4 for studio


that would mean I could do 2 things now. Delete everything below "### END DEBIAN AUTOMAGIC KERNELS LIST" and add:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
title        Studio 64bit
configfile   (hd0,4)/boot/grub/menu.lst
```

or 

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Studio 64bit
root (hdo,4)
chainloader +1 
```

assuming 5) that the title only changes the name in the menulist at boot

And 6) I assume grub is installed on both partitions. Is there a way to check that?

---

### Post by bodhi.zazen on 2009-03-09
See also : [How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

That thread reviews the options, including configfile :twisted:

---

### Post by Ouia on 2009-03-10
Just a question, maybe I figured out where my confusion lies.

Does the next code refers to a kernel or to the menulist on the other partition? (in other words, is it direct order to boot or an indirect one) If you understand what I'm getting at.

Because if it is the latter it would make sense to me. Whereas I assumed it was the first one.

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
title        Jaunty 64 SDB
configfile   (hd1,0)/boot/grub/menu.lst
```

---

### Post by philinux on 2009-03-10
> **Ouia said:**
> Just a question, maybe I figured out where my confusion lies.

Does the next code refers to a kernel or to the menulist on the other partition? (in other words, is it direct order to boot or an indirect one) If you understand what I'm getting at.

Because if it is the latter it would make sense to me. Whereas I assumed it was the first one.

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
title        Jaunty 64 SDB
configfile   (hd1,0)/boot/grub/menu.lst
```

It refers to the menu.lst on my second hard drive which contains the kernel entries etc. (hd1,0) is drive 2, linux starts at 0, and the first partition, / , on that drive. I installed grub to the mbr of my second hard drive

---

### Post by Ouia on 2009-03-10
Well, it seems that was the thing I was missing.

I used the config  method and when I boot to Studio now, I get another menulist for 1 second as specified, and it takes me to the right OS.

Thank you all very much for your help.

---

