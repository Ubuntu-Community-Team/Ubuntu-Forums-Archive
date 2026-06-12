---
title: "Removing old kernals from boot list...problem."
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Norm24 on 2009-04-26
I know how to do it but I've run into a snag.I've removed the old kernals through synaptic but they are still listed in Grub and in Startup Manager.

When I do this:
```
sudo gedit /boot/grub/menu.lst
```

Only the most recent kernal is listed(along with Vista installation) and I can't edit the old kernals out of the list.

This isn't affecting anything other than I have a large boot list.

---

### Post by drs305 on 2009-04-26
Please use "gksudo" instead of "sudo" if opening graphical applications. [_http://www.psychocats.net/ubuntu/graphicalsudo_]("http://www.psychocats.net/ubuntu/graphicalsudo")

I don't understand what you mean when you say you "can't" edit the old ones out. Do you not see them? Can you not save the file after removing them? 

**Added:** It could be that you have several menu.lst files and are not opening the correct one. One way to check is to change the title of your first menu item and reboot and check whether the change was made to the menu you see on boot. If you don't, you aren't editing the correct menu.lst.

If you post your menu.lst we can probably sort things out.

---

### Post by Norm24 on 2009-04-26
> **drs305 said:**
> Please use "gksudo" instead of "sudo" if opening graphical applications. [_http://www.psychocats.net/ubuntu/graphicalsudo_]("http://www.psychocats.net/ubuntu/graphicalsudo")

I don't understand what you mean when you say you "can't" edit the old ones out. Do you not see them? Can you not save the file after removing them? 

**Added:** It could be that you have several menu.lst files and are not opening the correct one. One way to check is to change the title of your first menu item and reboot and check whether the change was made to the menu you see on boot. If you don't, you aren't editing the correct menu.lst.

If you post your menu.lst we can probably sort things out.

I can only find one menu.lst file.This is the output:

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
# kopt=root=UUID=b16043a1-7de8-472f-8a48-0ff3d00c258e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b16043a1-7de8-472f-8a48-0ff3d00c258e

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
uuid		b16043a1-7de8-472f-8a48-0ff3d00c258e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b16043a1-7de8-472f-8a48-0ff3d00c258e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b16043a1-7de8-472f-8a48-0ff3d00c258e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b16043a1-7de8-472f-8a48-0ff3d00c258e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Chainload into GRUB 2
root		b16043a1-7de8-472f-8a48-0ff3d00c258e
kernel		/boot/grub/core.img

title		Ubuntu 9.04, memtest86+
uuid		b16043a1-7de8-472f-8a48-0ff3d00c258e
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

---

### Post by drs305 on 2009-04-26
I suspect the Grub2 is what is causing the multiple kernel displays. Are you using this option? I do not have much knowledge about Grub2 but if you don't either and aren't using it for a specific reason you probably don't need it. Do you use only 2.6.28-11 generic and Windows Vista? It looks they are covered by your standard entries.

If so, comment out the entire section.
> 
#title		Chainload into GRUB 2
#root		b16043a1-7de8-472f-8a48-0ff3d00c258e
#kernel		/boot/grub/core.img

Once you are sure you have the menu options you want you can delete this section.

---

### Post by Norm24 on 2009-04-26
> **drs305 said:**
> I suspect the "chainload" into Grub2 is what is causing the multiple kernel displays. Are you using this option? I do not have much knowledge about Grub2 but if you don't either and aren't using it for a specific reason you probably don't need it. Do you use only 2.6.28-11 generic and Windows Vista? It looks they are covered by your standard entries.

If so, comment out the entire section.

Once you are sure you have the menu options you want you can delete this section.

I am only using the latest Kernal and rarely Vista.

Before I do anything I would like to also add I ugraded to Grub2 when still using Intrepid.I had the same issue and never really bothered with it hoping that it would resolve itself in Jaunty.I don't know if any of this would make a difference in using the code you supplied me.

Even though the older kernals have been deleted it just bothers me that they are still listed on bootup and I don't want to screw things up when it is more just a cosmetic thing,I'm cautious by nature as I've screwed things up badly in Ubuntu in the past.

---

### Post by drs305 on 2009-04-26
I understand your concerns. ;-)

When you start the system, are you manually selecting the first option? If so, it is safe to comment out the GRUB2 section.

If it is automatic, it is defaulting to "0", which is also the first item. It would be safe in this case as well.

From your menu.lst, the only problem you should have in commenting out the GRUB2 reference would be if you are manually selecting that item during start or you automatically boot without selecting anything and have "default 2" in your menu.lst, which you don't.

So comment GRUB2 out, reboot...  and cross your fingers. 
Sorry, I couldn't resist the last part. You will be fine. ;-)

---

### Post by Norm24 on 2009-04-26
I commented out the "Chainload into Grub2" reference and rebooted with no issues.But the issue of the older kernals being listed is still there.

Oh well.No big deal,like I said its purely cosmetic and Jaunty is working perfectly fine in every other aspect.

---

