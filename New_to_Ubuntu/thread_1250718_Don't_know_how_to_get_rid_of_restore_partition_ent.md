---
title: "Don't know how to get rid of restore partition entry in GRUB."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by afmGM on 2009-08-26
I've just did a full install of Ubuntu (not using Wubi) and now in GRUB, I have two entries for Vista (under the same name), but one's the restore partition, and I don't want to risk not being able to stop the restore partition from screwing up my system.  

I've written down which partition the real Windows Vista is on, and the restore partition.

The restore partition is on /dev/sda1
The vista partition is on /dev/sda2
Ubuntu is on /dev/sda4

Can anyone tell me how to do that, without going and testing each one?

Thanks in advance.

---

### Post by SoftwareExplorer on 2009-08-26
Boot into ubuntu. Go to Places->Computer. Open filesystem. Open boot. Open grub. Open menu.lst. Copy it and paste it here and I'll tell you what part to take out.

---

### Post by afmGM on 2009-08-26
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
default        0

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
# kopt=root=UUID=4456fc5f-4aa8-4ce2-a831-7cac89aa2e69 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4456fc5f-4aa8-4ce2-a831-7cac89aa2e69

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
uuid        4456fc5f-4aa8-4ce2-a831-7cac89aa2e69
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4456fc5f-4aa8-4ce2-a831-7cac89aa2e69 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4456fc5f-4aa8-4ce2-a831-7cac89aa2e69
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4456fc5f-4aa8-4ce2-a831-7cac89aa2e69 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4456fc5f-4aa8-4ce2-a831-7cac89aa2e69
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by drs305 on 2009-08-26
This is your normal Vista partition entry if it is sda2:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (**[COLOR="DarkRed"]hd0,1[/COLOR]**)
savedefault
makeactive
chainloader    +1


In Grub Legacy, drive and partition counting start with 0, so the first drive is drive 0, the first partition is partition 0. The second partition is 1, etc. So the second partition on the first drive is (hd0,1).

You can edit the menu.lst with the following commands:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak # make backup
gksudo gedit /boot/grub/menu.lst  # edit menu.lst

```

You can either remove the first Vista entry, change the title to reflect that it is the restore partition, etc. You can also move the entire section (all seven lines) to put it below the normal Vista partition. The one thing you DON'T want to do is move it above your Ubuntu section, since the first entry is the default boot entry according to the grub settings (from the "default 0" line).

Here is one revision. Copy/replace the two Vista entries with these. What I have done is "comment out" the restore partition. You won't see it on the normal menu. If you need it you can remove the # symbols from the last five lines:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        *** Windows Vista Restore Partition ***
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1



Credit to SoftwareExplorer for putting you on the right track!

Tip Added: When the grub menu pops up, you can 'freeze' it by hitting ESC. Then scroll using the down arrow to the item you are about to select. Press E and you can see the actual code and confirm it's the correct partition. Press ESC to return to the menu or B to boot the selection.

---

### Post by afmGM on 2009-08-26
Thank you, I'm going to reboot to test if it works now :)

---

### Post by SoftwareExplorer on 2009-08-26
> **drs305 said:**
> 
Credit to SoftwareExplorer for putting you on the right track!
Credit to drs305 for fulfilling my promise while I was busy!

---

