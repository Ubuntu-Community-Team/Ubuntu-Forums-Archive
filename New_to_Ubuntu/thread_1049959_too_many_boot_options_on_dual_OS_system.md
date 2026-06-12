---
title: "too many boot options on dual OS system???"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by ebineesey on 2009-01-25
i have ubuntu 8.10 and windows xp (set to default, shared computer), and i have the following partitions:

1 for xp NTFS
1 for backup storage NTFS
1 for ubuntu EXT3
1 swap

but it shows a ton of options when i'm at the boot menu.

what does all this mean?
i don't know the terminal code to list it (new to ubuntu), but will happily list it if somebody can tell me what to do

---

### Post by hayden92 on 2009-01-25
These are all boot options that you can choose. There should be memtest and recovery modes and the kernels that you can boot into.

If you do some research into Linux kernels, (try wikipedia or google).

To edit what you can see in the grub menu sudo edit the boot/grub/menu.lst file with the command "gksu boot/grub/menu.lst" and remove some entries that you don't want to see (I commented them out).

But do some research before you try anything!

Hayden

---

### Post by Montblanc_Kupo on 2009-01-25
I guess it depends what you mean by "a ton of options"...

Usually the ubuntu install will set up the GRUB boot loader with 3 options (initially) for ubuntu, and one for windows.

So you should get a "Ubuntu", a "Ubuntu Recovery Mode", and a "Ubuntu memtest"... then one for whatever windows version you have. Often you will get a duplicate of the three ubuntu when you run the updater... each with a different version of the linux kernel (each time the linux kernel is updated). This can be edited if you only want one.

More specific info about your problemw ould help us help you.

---

### Post by Michael.Godawski on 2009-01-25
I would leave the older kernels in the menu.list, in the grub boot loader.

So you can always switch back to a working kernel.

---

### Post by ebineesey on 2009-01-25
yea, one of them says yadayada-7, and the other says -9. i boot on the 9 one, i guess it came from the update. and I do see the 3 versions of each, plus windows... seems like a lot

but if they're all supposed to be there, i guess i don't have anything to worry about.

i can post more info if you tell me what to type into terminal to list it for me?

---

### Post by Michael.Godawski on 2009-01-25
Here we go:
```

cat /boot/grub/menu.lst
```

---

### Post by ebineesey on 2009-01-25
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		6

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
# kopt=root=UUID=3441e0e8-5afe-44ee-b698-631a336f95a0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3441e0e8-5afe-44ee-b698-631a336f95a0

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
# defoptions=quiet vga=795 splash

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
uuid		3441e0e8-5afe-44ee-b698-631a336f95a0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3441e0e8-5afe-44ee-b698-631a336f95a0 ro quiet vga=795 splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		3441e0e8-5afe-44ee-b698-631a336f95a0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3441e0e8-5afe-44ee-b698-631a336f95a0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3441e0e8-5afe-44ee-b698-631a336f95a0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3441e0e8-5afe-44ee-b698-631a336f95a0 ro quiet vga=795 splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3441e0e8-5afe-44ee-b698-631a336f95a0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3441e0e8-5afe-44ee-b698-631a336f95a0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3441e0e8-5afe-44ee-b698-631a336f95a0
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

```

---

### Post by bruce89 on 2009-01-25
The packages to remove are linux-image-2.6.27-7-generic linux-restricted-modules-2.6.27-7-generic and perhaps linux-headers-2.6.27-7 and linux-headers-2.6.27-7-generic.

I see no point in keeping old kernels once you've made sure the newest one works.

---

### Post by drs305 on 2009-01-25
StartUp-Manager is a gui app that will tweak the menu.lst settings without the user having to manually edit menu.lst  It can set how many kernels to view (one of your concerns), which OS is the default, how long to view the menu, etc. It does't remove older kernels (use Synaptic for that) but does change what you see.

Here is a tutuorial on how to use StartUp-Manager. I originally wrote it (just the tutorial, not the app!) specifically to address the number of kernel options viewed and expanded it from there:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

It also discusses manually editing menu.lst if that is what you decide to do.

---

### Post by Timi 9 on 2009-01-25
OK that's simple!But you must be very carefull,install Startup manager,and you'll see the options to show memtest and recovery mode,or something like that.Then you can uncheck the boxes,also you have the option to show only one kernel or more,if there are more.Usually if you decide to go for one kernel,it will be the most recent one plus Windows and that's it.You can change with this utility and the startup usplash but only in older versions of Ubuntu,in Intrepid doesn't work,it has a bug!Never select 0 kernels or you will and up only with Windows!

---

### Post by Montblanc_Kupo on 2009-01-25
Personally... this is what I did...

When I got a kernel update... I would leave the old kernel in the list for a week and use the new one in case there were any problems I could load into the old kernel. If I haven't seen any issues, I would edit the menu.lst and *comment out* the entries I wanted hidden so I only had the recent kernel in the list ... just to make the list more manageable. 

If there was really a problem caused by a specific kernel... it wouldn't be that hard to boot on a livecd... find the menu.lst file and uncomment the entries (or replace with a backup) so that you can load the older kernel again.

$0.02

---

