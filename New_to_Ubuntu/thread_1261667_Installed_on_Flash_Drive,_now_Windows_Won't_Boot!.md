---
title: "Installed on Flash Drive, now Windows Won't Boot!"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Badmonkey005 on 2009-09-09
So my fiancée breaks up with me and I have to move in with my parents for a short while. How do I re-pay them? I screw up their computer.

I installed Ubuntu on my 8 GB flash drive. I'm running from the Live CD right now because for some reason when I try to start Windows XP (single boot on the HD) it says
"GRUB Loading stage1.5.


GRUB loading, please wait...
Error 21"

I can't even get to the BIOS options to change boot priority's. I'm screwed, please help.

P.S.

I checked and the windows files are still on the HD

---

### Post by eyeyoubin on 2009-09-09
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

hope this helps.

---

### Post by Badmonkey005 on 2009-09-09
Thank you so much.

Troubleshooting Update:

I tried starting Live CD and then using the "Boot from first hard disk" option and received the same error.

So I  took the battery out of the MoBo to clear the CMOS and started it back up after re-inserting the battery. Gave me a confirmation BIOS screen to start or enter setup. Started and got the same error. This time when I ran the Live CD I got a Synaptic Package Manager that automatically came up. Maybe unchecking the GRUB stuff to uninstall it? Not sure yet. Will try the above post first.

Thanks again, I will keep you updated.

---

### Post by oboedad55 on 2009-09-09
> **Badmonkey005 said:**
> Thank you so much.

Troubleshooting Update:

I tried starting Live CD and then using the "Boot from first hard disk" option and received the same error.

So I  took the battery out of the MoBo to clear the CMOS and started it back up after re-inserting the battery. Gave me a confirmation BIOS screen to start or enter setup. Started and got the same error. This time when I ran the Live CD I got a Synaptic Package Manager that automatically came up. Maybe unchecking the GRUB stuff to uninstall it? Not sure yet. Will try the above post first.

Thanks again, I will keep you updated.

Are you trying to get Windows running again?

---

### Post by Badmonkey005 on 2009-09-09
I never tried to stop windows from running. All I intended to do was install Ubuntu on my Flash Drive so that I could use it as an OS on this system without dealing with the constant noise of the CD drive on this computer.

I tried the advice posted above with no luck. I was able to succesfully get into the BIOS and navigate the Primary to Type: User and Mode LBA with Secondary being Auto but I got the same error.

I also tried uninstalling ALL packets that had been installed on my HD. This ended up in failure. I then tried just doing a "Complete Uninstal" of both GRUB packets on the HD which failed. When LIVE CD booted again I found that the GRUB packets were not really removed.

---

### Post by oboedad55 on 2009-09-09
> **Badmonkey005 said:**
> I never tried to stop windows from running. All I intended to do was install Ubuntu on my Flash Drive so that I could use it as an OS on this system without dealing with the constant noise of the CD drive on this computer.

I tried the advice posted above with no luck. I was able to succesfully get into the BIOS and navigate the Primary to Type: User and Mode LBA with Secondary being Auto but I got the same error.

I also tried uninstalling ALL packets that had been installed on my HD. This ended up in failure. I then tried just doing a "Complete Uninstal" of both GRUB packets on the HD which failed. When LIVE CD booted again I found that the GRUB packets were not really removed.

Well, if you just want Windows to boot up again just boot up the Windows XP CD and go to the repair console. Then run "fixmbr" and you'll be bootable again.

---

### Post by Badmonkey005 on 2009-09-09
do not have an xp cd. currently getting help on irc so this quote is for them:
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
# kopt=root=UUID=bcfd58cc-540c-4dcd-b01d-b5d784f860f3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bcfd58cc-540c-4dcd-b01d-b5d784f860f3

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bcfd58cc-540c-4dcd-b01d-b5d784f860f3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bcfd58cc-540c-4dcd-b01d-b5d784f860f3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bcfd58cc-540c-4dcd-b01d-b5d784f860f3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bcfd58cc-540c-4dcd-b01d-b5d784f860f3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bcfd58cc-540c-4dcd-b01d-b5d784f860f3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by Badmonkey005 on 2009-09-09
The problem is now solved. Much thanks to Indus and PaPaGoose on IRC for their massive amount of patience and help as well as the others who chipped in here and there. Here is what I ended up doing (for those who use the search button):

I downloaded the SuperGrubDisk from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and burned the .iso to a cd.

I then booted the CD and chose the quick fix (WIN => MBR & !WIN! :((((((((((((() to take the easy way out.

My computer booted and started with VAIO Recovery which faked me out with a blue screen of death.

I had to go back in and navigate the other menus (I do not remember how I got there, I was winging it) and found the partitions. Aparently there is a 5GB partition that is numero uno on the list which I'm guessing is how VAIO recovery stays uncontaminated from the rest of the HD. Of course when it was not properly called upon I got the BSOD.

I selected the second partition which booted me into windows but when I took the CD out and restarted went back to the VAIO recovery.

I started the CD again and navigated some more to find the actual "fix this for good" setting (my words, not the program's) which worked.

Thanks again to everyone who helped or tried.

---

