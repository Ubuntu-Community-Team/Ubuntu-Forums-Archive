---
title: "Dell Studio 1535 -- Function key hangs the Menu bar"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by dhirendra1 on 2008-12-30
I have just installed ubuntu 8.10 on Studio 1535 (Core 2 Duo, ATI Radeon 3450).  The system works perfectly till I press the function key on the keyboard to reduce the brightness.  Once it is done, following happens :

1.  the Menu bar on the panel stops showing the drop down menu.  Other buttons on the panel viz. Firefox etc. are working. Drop-down menus (Application, system etc) get highlighted but nothing more.

2.  the Keyboard totally locks and nothing can be typed.....even on the google search.  

3.  Mouse works but windows can not be moved on the screen...The firefox menus can howver be opened...however, the browsing can be done during this hang up...

If function key alone is pressed, it doesn't give any problem....all the above happen the moment up or down key is pressed in conjunction with it.

The Ctrl+Alt+backspece revives the xorg and works perfectly again till Function key comes into picture....

One more thing...no such problem was encountered with Kubuntu 8.10 on the same machine.....but I wanted to switch to Ubuntu...

Any idea what is wrong ??? Any suggestion???

---

### Post by aw47 on 2009-01-11
I'm  experiencing the same problem.
Any suggestions?

---

### Post by aw47 on 2009-01-11
It appears this bug has been reported:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/285323]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/285323")

---

### Post by aw47 on 2009-01-11
ok, a bunch more googling turned up a thread about this being fixed with a kernel update:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721")

Bottom line, update to 2.6.27-11 proposed to fix the problem.

to check your current version:
$uname -r

---

### Post by aw47 on 2009-01-11
I updated the kernel and can confirm it fixed the problem.

Steps:
add the following line to the end of /etc/apt/sources.list:
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

run:
$ sudo apt-get install linux-image-2.6.27-11-generic

reboot

---

### Post by dhirendra1 on 2009-01-11
Thanx...it worked....

---

### Post by Jammanuser on 2009-01-11
I am having the same problem. I also have the Dell Studio 1535 laptop. I will try upgrading to the latest kernel, and see if that fixes it. Just one question, though, before i begin...;)

Will i need to edit my menu.lst to display the correct kernel, after upgrading, or is this done automatically when upgrading?

Looking forward to a reply.

-Jam man

:guitar:

EDIT: I currently have the 2.6.27-7-generic kernel.

---

### Post by Jammanuser on 2009-01-11
Bump.

---

### Post by Jammanuser on 2009-01-11
> **aw47 said:**
> I updated the kernel and can confirm it fixed the problem.

Steps:
add the following line to the end of /etc/apt/sources.list:
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

run:
$ sudo apt-get install linux-image-2.6.27-11-generic

reboot

Nope...it didn't work! :( I added that line to my sources, ran apt-get, everything looked like it worked, a GUI popped up in the terminal afterwards asking me if i wanted to keep the menu.lst i had or download a new one, i chose to keep the one that i had, rebooted, thought everything was correct...until trying it! I pushed the Fn + Up arrow keys and the same thing happened...puzzled, i manually rebooted, and then ran **uname -r** in my terminal again, and found out the 2.6.27-**7**-generic kernel is still installed! :shock: And so i tried it again, but got a response in the terminal saying 2.6.27-11-generic is already installed, but rebooted again, checked uname -r again, and same result! :-k

For whatever reason, it doesn't appear to have upgraded my kernel...:?

-Jam man

:guitar:

---

### Post by aw47 on 2009-01-12
I'm guessing that since you kept the existing menu.lst, the new kernel choice was not added. Try adding the following lines to /boot/grub/menu.lst, right after the "## ## End Default Options ##" line so it appears as the first choice:

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ee91ca12-a03c-4705-9107-7e4ab20018ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ee91ca12-a03c-4705-9107-7e4ab20018ab ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

NOTE: you need to change your root UUID to whatever your actually is...you should  see it in the other kernel options

---

### Post by Jammanuser on 2009-01-16
> **aw47 said:**
> I'm guessing that since you kept the existing menu.lst, the new kernel choice was not added. Try adding the following lines to /boot/grub/menu.lst, right after the "## ## End Default Options ##" line so it appears as the first choice:

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ee91ca12-a03c-4705-9107-7e4ab20018ab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ee91ca12-a03c-4705-9107-7e4ab20018ab ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

NOTE: you need to change your root UUID to whatever your actually is...you should  see it in the other kernel options

Thanks, that worked! :D Mostly...
It fixed the problem with the wrong kernel being used, and fixed the issue with the fn keys, but now my wireless driver doesn't work! :( I guess the one I have currently on works with the 7 kernel, and not the 11? 

BTW, what did you mean by "other kernel options"? Nowhere in my menu.lst could I find that, so I ended up just changing the "7" to "11", without changing the UUID numbers, and it works now...all except for my wireless driver! :guitar:

Any idea why on how to fix it?

Here's a copy of my menu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
```

Thanks, and looking forward to your next reply! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-17
Bump. ^

---

### Post by dhirendra1 on 2009-01-18
Same happened with me when I installed Kernel version -11 to make Fn key functional.  Wireless just stopped working.  After trying so many things.....I deactivated and again reactivated the driver for WLAN card....deleted the earlier functinal connection...cleared out the Keyring...and then reconnected....and voila, it worked.....Just a hunch....may work for you as well....

---

### Post by Jammanuser on 2009-01-18
> **dhirendra1 said:**
> Same happened with me when I installed Kernel version -11 to make Fn key functional.  Wireless just stopped working.  After trying so many things.....I deactivated and again reactivated the driver for WLAN card....deleted the earlier functinal connection...cleared out the Keyring...and then reconnected....and voila, it worked.....Just a hunch....may work for you as well....

Ok, thanks. :) But how do I deactivate the driver, and do the other things you mentioned? Sorry, I'm a bit new to Linux...;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-02-01
Bump again. ^_^ :)

-Jam man

:guitar:

---

