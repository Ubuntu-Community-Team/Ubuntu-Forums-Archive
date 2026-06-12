---
title: "gfxboot... has anyone been able to make it work in Ubuntu?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by the8thstar on 2009-02-14
I installed gfxboot to try and get a nicer bootsplash with Grub (not usplash). Here is the modification I made in /boot/grub/menu.lst :
> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
**gfxmenu (hd0,3)/boot/grub/message.ubugrey**
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
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=36546e11-28e5-479d-aec4-7650ff14f9e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=36546e11-28e5-479d-aec4-7650ff14f9e5

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
# defoptions=quiet splash vga=866

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

title		Ubuntu 8.10
uuid		36546e11-28e5-479d-aec4-7650ff14f9e5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36546e11-28e5-479d-aec4-7650ff14f9e5 ro quiet splash vga=866
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10 (Recovery Mode)
uuid		36546e11-28e5-479d-aec4-7650ff14f9e5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36546e11-28e5-479d-aec4-7650ff14f9e5 ro  single vga=866
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10 (Memory Test)
uuid		36546e11-28e5-479d-aec4-7650ff14f9e5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows 7 Ultimate (Beta)
root		(hd0,1)
makeactive
chainloader	+1

(hd0,3) is where my / partition resides
/boot/grub is where I put the background image "message.ubugrey"

but nothing changed. Any ideas why?

---

### Post by the8thstar on 2009-02-14
Bump

---

### Post by UbNewbie on 2009-02-18
Hi there,

For the gfxboot fancy things you need to install grub-gfxboot package.
Don't know which version are you using.
YOU need to deinstall grub first of course.

I have used grub-gfxboot_0.97-40_i386.deb for Intrepid and you need also  to install grub-common. Otherwise it won't work.
BUT you can use any message.* that you can find on Internet. It seems that there is a change in file format so you need to compile a new one by yourself.

What i have done:

install gfxboot-theme-zen package from synaptic...

cd /usr/share/gfxboot-theme-zen/
sudo make
sudo make install
cd install
sudo su
ls . |cpio -o > /boot/grub/message.zen

And use that file for in your menu.lst. And Voila it works...

---

### Post by Metallion on 2009-02-18
I've made it work several times in ubuntu. This guide has been my best friend in the process => [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by UbNewbie on 2009-02-18
> **Metallion said:**
> I've made it work several times in ubuntu. This guide has been my best friend in the process => [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

Hi Metallion,

It's now working also on my Intrepid but the problem is now how to customize the theme.
I can't find any good document how to customize that.

Regards,

H2T

---

### Post by Metallion on 2009-02-19
> **UbNewbie said:**
> Hi Metallion,

It's now working also on my Intrepid but the problem is now how to customize the theme.
I can't find any good document how to customize that.

Regards,

H2T

By customizing you mean making your own message.* right? Unfortunately I have never tried it so I don't know any guides for that. In case you mean simply changing the picture then you can just repeat the guide with another message.*

---

### Post by the8thstar on 2009-02-28
Alright, thanks to you all!

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111192[/ATTACH]

Hope this helps

---

