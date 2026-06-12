---
title: "boot system failure"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by DarinB on 2009-09-14
boot system failure insert disk?????
when i insert a 9.04 disk i can boot up and even access my system drive, and my windows drive so not sure the hdd must be working if i can see the files. do i need to restore the grub or something????? i am really lost right now and need this thing to work HELP
I have my home partition on a separate drive as well as my music, if that is any help. i do have the original vista on a partition on the same drive all of ii is visible and can be opened when using a live cd.

---

### Post by Pirolocito on 2009-09-14
Post here the content of your /boot/grub/menu.lst

The problem must be there! Or not!

---

### Post by DarinB on 2009-09-14
i need more how to than that when i turn it on after the motherboard screen it just flashes boot system failure, i have no access to anything even windows. if i add the live cd i can but where do i fond what you are asking for cant i rebuild the boot menu or replace it. or something??????? using the live cd????

---

### Post by paultag on 2009-09-14
Hey buddy.

Here is what you need to do. There are a few red flags that I see.

First:
 Check the simple stuff. Make sure the boot order is correct.

Second:
 Boot from a Live CD, and preform a check on the HDD.

Third:
 If the HD is healthy, and the BIOS is set right, try a grub reinstall to the MBR. Remember to ensure your menu.lst and system.map are set up right!

If you get to the third step, post back here, and we can walk you through a more total work through.

Have a great day, all is not lost!

---

### Post by Pirolocito on 2009-09-14
if you can access your drives from the live cd you will be able to go to your linux partition and see the content of /boot/grub/menu.lst

And post it here.

---

### Post by stderr on 2009-09-14
Are you sure there's no floppy in the floppy drive? ;)

I trust you're using GRUB to dual boot between Ubuntu and (shudders) Micro$h** 'Vista'?

Here's a howto for repairing GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I am quite skeptical as to whether the problem will be in menu.lst. However, in terms of finding it you can mount your Ubuntu system partition in the live CD, and then literally 

```
gedit /boot/grub/menu.lst
```

edit: Yeah, just follow the steps paultag has given, best to double-check the BIOS and ensure your HDD isn't screaming SMART errors or the like first!

---

### Post by paultag on 2009-09-14
> **Pirolocito said:**
> if you can access your drives from the live cd you will be able to go to your linux partition and see the content of /boot/grub/menu.lst

And post it here.

Good advice, but in this case not very useful. GRUB would fail if the menu.lst is messed up. This is an issue involving the MBR.

Still, great approach.

---

### Post by DarinB on 2009-09-14
my boot order is dvd then hdd, as it has always been
i can change it if you like to hdd first ????
i will run a hdd check how do i do that with the live cd?

---

### Post by paultag on 2009-09-14
look into `fsck` ( or file system check ) for running a basic test on the integrity of the filesystem data structure.

As for your BIOS, you might have to consult your documentation for the machine. Also, make sure there is no other medium in your machine on boot. As stderr put it ( quite well ), we have all had the floppy mess up boot. Make sure there is no DVD or CD in the drive, or floppys in the machine :)

---

### Post by DarinB on 2009-09-14
Ok i got it checking it says it will take some time? step 3 seems really complicated i will need some more explanation?

---

### Post by paultag on 2009-09-14
> **DarinB said:**
> Ok i got it checking it says it will take some time? step 3 seems really complicated i will need some more explanation?

stderr had a great post, check out his links :)

---

### Post by DarinB on 2009-09-14
nope no media in i am doing a check disk from the live cd. ok it is done no errors found bi what ???

---

### Post by paultag on 2009-09-14
> **DarinB said:**
> nope no media in i am doing a check disk from the live cd. ok it is done no errors found bi what ???

Check out stderr's link here:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by LewRockwell on 2009-09-14
Super Grub Disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

{{sigh}}

---

### Post by DarinB on 2009-09-14
after the disk check it asked if i want to boot from the 1st disk and it worked i am on it now by the way here is the grub thing what is going on and what if it happens again?????
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
color light-gray/blue light-red/blue

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
# kopt=root=UUID=e0d87cdd-443d-4f69-884e-469bc431b1f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0d87cdd-443d-4f69-884e-469bc431b1f5

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
# defoptions=splash quiet

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		e0d87cdd-443d-4f69-884e-469bc431b1f5
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=e0d87cdd-443d-4f69-884e-469bc431b1f5 ro splash quiet 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		e0d87cdd-443d-4f69-884e-469bc431b1f5
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=e0d87cdd-443d-4f69-884e-469bc431b1f5 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		e0d87cdd-443d-4f69-884e-469bc431b1f5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by DarinB on 2009-09-14
OK does this make sense, my system is having a problem with my firefox and sometimes freezes. when i rebooted the boot system failure, i was just noticing that with the live cd if i choose boot with 1st hdd, it works fast, and gives me the grub. but not on its own i went into the bios again and the hdd order was flipped so i moved up the 1st hdd to the #1 position and it booted fine, ????? can anybody explain what is going on or is my machine haunted????

---

### Post by LewRockwell on 2009-09-14
haunted


you need a poltergeist

.

---

### Post by stderr on 2009-09-14
It would appear slightly odd that it was behaving in that fashion. With the boot order set to CD and then hard drive, what typically happens is first it checks if there's a bootable CD/DVD in the drive. If there isn't, it should move on to the next boot device - in your case, the hard drive. If there is a bootable CD/DVD, it typically prompts you to press a button to boot to the media; if you do, it boots it if possible, and displays an error similar to the one you got if it can't boot it for whatever reason. If you don't press the 'any' button ;) to boot to the disk, it moves on to the secondary boot device (the hard drive). 

Did you have another CD/DVD in the drive when you were encountering problems? It could simply be the case that your motherboard isn't handling it very well; whereas most prompt to boot to CD/DVD, perhaps yours doesn't bother, and was trying to boot a non-bootable disk. 

Anyway, sounds like it's resolved now :) With the boot order set to hard drive first, it will ignore all disks in your CD/DVD drive and just boot to your primary hard drive (i.e. the GRUB menu). Just remember the edit you made, so that in future if you want to use the Live CD again, you remember to go back into the BIOS and change the boot order, so you're not left repeatedly rebooting and getting confused as to why your CD/DVD drive doesn't appear to be working!

---

### Post by DarinB on 2009-09-14
maybe a priest to exorcise my machine. 
I am afraid the screen will turn in a circle and the dvd will start vomiting green goo.

---

### Post by DarinB on 2009-09-14
what can be causing the boot order of the hdd to flip, it just happened again after another firefox related freeze up???????? is it the bios the motherboard or the system freeze,,,,nothing was in the cd but it did not move from one hdd to the other looking for a bootable partition. 2 things why does it change and why is it not moving on to the next hdd?

---

### Post by stderr on 2009-09-14
I have encountered odd boot sequence behaviour before, but I have no idea how BIOS settings could change by themselves - I've never encountered that happening, ever, in any system I've built/repaired/upgraded/used. To be clear, you went back into the BIOS and the boot order had reverted by itself??

I'm slightly concerned about the Firefox freezes anyway. Sounds like either a dodgy plugin you're using, or because Firefox uses quite a bit of RAM, perhaps you have a dodgy RAM module (a few memtest86+ runs may be a good idea) - see what others think first regarding your BIOS issue though.

---

### Post by DarinB on 2009-09-14
yes, it did change to put the 1 sata drive in the number 2 position, once before it was moved to the no 3 position, very bizarre yes i did a ram test and there were so many errors i just about messed my self, i am trying to ignore it since the dam thing is out of warranty, so much for going to a third party to build a pc. even though i thought i was ordering a good box. funny though i never had a crash until i upgraded my firefox to 3.0 then worse on 3.52 i do know that xmarks is a disaster with 3.0 and higher, it is even on their web site. i just turned on xmarks to up load my latest bookmarks and it closed about every 10 seconds. so not really sure wtf is going on. i have resorted to praying since funds are tight now. pretty sad hoping that a clean install of karmic will help i do have a separate hdd for my home and music. so i am waiting for a short while after that will be released maybe i can hold out until nov or dec. thanks for being precise and clear in your answer some answers are not worth reading. or way over a relative beginners head.

---

### Post by stderr on 2009-09-15
No problem DarinB. If memtest86+ is giving you a whole host of errors, chances are you really do need new RAM. Another possibility is that it is the motherboard causing problems. This could also explain your bizarre boot order issues. 

If it is RAM, then replacing your modules should be very cheap, easy and quick (RAM module prices have plummeted of late!) On the other hand, if it's your motherboard, then that's a pain in the backside to replace, and depending on the precise specifications of your system, it could conceivably be more difficult to get one that will work with your other components.

It would help to know more about your system and specifically your RAM - how many modules have you got, are they DDR I or DDR II, how large are they (how many MegaBytes), etc. If you have multiple RAM modules in your system, then that presents an opportunity - you can remove all but one of the modules (again, we'd need to know more about your system, because often you have to use a specific RAM slot when you're running just one module) and run memtest86+ tests again to see if you're still getting errors. Basically, we're trying to find out if just one of your modules is causing problems. If we can isolate it to one module, then that'll rule out the motherboard as a problem, and give you time to run your system in a stable state whilst ordering a new module (cheaply :)).

The easiest way to determine how many modules you have is to open the case and look, but another almost equally easy method is to look in the BIOS. It will normally tell you somewhere in there. Alternatively (and this would be good) you could run this command in a terminal and post the results here:

```
sudo lshw -C memory
```

If it moans that you haven't got lshw installed, you can install it with:

```
sudo apt-get install lshw 
```

On the other hand, if you're uncomfortable about opening your case and dealing with hardware, then maybe you'd feel happier taking your system to another one of those 3rd parties ;) and getting them to deal with it. If it's simply a RAM issue though, you can likely handle it yourself with a little help, and thereby save yourself some unnecessary service fees.

---

