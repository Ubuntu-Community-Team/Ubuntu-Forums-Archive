---
title: "[SOLVED] memtest86 reboots computer"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Facetious Falcon on 2009-01-08
When I try and run memtest86 from Grub it just flashes a blue screen, so fast that I can't read it then restarts the computer. Not sure why this is. Anyone else had this problem?

Thanks for the help !

---

### Post by Facetious Falcon on 2009-01-08
Just to note, the contents of my /boot/grub/menu.lst file have this option in:

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

I'm hoping this should allow me to run memtest.

---

### Post by oldos2er on 2009-01-08
> **Facetious Falcon said:**
> Just to note, the contents of my /boot/grub/menu.lst file have this option in:

title        Ubuntu 8.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

I'm hoping this should allow me to run memtest.

 memtest lives in /boot of the root partition. Can you post your entire menu.lst?

---

### Post by Facetious Falcon on 2009-01-08
```
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
memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5666f9dd-6a46-4beb-aa59-672b3c2357c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5666f9dd-6a46-4beb-aa59-672b3c2357c1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5666f9dd-6a46-4beb-aa59-672b3c2357c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5666f9dd-6a46-4beb-aa59-672b3c2357c1 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		**** operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I'm fairly sure that it's pointing to the right hard disk. I think it may load up but it hits an error and restarts it does it so fast I can't see what that error is though :(

---

### Post by handydan918 on 2009-01-08
> **Facetious Falcon said:**
> When I try and run memtest86 from Grub it just flashes a blue screen, so fast that I can't read it then restarts the computer. Not sure why this is. Anyone else had this problem?

Thanks for the help !

Sounds an awful lot like a hardware issue. if you can't even run memtest...
Will the machine boot normally?

---

### Post by Facetious Falcon on 2009-01-08
There's nothing particularly wrong with the machine (i'm using it now) but I wanted to a do a memtest because every now and then I get visual artifact appearing on the screen (pink pixels appearing randomly everywhere) which eventually causes the computer to crash. I'm thinking it's more likely to be Graphics card ram than normal RAM but I'd just like to be on the safe side ;)

---

### Post by oldos2er on 2009-01-08
Yes, that looks ok. If you have a LiveCD, try running memtest from there.

---

