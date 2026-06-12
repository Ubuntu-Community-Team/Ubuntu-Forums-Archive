---
title: "GRUB Error 13 - help!"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-02-11
I've tried to find some info on this, but everyone I come across who has received this error has been using 2 hard disks. I've come up against this error on a laptop with just one hard drive. It's a dual-boot system with Intrepid and XP.

Here is the relevant portion of the menu.lst:
```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d91e1c21-0d6b-4f14-bf01-96c979931c88
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d91e1c21-0d6b-4f14-bf01-96c979931c88 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d91e1c21-0d6b-4f14-bf01-96c979931c88
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d91e1c21-0d6b-4f14-bf01-96c979931c88 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d91e1c21-0d6b-4f14-bf01-96c979931c88
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d91e1c21-0d6b-4f14-bf01-96c979931c88 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d91e1c21-0d6b-4f14-bf01-96c979931c88
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d91e1c21-0d6b-4f14-bf01-96c979931c88 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d91e1c21-0d6b-4f14-bf01-96c979931c88
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I'm also receiving an error when I try to boot XP - it's telling me that hal.dll is corrupt. I can't help but think these two problems are related somehow. (if not, I'll fix hal.dll later!)

Any help is very much appreciated!

---

### Post by mandeepsmagh on 2009-02-11
try to fix mbr for windows first, then u can install grub from ubuntu live cd later on.

---

