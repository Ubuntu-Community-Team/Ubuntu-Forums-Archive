---
title: "Bootloader/chainloading help?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Guyon on 2009-08-25
So, I've messed up. I boot Ubuntu off an external drive (hd1) with GRUB also on the external. I installed Kubuntu on the drive to test it out, and later removed it. Upon reboot I got GRUB Error 22 (deleted partition). I followed this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and messed up a very simple step and installed GRUB to hd0 rather than my pre-existing hd1. This gave me GRUB error 17 (Invalid device requested). I went back around and installed GRUB on hd1, which helped, but now upon reboot I get Error 21 (unknown boot failure). 

To boot off hd1 I now have to go to the boot menu and manually go to hd1, where I can successfully (Yes!) boot onto Ubuntu, however, booting Vista doesn't work, but that's a minor issue because I don't use it. My main problem is that if when started, if left alone, it will run right into GRUB to get error 21. 

Is there a way I can restore it so that on boot GRUB prompts me to choose my OS again? Does this require a restore of the windows bootloader?

Thanks in advance.

---

### Post by kansasnoob on 2009-08-25
So, you were already dual-booting Vista and Ubuntu on the internal drive?

---

### Post by Guyon on 2009-08-25
> **kansasnoob said:**
> So, you were already dual-booting Vista and Ubuntu on the internal drive?

Vista on the internal drive, Ubuntu on an external drive. Sorry for not being too clear.

---

### Post by kansasnoob on 2009-08-25
Well, going back to the guide you posted, if you now go to terminakl while booted into Ubuntu and:

```
sudo grub
```

Then:

```
find /boot/grub/stage1
```

Does it now show two options? If so just choose the option "(hd1,0)" [I'm guessing it will be (hd1,0)].

Then run:

```
root (hd1,0)
```

And:

```
setup (hd1)
```

And:

```
quit
```

Or maybe just post the output of "find /boot/grub/stage1" here.

---

### Post by Guyon on 2009-08-25
This is what I did after I was getting Error 17, I had done this before but did it just to double-check. Still the same result (Error 21). And yes, 
```
find /boot/grub/stage1
```
resulted in (hd1,0)

---

### Post by kansasnoob on 2009-08-25
Well, I'd complete the steps I listed above, but don't reboot yet. I'd like to see the output of the following two commands:

```
sudo fdisk -l
```

and:

```
cat /boot/grub/menu.lst
```

---

### Post by Guyon on 2009-08-25
sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c4455cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       35653   275892867    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9255cefb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

```
cat /boot/grub/menu.lst
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
timeout		4

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
# kopt=root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e6c12eb-8530-4552-a097-4d97c8929215

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e6c12eb-8530-4552-a097-4d97c8929215 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9e6c12eb-8530-4552-a097-4d97c8929215
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```
Glad somebody knows what they're doing. :D

---

### Post by kansasnoob on 2009-08-25
**Read this in it's entirety and if you're unsure about anything ask first!**

Well I'm thinking this part of the menu.lst:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Should be edited, but rather than "cut" and "edit" what's there we'll just comment out some of the existing lines with #, and we'll add the new lines at the bottom. After editing it should look like this:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
**#**title		Windows Vista/Longhorn (loader)
**#**root		(hd0,0)
**#**savedefault
**#**makeactive
**#**chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
**#**title		Windows Vista/Longhorn (loader)
**#**root		(hd0,1)
**#**savedefault
**#**makeactive
**#**chainloader	+1

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
map        (hd1) (hd0)
map        (hd0) (hd1)
chainloader    +1[/B]



You'll notice that all of my edits are in **bold** only so you can see what I've changed. Of course to make edits to the menu.lst you must run the command:

```
gksudo gedit /boot/grub/menu.lst
```

And after editing be sure to click on Save, then File > Quit.

Also I'd increase the timeout to 10 (which is 10 seconds), and it would be good to clean up that long list of kernels, but first I want to be sure you're actually booting kernel 2.6.28-15-generic. You can see by running the command:

```
uname -r
```

If you are running 2.6.28-15 then let's install a nifty tool to do some clean up (it's also totally reversable):

```
sudo apt-get install startupmanager
```

After installed it'll show up in System > Administration:

[ATTACH]126157[/ATTACH]

[ATTACH]126158[/ATTACH]

You can see I've adjusted the timeout in the first screenshot and chosen to keep only two kernels in the second.

Of course if you want to be able to boot Vista without having the external drive plugged in that's a different story. You'd need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by Guyon on 2009-08-25
Thanks for all the help, startupmanager is neat, only having 2 kernals is quite nice, I was wondering how to do this anyway. I no longer get that error message, but not the computer boots straight into Vista instead of going to GRUB. Any idea how I could get GRUB to run on boot?

---

### Post by kansasnoob on 2009-08-25
Uh, which steps did you follow?

I've worked on a few machines since then so I need a recap. Did you restore the Vista mbr or just make the menu.lst changes?

I should add that we're currently having sporadic power outages so I could disappear for a while.

---

### Post by Guyon on 2009-08-25
> **kansasnoob said:**
> Uh, which steps did you follow?

I've worked on a few machines since then so I need a recap. Did you restore the Vista mbr or just make the menu.lst changes?

I should add that we're currently having sporadic power outages so I could disappear for a while.

Both. First I did the menu.lst changes, then restored the Vista mbr. It's okay. I'm in no big hurry. :)

---

### Post by kansasnoob on 2009-08-25
And now you get no GRUB menu at reboot even if the external drive is plugged in?

I know this is a lot to absorb but it's where I learned:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

You'll notice there are a few options.

Another great resource:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Guyon on 2009-08-26
That's correct, but it is still accessible through going through the boot menu -> Boot from hard drive -> External

---

