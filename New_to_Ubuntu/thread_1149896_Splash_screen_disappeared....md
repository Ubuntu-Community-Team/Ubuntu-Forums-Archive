---
title: "Splash screen disappeared..."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by sdim on 2009-05-05
Hi,everyone.
I've already asked about this in the past,but I can't follow what was suggested back then,since my partitions are different now,and I'm afraid I'll mess things up.
I run Mint 6 (Intrepid),and it's been two days now that while booting,the progress bar that usually appeared and was filling up as the OS was loading,doesn't appear any more.Instead,I get detailed boot info.
How can I bring back the normal boot screen with the progress bar?

(I probably clicked on an installer of another OS while trying out a live CD based on Debian...)

Many thanks.

* After running the command *ls -l /dev/disk/by-uuid*,I get:

sd@sd ~/Desktop $ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-05-06 01:37 020ba898-36c0-4e6d-bd10-8a1c1fa641e0 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-05-06 01:37 2CC81C82C81C4C88 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-05-06 01:37 d5953332-81e3-43b7-b408-7ae195587816 -> ../../sda1
sd@sd ~/Desktop $

Also,after running the command *sudo gedit /boot/grub/menu.lst*,I get this:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by tjwoosta on 2009-05-05
hmm..  try this

find this part

```

title Linux Mint 6, kernel 2.6.27-7-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

```

change it to look like this

```

title Linux Mint 6, kernel 2.6.27-7-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash=silent
initrd /boot/initrd.img-2.6.27-7-generic
quiet

```

if that doesnt work you may need to reinstall usplash and/or the mint usplash theme

on the other hand if it did work then it probably means there is a more serious problem somewhere (usually if the splash stops showing up its because there is an error somewhere in the boot messages and it wants you to see it, but specifying splash=silent will make it ignore the error)

---

### Post by sdim on 2009-05-06
Thanks for the answer.
I took a look back at the solution that was suggested when I had the same issue.Things looked the same,so,I followed that one,and it worked like a dream.Here it is:
I typed :
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
sudo blkid -c /dev/null
cat /etc/fstab
```

(sda5 is the swap partition)
and I rebooted,and the splash screen came back on.

---

### Post by tjwoosta on 2009-05-06
so there was an issue with your swap partition?

could you elaborate a bit more about what happened to cause this and how the solution was found?  (just out of curiousity)

---

### Post by sdim on 2009-05-08
I must have probably pressed the Install button while checking out another Linux distro on a live CD (just to see how the installation was mapped out).What probably happened is that the installation process started with the grub settings...Now I know better...

---

### Post by Don1500 on 2009-05-17
Change this:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
``` 

to this:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
```

This shouold get your splash screen back, but it might not be centered.

---

### Post by tjwoosta on 2009-05-17
> **Don1500 said:**
> Change this:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
``` 

to this:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
```

This shouold get your splash screen back, but it might not be centered.

Two problems with this

1. He already fixed the problem

2. That line is commented out (#)
It does nothing unless you remove the # infront of it


Also vga=791 is only if you want the splash with 1024x768 resolution in 16bit color

Here is a table that shows the different framebuffer vga modes

```

Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795

```

---

### Post by Don1500 on 2009-05-18
> 

2. That line is commented out (#)
It does nothing unless you remove the # infront of it


Not Quite
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs 
```

In this section of menu.lst the items need double "##" to be commented out.
And I knew it was for 1024 X 768, that was just a size that would work on most monitors. (Mine, for instance will not work at the default of 640X480 or at 800X600, but it does work at 791.

---

### Post by tjwoosta on 2009-05-18
lol, ok your right, my bad sorry.

:-#

---

### Post by Don1500 on 2009-05-18
More on this little problem can be found at:

[http://ubuntuforums.org/showthread.php?t=1162588](http://ubuntuforums.org/showthread.php?t=1162588)

I had more problems then just my grub resolution.
When I answered the original I was thinking sdim had the same problem as I did. (Or - DO - since I haven't been home to fix it yet.)

Thanks to Legace and tjwoosta, maybe I'll get this sorted out yet.

---

