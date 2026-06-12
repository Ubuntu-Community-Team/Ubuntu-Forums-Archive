---
title: "Can't select MS in grub"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Sheedy on 2010-08-19
Im unable to select MS XP in the grub screen. The arrow keys will not move. Did try to start up MS in safe mode which caused said prob. have I disturbed something in the BIOS screen? Have no discs at present location & I'm a noob, a mate set up my drive years ago.

Any suggestions?

---

### Post by jtarin on 2010-08-19
Try from a terminal```
sudo update-grub
```Note any error messages and post. Reboot to see changes.

---

### Post by Sheedy on 2010-08-19
Tried the sudo update-grub command & still no option to select any OS in grub screen. This is what I got after update command.
So does this show it not recognising MS ?


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by jtarin on 2010-08-19
> **Sheedy said:**
> Tried the sudo update-grub command & still no option to select any OS in grub screen. This is what I got after update command.
So does this show it not recognising MS ?


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done
Run the command ```
cat /boot/grub/menu.lst
```and post those results.

---

### Post by Sheedy on 2010-08-19
Here's what that command shows us.

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
## This includes the seperator line!!
default    10

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

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
# kopt=root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
# savedefault=tfalse

## ## End Default Options ##

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-25-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-25-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-25-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-25-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-22-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-22-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-21-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-21-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root        (hd0,7)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro quiet splash
initrd        /initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,7)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=dc8ba96e-5796-4d7a-ac3e-ccd289a8a841 ro single
initrd        /initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,7)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microshaft Windows XP Professional
root        (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by jtarin on 2010-08-20
You have more kernel entries than you need. Iwould keep two of the latest and remove the rest if you don't need them. Uninstall old kernals using the Symnaptic Package Manager. Menu: System>Administration>Synaptic Package Manager. Enter your pass word.

In the search box enter:

```
linux-image
```

You should then see all the kernals installed. Right click the ones you want to remove and select > Mark for removal. When you have all marked click Apply.

After Synaptic is done (this will take awhile depending on how many images you are removing) close it.

Open a Terminal and type:


```
sudo update-grub
```

Enter your password:

IF you have done everything correctly, you should get a screen that looks similar to this:



```
john@john-desktop:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdc5
done
```

Reboot.

Post that screen here and let's see if the XP entry shows.

---

### Post by jtarin on 2010-08-20
[Changing Default OS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

