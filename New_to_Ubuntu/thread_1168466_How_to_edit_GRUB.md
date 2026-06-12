---
title: "How to edit GRUB"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-24
When I boot my machine I get a list of about 5 or 6  options in the Grub which the first 3 or 4 are all related to Ubuntu and the 5th is other Operating Systems and the the last is Windows XP.
Is there any way to make the Grub Options only two one for Ubuntu and the other for Windows XP and how do I change my default Operating System in Grub the one that appears as the first.

---

### Post by Elfy on 2009-05-24
You can edit the file so less appear or you could remove some of the older kernels. I always keep the last kernel just in case of problems. Each kernel has 2 menu entries - one normal and one recovery.

If you want to remove a kernel search in synaptic for linux-image - right click the oldest and then remove all.

To change the default find the line in menu.lst which looks like

default    0

and change the number to suit - grub counts from 0 and counts all the 'title' occurences.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

If you are unsure, paste your menu lists here and someone will help - use code tags please - [noparse]```
[/noparse] at the beginning of the pasted text and [noparse]
```[/noparse] at the end.

---

### Post by sahabcse on 2009-05-24
open the terminal

there type 

sudo vim /boot/grub/menu.lst

there you can comment out the unwanted option. 

For using vim command line editior clck [here]("http://sahabm.blogspot.com/2009/04/vi-editor-how-to.html")

---

### Post by Didius Falco on 2009-05-24
> **mosaabJ said:**
> When I boot my machine I get a list of about 5 or 6  options in the Grub which the first 3 or 4 are all related to Ubuntu and the 5th is other Operating Systems and the the last is Windows XP.
Is there any way to make the Grub Options only two one for Ubuntu and the other for Windows XP and how do I change my default Operating System in Grub the one that appears as the first.

If you take a closer look at the Grub menu, you'll see that each kernel is listed twice. The first one is the normal boot up, and the second listing is for Recovery Mode, which is what you use when there is a problem that prevents you from logging in normally.

You can remove older kernels that you do not use using Synaptic Package Manager. Some people only keep the newest kernel. Personally, I keep the latest two, just in case of a problem with the newest kernel.

To remove the old kernels, first open a Terminal shell (**Applications/Accessories/Terminal**) and type ```
uname -r
```
This will tell you the kernel that you are currently using. Write down or remember this information.

Open Synaptic Package Manager (**System/Administration/Synaptic Package** **Manager**) and search for ```
linux-image-2
```

This will bring up a list of all the kernels currently installed. Select the ones you want to remove - be sure and leave at least the one you wrote down/remembered - and choose to "remove completely".

This will not only remove the kernel files, it will also update the menu.lst file and remove them from that as well.

Alternatively, you can just open a terminal and type ```
gksu gedit /boot/grub/menu.lst
``` This will open the file that contains the listings seen on the boot up menu.

You can simply comment out the lines you don't want displayed by putting a hash (#) at the front. Here is a before and after example.

before:

```
## ## End Default Options ##

title        Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid        e47525af-4710-4faa-bc80-fbad1ec6d109
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash 
initrd        /boot/initrd.img-2.6.30-5-generic
quiet
```

After:

```
## ## End Default Options ##

#title        Ubuntu karmic (development branch), kernel 2.6.30-5-generic
#uuid        e47525af-4710-4faa-bc80-fbad1ec6d109
#kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash 
#initrd        /boot/initrd.img-2.6.30-5-generic
#quiet
```

Doing that will stop it from being displayed, but the kernel files are still on my system.

To choose the default start-up option, you can change the number in this section of the menu.lst file:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```

Change the number to the number of the entry you want to boot up first. As noted in the file, numbering starts at 0. Yes, they do this just to mess with our heads. <G>

I hope this helps...

Regards,

Didius

---

### Post by mosaabJ on 2009-05-24
To be on the safe this is My Main.lst I only want to keep Windows XP as the default with Ubuntu and only two options.
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
# kopt=root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9670217-fd70-4137-ae11-dc27e937a4aa

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
uuid		f9670217-fd70-4137-ae11-dc27e937a4aa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f9670217-fd70-4137-ae11-dc27e937a4aa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f9670217-fd70-4137-ae11-dc27e937a4aa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by CylnZ on 2009-05-24
Thanks, your help worked a treat. got rid of a couple rc kernels and I titled the vista recovery partition appropriately. :) Thanks again.

---

### Post by Elfy on 2009-05-25
Change this part of your menu list
```
default		0
```to

```
default		saved
```

Grub will remember which os you last booted. To edit the file - follow my last post to backup and then open the file for editing - remove this part
```

title		Ubuntu 9.04, memtest86+
uuid		f9670217-fd70-4137-ae11-dc27e937a4aa
kernel		/boot/memtest86+.bin
quiet
```

You actually only have one kernel there - one option is recovery mode.

---

### Post by mosaabJ on 2009-05-25
Thank you every one for your help. I'll try it out and post what happens.;)

---

### Post by camper365 on 2009-05-25
Here is what you should have for your new menu.lst:

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
default        1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9670217-fd70-4137-ae11-dc27e937a4aa

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f9670217-fd70-4137-ae11-dc27e937a4aa
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

# title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
# uuid        f9670217-fd70-4137-ae11-dc27e937a4aa
# kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9670217-fd70-4137-ae11-dc27e937a4aa ro  single
# initrd        /boot/initrd.img-2.6.28-11-generic

# title        Ubuntu 9.04, memtest86+
# uuid        f9670217-fd70-4137-ae11-dc27e937a4aa
# kernel        /boot/memtest86+.bin
# quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```Make sure you backup your old menu.lst with

```
sudo cp /boot/grub/menu.lst boot/grub/menu.lst.old
```

before you edit your menu.lst

---

### Post by 2048Megabytes on 2009-05-26
[SIZE="3"]Thank you for the great advice Didius Falco.  I am still new to Linux Ubuntu and the following command worked great:

gksu gedit /boot/grub/menu.lst

I was able to customize my Grub 1.5 menu to what I wanted.  I had three unwanted entries in Grub and I was able to get rid of them.[/SIZE]

---

### Post by Didius Falco on 2009-05-26
Happy to help. I should have told you (as several others did) to make a backup of the file first. That's a very good habit to develop, particularly when dealing with system files.

Regards,

Didius

---

### Post by Chalfont on 2009-05-28
Thanks to the posts here.

Just successfully edited the Grub menu to default boot up in XP unless I have chosen Ubuntu (it's the work PC and has to run XP normally). 

Thanks :p

---

