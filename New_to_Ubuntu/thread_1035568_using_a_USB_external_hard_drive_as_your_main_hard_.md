---
title: "using a USB external hard drive as your main hard drive"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2009-01-09
well i posted this earlier but it never came up so i was curious as i have said before i am building a computer that is in an old xbox case and now all i have to do is put in a hard drive

well the space i have left is super limited so i figured the easiest way to go would be to use a USB external hardrive so i was wondering if it would be possible to load an OS system on that hardrive then have the computer boot from that device everytime

---

### Post by Michaelg14 on 2009-01-09
I would think that you could.  Ubuntu can boot a live CD from a usb flash and save updates it should be able to handle a usb hard drive.  Nothing like trying it to find out, let us know if it works.

---

### Post by johnsonfarms on 2009-01-09
When you install Ubuntu make sure you tell it to install grub to the drive in the computer. That is, if the drive in your computer is /dev/sda and the external is /dev/sdb make sure gruyb is installed to /dev/sda (or (hd0 i think). I believe this makes it so the boot loader on the main drive will start, but the drive you installed to will still be the boot option for the OS. If not you can always edit /boot/grub/menu.lst to include the proper drive for booting.

> title		Ubuntu jaunty (development branch), kernel 2.6.27-4-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=97eb2526-05c1-4ecb-8ff6-694465c88c41 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=97eb2526-05c1-4ecb-8ff6-694465c88c41 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu jaunty (development branch), memtest86+
root		(hd0,1)
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


So here is a portion of my menu.lst, if Windows in this case was on an external drive I would simply make the listing under root match the appropriate drive i.e. (hd1,0) for example.

Hopefully I am not steering you too far off track with this, good luck.

---

