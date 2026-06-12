---
title: "Issue getting selection bar to show up in Grub when Dual-booting"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Binary.tobis on 2009-07-29
I recently set my computer to dual-boot Windows XP and Ubuntu Linux. For some reason, the boot-up menu is glitched out so that the only way to tell which boot-up option I am choosing is that it has a black bar behind it. Ideally I would want the selected choice to have a light grey box behind it with black text, and the other items to have nothing behind them and white text. I chose a background which is mostly black, so I can't see which one I am choosing.

I downloaded KGRUBEditor and StartUp-Manager and tried using both of them to change the colors in the menu, but they didn't have any effect. I changed the text color and the box color, then saved and rebooted to check. Here's my /boot/grub/menu.lst file:

```
splashimage /boot/grub/splashimages/Portal.xpm.gz
default 0
timeout 10
color white/black blink-black/light-gray

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
# kopt=root=UUID=b5747fc7-a5d7-433d-a83e-0f99840c7292 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=b5747fc7-a5d7-433d-a83e-0f99840c7292

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
# defoptions=quiet splash vga=794

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=b5747fc7-a5d7-433d-a83e-0f99840c7292 ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=b5747fc7-a5d7-433d-a83e-0f99840c7292 ro xforcevesa  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I had to manually change the order of the list on the bottom of this file, but I don't think that would effect the menu colors, hopefully. :( Thanks in advance for any responses!

---

### Post by Binary.tobis on 2009-07-29
Any help is appreciated, I will have to look at this screen every time I boot my computer. :(

---

### Post by Binary.tobis on 2009-08-05
One last bump before I give up on it. :(

---

