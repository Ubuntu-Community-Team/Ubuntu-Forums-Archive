---
title: "Weird problem with USplash."
date: 2009-04-29
forum: New to Ubuntu
---

### Post by ugriffin on 2009-04-29
Hey. Usually, kubuntu 9.04 installation, while displaying the splash screen, on the first part (when it goes forward and back), just went forward and then proceeded to the second part where the entire bar filled up. However, today, I went on and attempted to do the impossible task of triple booting, by installing XP on an extended partition (gah!). Although I knew my Kubuntu partition would be spared, and maybe my Vista one might get hacked (something I didn't mind too much), I proceeded, and after a few hardware crashes (computer just lost power even with a battery), I finished my XP installation, which didn't work, so I reinstalled GRUB and proceeded to cleaning this mess from Kubuntu. My Vista partition was beyond repair (I'm currently backing up everything), and, queerly enough, my Kubuntu installation was slightly affected. Now, at the splash screen, in the first part, it goes forward and then back one time, and then, proceeds to doing the second part in text mode, something which reminds me of Windows 95/98.

Is there a way to fix this? I really don't want to reinstall Kubuntu as well, and I don't think reinstalling usplash will work in any case.

EDIT: Will installing a separate splash screen package (such as splashy) fix this? Are there identical 9.04 or 8.10 (I never liked the Jaunty boot screen) for such a program? Thanks in advance.

---

### Post by picopir8 on 2009-04-29
Edit /boot/grub/menu.lst and make sure "quiet" and "splash" are specified as defoptions.

---

### Post by ugriffin on 2009-04-29
Is this in the Kubuntu boot entry? Where the OS boot information is located? If so, it is already set to "ro quiet splash". Or is it somewhere else?

EDIT: My menu.list

> 
hiddenmenu
default 0
timeout 2

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
# kopt=root=UUID=b0ca35c0-0170-44c6-865c-74067615112b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b0ca35c0-0170-44c6-865c-74067615112b

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

title Kubuntu 9.04
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=b0ca35c0-0170-44c6-865c-74067615112b ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=b0ca35c0-0170-44c6-865c-74067615112b ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=b0ca35c0-0170-44c6-865c-74067615112b ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=b0ca35c0-0170-44c6-865c-74067615112b ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows Vista
root (hd0,1)
chainloader +1
savedefault
makeactive

title Acer Recovery Utility
root (hd0,0)
chainloader +1
savedefault
makeactive




---

### Post by ugriffin on 2009-04-30
*bump*

Any help folks?

---

