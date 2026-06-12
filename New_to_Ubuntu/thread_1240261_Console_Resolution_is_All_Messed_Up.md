---
title: "Console Resolution is All Messed Up"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by mrgnash on 2009-08-14
Ok, so during bootup, the few lines of console output that appear are fine, but if I jump back to the console after GDM has been loaded, the resolution is out of whack, and I can't actually see the command prompt at all because it is located outside of the viewing area, while the opening text is humungous. Any idea as to how I might fix this, as it is quite troubling if X dies and I have to work with the system like this (already I had to edit xorg.conf under these conditions, and it wasn't much fun at all!).

---

### Post by zerhacke on 2009-08-14
What does it look like if you press CTRL+ALT+F2?

To get back to X you press CTRL+ALT+F7

---

### Post by mrgnash on 2009-08-14
> **zerhacke said:**
> What does it look like if you press CTRL+ALT+F2?

To get back to X you press CTRL+ALT+F7

Just as I described.

---

### Post by Shig on 2009-08-14
Could you please post your xorg.conf file, and also your grub menu.lst file?

```
/etc/X11/xorg.conf
/boot/grub/menu.lst

```This is probably because you are using the newer userspace framebuffer (which is the default in newer version of ubuntu) and your monitor/graphics card does not like switching back to VGA mode when you drop to a console session. Enabling kernel vesafb can work around this, I had to do this for my home theatre setup.

More information:
[http://forum.awkwardtv.org/viewtopic.php?f=23&t=1997](http://forum.awkwardtv.org/viewtopic.php?f=23&t=1997)

---

### Post by mrgnash on 2009-08-14
Sure thing :)

Xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
	Option "AccelMethod" "EXA"
	Option "MigrationHeuristic" "greedy"




EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

menu.lst:

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
# kopt=root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ab40f01-1528-4390-9fa9-c0124d53dc73

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5ab40f01-1528-4390-9fa9-c0124d53dc73
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Shig on 2009-08-14
OK - Thanks, to enable vesafb as a test (and hopefully fix)

Change, in your menu.lst file:

```
# defoptions=quiet splash
```
to
```
defoptions=quiet splash video=vesafb:mtrr,ypan vga=791
```

Ensure the leading # is removed
This will enable the kernel vesa framebuffer, with some optimizations, and use a 1024x768 resolution (791). The resolution can be changed by using various values, 791 is a safe value however to try.

Once you've made this edit run update-grub, and reboot.

---

### Post by mrgnash on 2009-08-14
> **Shig said:**
> OK - Thanks, to enable vesafb as a test (and hopefully fix)

Change, in your menu.lst file:

```
# defoptions=quiet splash
```
to
```
defoptions=quiet splash video=vesafb:mtrr,ypan vga=791
```

Ensure the leading # is removed
This will enable the kernel vesa framebuffer, with some optimizations, and use a 1024x768 resolution (791). The resolution can be changed by using various values, 791 is a safe value however to try.

Once you've made this edit run update-grub, and reboot.

Thankyou for that :D Unfortunately, the same problem persists, even after making the above changes :(

---

### Post by Shig on 2009-08-15
Could you please provide the output of the following:
```
cat /proc/cmdline
```

---

### Post by mrgnash on 2009-08-15
> **Shig said:**
> Could you please provide the output of the following:
```
cat /proc/cmdline
```

```
root=UUID=5ab40f01-1528-4390-9fa9-c0124d53dc73 ro quiet splash
```

... and when I checked the menu.list file, sure enough, the changes weren't there. I made the changes again, and ran update-grub, and the file reverted back to its default state again :-S

---

### Post by mrgnash on 2009-08-15
Well, I seem to have solved the issue (at least partially), but simply adding vga=791 directly to the kernel mode line in menu.list, rather than defoptions. This way, the changes I make aren't undone when I run update-grub (why, I have no idea). Also, I added vesafb to initramfs, and removed vesafb from the modprobe blacklist. The resolution is fine now, with the only remaining problem being that when I switch back to X after invoking one of the ttys the screen blanks, and stays that way indefinitely. Still, at least now I can work on the system properly in the advent of X's failure. Thanks for all your help :)

---

