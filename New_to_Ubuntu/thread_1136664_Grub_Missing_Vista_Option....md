---
title: "Grub Missing Vista Option..."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by shoot2kill on 2009-04-25
I have just upgraded to 9.04, and the GRUB no longer shows an option to boot to vista.. below is my menu.lst.. also, i would like vista to be the default OS if this is possible..

```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1725194e-a931-4502-99dd-994e1d21723f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1725194e-a931-4502-99dd-994e1d21723f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1725194e-a931-4502-99dd-994e1d21723f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1725194e-a931-4502-99dd-994e1d21723f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
uuid		1725194e-a931-4502-99dd-994e1d21723f
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=1725194e-a931-4502-99dd-994e1d21723f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid		1725194e-a931-4502-99dd-994e1d21723f
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=1725194e-a931-4502-99dd-994e1d21723f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
uuid		1725194e-a931-4502-99dd-994e1d21723f
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by zvacet on 2009-04-25
Add this below 

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Of course you will change root (hd0,0) to partition on witch Vista is.To find that put Ubuntu live Cd in drive and type in terminal

```
sudo fdisk -l
```

you can choose your first boot OS with **startupmanager**.It is in synaptic.

---

