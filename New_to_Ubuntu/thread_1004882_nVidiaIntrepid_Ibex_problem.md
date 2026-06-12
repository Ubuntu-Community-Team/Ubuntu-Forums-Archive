---
title: "nVidia/Intrepid Ibex problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Dark006 on 2008-12-07
First, click [HERE]("http://www.nvnews.net/vbulletin/showthread.php?t=124315") to see what my problem is (its posted at another site). I'm posting here because I still cannot get any nvidia drivers to work in Intrepid. The replies I got over there didn't really help, and I've tried to get them working through Synaptic with no luck. Does anyone have any idea why this is so damn complicated? I've been trying to get these friggin' drivers to work since intrepid came out and still have not been successful. Please help, I'm very annoyed because this has been the only pain in the *** thing I've dealt with since I started using Linux (I've been using Ubuntu for 8 months). Sorry for the angry tone, I'm just...GGGRRR!!!!

---

### Post by gettinoriginal on 2008-12-07
What happens when you go to System > Admin > Hardware Drivers ??  All I did after updating was set it there and it worked.

---

### Post by Sealbhach on 2008-12-07
What Nividia card have you got?  

You could try this method if your card is not really ancient:

[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

Be careful though, be sure to undo what you did, or you will be offered hundreds of updates. It worked fine for me.


.

---

### Post by Dark006 on 2008-12-07
Yup, I already tried going to System > Admin > Hardware drivers and tried activating 173 and 177 with no success.

I have a GeForce 6800 video card.

---

### Post by doas777 on 2008-12-07
have you tried [envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

---

### Post by Dark006 on 2008-12-07
Sealbhach, I tried that guide that you posted, but I don't think that worked either. How would I tell if it is installed? I checked hardware drivers again and nvidia-glx-180 didn't show up, and nvidia settings still says I'm not using an nVidia driver. Everytime I try to install one of these drivers (no matter what way I do it, manually, synaptic etc.) it always references something about linux-source or kernel-source and I think linux-headers also. This thing is so stubborn, I'm considering changing distro's.

---

### Post by Dark006 on 2008-12-07
doas777, I just installed envyNG and ran it, and it gave an error message saying that the headers for my kernel are missing and it cannot be installed. So the question is, how do I get my kernel headers?
I've tried to download them, sudo apt-get install linux-headers-`uname -r` but that doesn't work, it either says it can't find that file or has no installation candidate.

---

### Post by doas777 on 2008-12-07
> **Dark006 said:**
> doas777, I just installed envyNG and ran it, and it gave an error message saying that the headers for my kernel are missing and it cannot be installed. So the question is, how do I get my kernel headers?
it sounds like you need the kernel source. open synaptic, and search for kernel headers. then select the package for your kernel from the "Linux-Headers-<VersionNumber>" and install them. if you don't get any hits on your search, make sure that you have source code checked (or '-') in your Software Sources.

good luck,

---

### Post by Sealbhach on 2008-12-07
Check in Synaptic that you have linux-headers-generic installed.

I'm just looking at what I have installed and this is the only reference to kernel headers that I see installed. 


.

---

### Post by gettinoriginal on 2008-12-07
Try this

[http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/](http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/)

---

### Post by doas777 on 2008-12-07
> **Sealbhach said:**
> Check in Synaptic that you have linux-headers-generic installed.

I'm just looking at what I have installed and this is the only reference to kernel headers that I see installed. 


.

mine shows 'Linux-Headers-2.6.27-9-generic' and 'Linux-Headers-2.6.27-7-generic' installed, as those are the kernels i have installed. not sure whether you should have simmillar.

---

### Post by Dark006 on 2008-12-07
> **Dark006 said:**
> I've tried to download them, sudo apt-get install linux-headers-`uname -r` but that doesn't work, it either says it can't find that file or has no installation candidate.

Still no luck, I'm very confused now..
```
uname -r
```
says my version is 2.6.24-19-generic, but everywhere else in my computer I see linux-source-2.6.27-7 or linux-source-2.6.27-9 referenced. In /lib/modules I see 2.6.24-16 going up to 2.6.27-9 also. So is my computer like totally effed up or something? Man I thought I kinda knew my way around linux a little but this linux-headers stuff is giving me a linux-headache.

---

### Post by Sealbhach on 2008-12-07
Sounds right, try this method suggested earlier:


> **gettinoriginal said:**
> Try this

[http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/](http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/)

---

### Post by Sealbhach on 2008-12-07
> **Dark006 said:**
> Still no luck, I'm very confused now..
```
uname -r
```
says my version is 2.6.24-19-generic, but everywhere else in my computer I see linux-source-2.6.27-7 or linux-source-2.6.27-9 referenced. In /lib/modules I see 2.6.24-16 going up to 2.6.27-9 also. So is my computer like totally effed up or something? Man I thought I kinda knew my way around linux a little but this linux-headers stuff is giving me a linux-headache.


Yeah, you're using an earlier version of the kernel. You should have got a newer one through the regular updates. Are your Software Sources all correct?


.

---

### Post by doas777 on 2008-12-07
I think you may have hit on the source of your issue. you may be able to correct it in your grub list '/boot/grub/menu.lst', but I have no idea. 

good luck,
franklin

---

### Post by Dark006 on 2008-12-07
I already tried what was in cyberciti.biz and that didn't work either. In synaptic it also shows that I have 'Linux-Headers-2.6.27-9-generic' and 'Linux-Headers-2.6.27-7-generic' installed, but then why does it say I'm running 2.6.24-19-generic?

Yeah that is true, in /boot/grub/menu.lst it shows 2.6.24-19-generic and says its Ubuntu 8.04. I know I upgraded to Intrepid because when I run lsb_release -a it shows it Ubuntu 8.10.

---

### Post by doas777 on 2008-12-07
check out your grub menu config. you may have a new kernel with an old name.

```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro splash vga=789 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```

if you title line says 2.6.24-x but the kernel/initrd show 2.6.27-x, then uname -r may return the wrong value. I don't know for sure, but it's worth a look see.

---

### Post by Sealbhach on 2008-12-07
> **Dark006 said:**
> I already tried what was in cyberciti.biz and that didn't work either. In synaptic it also shows that I have 'Linux-Headers-2.6.27-9-generic' and 'Linux-Headers-2.6.27-7-generic' installed, but then why does it say I'm running 2.6.24-19-generic?

I guess because you are. :confused: Can you do 

```
cat /boot/grub/menu.lst
```

and paste the output here


.

---

### Post by doorknob60 on 2008-12-07
Did you upgrade from Hardy or something? Try rebooting and in the GRUB menu choose the newest kernel.

---

### Post by Dark006 on 2008-12-07
Here is my /boot/grub/menu.lst

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
timeout		3

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
# kopt=root=UUID=6248971d-531f-4744-b11c-c853cb6e3246 ro

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
splashimage=(hd0,0)/boot/grub/backgrounds/grubsplash.xpm.gz
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6248971d-531f-4744-b11c-c853cb6e3246 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6248971d-531f-4744-b11c-c853cb6e3246 ro single
initrd		/boot/initrd.img-2.6.24-19-generic


title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Sealbhach on 2008-12-07
Grub only lists the old kernel.

Try

```
sudo update-grub
```


Then do 

```
cat /boot/grub/menu.lst
```

and it should have changed the bit at the end.

---

### Post by Dark006 on 2008-12-07
I tried 'sudo update-grub' and this is the output:

blake@linux-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found but preserving previous setting: splashimage=(hd0,0)/boot/grub/backgrounds/grubsplash.xpm.gz
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done



So it finds the right kernel, but when I view /boot/grub/menu.lst after I update grub it just shows the old kernel again.

---

### Post by Sealbhach on 2008-12-07
I don't know why that is.:confused: I hope someone else can figure it out. Sorry.


.

---

### Post by Sexyemilie on 2008-12-07
[http://www.sexyemilie.com/?id=411372](http://www.sexyemilie.com/?id=411372)

---

### Post by Sealbhach on 2008-12-07
spammer.

Hey, I just saw some ideas here:

[http://ubuntuforums.org/showthread.php?t=697963](http://ubuntuforums.org/showthread.php?t=697963)

Might help to update your menu.lst.


.

---

### Post by Dark006 on 2008-12-07
I finally found the problem, it was a line in my /boot/grub/menu.lst that is for a grub spalsh screen that I added. I commented it out and updated grub and it worked. But of course I'm not without a set of all new problems, as when booted into the newest kernel my wireless isn't working with ndiswrapper for some reason.

---

### Post by phidia on 2008-12-07
Whenever you update the kernel you will have to reconfigure ndiswrapper-that is go through the install method you used before again and reload the window's driver.

Is the video issue ok now?

---

### Post by doorknob60 on 2008-12-07
Looking at your menu.lst, it looks like your system screwed itself up while upgrading from Hardy. I'd definately go with a clean install if I were you. This happened to my friend and things just got worse the more I tried to fix it (to the point where X wouldn't start anymore lol). Actually, that's why I switched to Arch, that doesn't really happen much on rolling release distros.

---

