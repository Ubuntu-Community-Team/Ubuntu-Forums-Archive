---
title: "Editing grub?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Nottawa on 2009-11-15
I had a successfully working Jaunty and Vista set up.  Then I installed Win 7, with predictable results ( I learned after).  After finding the thread on dual booting with Jaunty and Win 7, I fixed the problem and have my dual boot back.  But my grub is cluttered with all sorts of other things, including Vista.  How can I get rid of the unwanted lines in my selector screen?

---

### Post by nitstorm on 2009-11-15
see that...

[http://ubuntuforums.org/showthread.php?t=169234](http://ubuntuforums.org/showthread.php?t=169234)

---

### Post by laidback on 2009-11-15
Have a look here for documentation:-

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by kansasnoob on 2009-11-15
> **Nottawa said:**
> I had a successfully working Jaunty and Vista set up.  Then I installed Win 7, with predictable results ( I learned after).  After finding the thread on dual booting with Jaunty and Win 7, I fixed the problem and have my dual boot back.  But my grub is cluttered with all sorts of other things, including Vista.  How can I get rid of the unwanted lines in my selector screen?

If you'd like more specific help go to Terminal in Jaunty and then post the full output of this command:

```
cat /boot/grub/menu.lst
```

BTW that's a lower case L.

---

### Post by Nottawa on 2009-11-16
> **kansasnoob said:**
> If you'd like more specific help go to Terminal in Jaunty and then post the full output of this command:

```
cat /boot/grub/menu.lst
```

BTW that's a lower case L.
Kansas:  Here is the output from your requested command:

peter@peter-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=7dbefb59-2e28-47b4-8d56-f4aca936ed6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7dbefb59-2e28-47b4-8d56-f4aca936ed6a

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		7dbefb59-2e28-47b4-8d56-f4aca936ed6a
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7dbefb59-2e28-47b4-8d56-f4aca936ed6a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		7dbefb59-2e28-47b4-8d56-f4aca936ed6a
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7dbefb59-2e28-47b4-8d56-f4aca936ed6a ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7dbefb59-2e28-47b4-8d56-f4aca936ed6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dbefb59-2e28-47b4-8d56-f4aca936ed6a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7dbefb59-2e28-47b4-8d56-f4aca936ed6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dbefb59-2e28-47b4-8d56-f4aca936ed6a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7dbefb59-2e28-47b4-8d56-f4aca936ed6a
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

title Windows 7 (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

peter@peter-laptop:~$ 
peter@peter-laptop:~$ 


The first half seems to be background info.  The second half shows the lines I get on boot up.  Do I need/want 2 versions of Jaunty?  I know I don't want Vista.  The rest I either want or can see possible future need for.  Thanks for your help.

---

### Post by Miljet on 2009-11-16
Yes, you want 2 versions of Jaunty. It is a good idea to always keep the latest 2 kernel versions. If the new version breaks something, you can always boot the older one.

Do you in fact still have Vista installed? I think not since both Vista and Win 7 are showing hdo,o. In any case if you are sure that you will never boot Vista, you can safely remove it from your menu.lst file.

Open terminal and enter
```
gksudo gedit /boot/grub/menu.lst
```
Make your changes, save, and exit.

---

### Post by kansasnoob on 2009-11-17
> **Miljet said:**
> Yes, you want 2 versions of Jaunty. It is a good idea to always keep the latest 2 kernel versions. If the new version breaks something, you can always boot the older one.

Do you in fact still have Vista installed? I think not since both Vista and Win 7 are showing hdo,o. In any case if you are sure that you will never boot Vista, you can safely remove it from your menu.lst file.

Open terminal and enter
```
gksudo gedit /boot/grub/menu.lst
```
Make your changes, save, and exit.

+1! If you want to play it really safe you can use "comments" # like shown below rather than deleting text (I used red just to make it obvious):

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[COLOR="Red"]#[/COLOR]title Windows Vista (loader)
[COLOR="Red"]#[/COLOR]rootnoverify (hd0,0)
[COLOR="Red"]#[/COLOR]savedefault
[COLOR="Red"]#[/COLOR]makeactive
[COLOR="Red"]#[/COLOR]chainloader +1

title Windows 7 (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

You might also want to take a look at Startup Manager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

As shown there you can change the timeout or if you uncheck it then the menu will just sit there until you make a selection, select default, etc.

If you click on the Advanced tab you can also choose whether or not to have the MemTest show up (how often do we use that), or even how many kernels to display.

---

### Post by Nottawa on 2009-11-17
Thank you for your answers.  I appreciate Kansasnoob's recommendation as it let me try it out first before making the changes permanent.

---

