---
title: "Still booting into kernel 2.6.24 following upgrade to Ubuntu 8.10"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by BoundaryNoob on 2009-02-13
I have attempted the upgrade from Ubuntu 8.04 to 8.10 (32-bit) using upgrade manager.  The download and install was very slow but apparently succeeded in that the new system booted; however it immediately failed to display at anything higher than 800x600.  

I have an Nvidia NX7600GS card and assumed a driver problem as described in BinaryDriverHowtoNvidia.  I downloaded the nvidia-glx package with its dependent packages (nvidia-glx-173,177, 71, and 96) and activated version 177 using the hardware drivers manager.  On re-starting the display resolution was unchanged.  Also tried modifying the xorg.conf file by adding refresh rate lines in the 'Monitor' section, but also no success.

I then realised that I might well have created the problem during the upgrade by instructing the upgrade manager that I wanted to retain my original Grub boot menu (I have dual boot with Windows XP).  The menu still shows Ubuntu kernel 2.6.24-21 generic (and this is confirmed as loaded using uname -a).  But I think that Ubuntu 8.10 should be using kernel 2.6.27.

On searching for 2.6.27-11 generic I have found the file located in /usr/share/doc.  So perhaps I have the new kernel installed but I'm still booting into the old one?  I also find that I have 2.6.27 kernel headers loaded, which, if I'm actually running 2.6.24-21 might be the reason why my video driver is not working.

I tried reloading Grub using a 8.10 live cd, but the boot menu is unchanged and still seems to boot into kernel 2.6.24.

The first step seems to be to find out if I'm right in thinking I'm  booting into the old kernel.  If so how can I get it to boot into the new one?

I am very much a newbie, so step by step guidance would be really helpful!

Thanks.

---

### Post by hellion0 on 2009-02-13
```
sudo update-grub
```

Run that in a Terminal. It should update your GRUB list with any new kernels. While you've got that Terminal open, run this:```
uname -a
```
Then post back here with what's there - it should look sort of like this (the following is from my laptop):
```
Linux flygon 2.6.27-11-generic #1 SMP Thu Jan 22 17:22:40 UTC 2009 i686 GNU/Linux
```
From there, we can help further.

---

### Post by BoundaryNoob on 2009-02-13
Thanks for the quick reply Helion0.

Updated Grub as you suggested and used uname -a.

Here's the terminal output:

al@Officemachine:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

al@Officemachine:~$ uname -a
Linux Officemachine 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
al@Officemachine:~$

So it still seems to be persisting with 2.6.24, although 2.6.27 is in there.

I tried rebooting after the Grub update and the old boot menu is still coming up.

Any ideas?

---

### Post by hellion0 on 2009-02-13
I can at least tell you a quick and dirty fix that would let you boot into your new kernel even with it not on the list. I hope your memory is good, or you have pen and paper or something.

See where your kernel resides? It's listed in your update-grub command as "/boot/vmlinuz-2.6.27-11-generic".

Reboot. While GRUB is active, select "Ubuntu 8.10, kernel 2.6.24-21-generic" and hit the "e" key.

Hit the down arrow key until you get to the line starting with "kernel". Hit "e" again.

Use the left arrow to get back to the start of the line. Change
```
/boot/vmlinuz-2.6.24-21-generic
```
to ```
/boot/vmlinuz-2.6.27-11-generic
```
...then hit Enter. From there, go to "initrd" and hit "e" again. Change
```
/boot/initrd.img-2.6.24-21-generic
```
to ```
/boot/initrd.img-2.6.27-11-generic
```
...and when done, hit Enter, then "b". 

Then hit Enter. If all goes right, you should boot into the new kernel. If not, you haven't permanently changed anything, so you can still boot back into the old kernel.

Give it a try, and let us know what happens.

---

### Post by BoundaryNoob on 2009-02-13
Having a slight problem that the edits are not being saved when I hit Escape!

---

### Post by hellion0 on 2009-02-13
My bad. After completing the edits, hit **Enter** instead of Escape. Also, when done, instead of hitting Escape twice, hit **Enter**, then "**b**".

---

### Post by BoundaryNoob on 2009-02-13
Major progress!

Following your instructions I've successfully booted into 2.6.27-11.  The video issues that started this journey have been solved now!  Thank you. :)

The only problem is that, when I reboot, the old grub menu still appears.  The edits are not persisting beyond the current session.

---

### Post by hellion0 on 2009-02-13
As I said, not permanent. Still, it's progress. At least you know the new kernel's there.

Try running sudo update-grub again under the new kernel. It can't hurt at this stage.

---

### Post by BoundaryNoob on 2009-02-13
Tried sudo update-grub but still not making a permanent change.

Would it work to edit the boot/grub/menu.lst file directly?

---

### Post by hellion0 on 2009-02-13
Not recommended unless you know what you're doing... post your /boot/grub/menu.lst here, preferably in {code} (replace {} with []) tags.

---

### Post by BoundaryNoob on 2009-02-13
Here's the menu.lst.  I'm not sure about dealing with your request "preferably in {code} (replace {} with []) tags".  I've just copied and pasted - hope this is OK.

(I bet there is a good chance that my current problem is caused by my historic meddling with this file....)



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
timeout		20

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
# kopt=root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1 (moved up by AL)
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# Windows moved up list to boot first!

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		MEPIS at sda8, newest kernel (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz root=/dev/sda8 nomce quiet splash vga=791 resume=/dev/sda9 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
#title		MEPIS at sda8, kernel 2.6.22-1-mepis-smp (on /dev/sda8)
#root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.22-1-mepis-smp root=/dev/sda8 nomce quiet splash vga=791 resume=/dev/sda9 
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
#title		MEMTEST (on /dev/sda8)
#root		(hd0,7)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot

---

### Post by hellion0 on 2009-02-13
Ok, I can see where it's been played with, moving Windows up and all... no harm in one more edit, I guess.

What I'm about to suggest here may break Grub. In fact, it just might, but it's all I can think of. Honestly, it's something I'd try myself, too.

After the entry for Windows but before the first Linux one, add this:

```
title Ubuntu 8.10, kernel 2.6.27-11-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root (hd1,5)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=9e406783-5057-4a89-9960-e4ce9096f3ad ro single
initrd /boot/initrd.img-2.6.27-11-generic
```

Once done editing, run this command:
```
sudo depmod -a && sudo update-grub
```

Make sure you have the LiveCD or the Super Grub Disc handy, reboot, and cross your fingers.

---

### Post by BoundaryNoob on 2009-02-13
Great cliff-hanger ending helion0 but you did it!

Thanks for all your help :P

Just for the record (and my education), what did the depmod command do?

---

### Post by hellion0 on 2009-02-13
Depmod would make sure all the needed modules were spot on for all kernels. I had to use it when I edited that list on a Thinkpad, so I figured "better safe" and all that.

---

### Post by BoundaryNoob on 2009-02-14
Thanks - I guess this one's successfully closed!

---

### Post by Paqman on 2009-02-14
For future reference: you don't need to edit /boot/grub/menu.lst manually. Just install startupmanager and it'll do it for you. It can also do a lot of other nice things like cleaning up Grub menus, changing splash screens, etc.

---

### Post by BoundaryNoob on 2009-02-14
> **Paqman said:**
> For future reference: you don't need to edit /boot/grub/menu.lst manually. Just install startupmanager and it'll do it for you. It can also do a lot of other nice things like cleaning up Grub menus, changing splash screens, etc.

Thanks Paqman - I've learned a lot from the process (but the hard way!)

---

