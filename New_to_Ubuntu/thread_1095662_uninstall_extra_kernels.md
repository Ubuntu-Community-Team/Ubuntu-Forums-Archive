---
title: "uninstall extra kernels"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-03-14
I use 2.6.27-7 (8.10 install CD). It upgraded to 2.6.27-13, which doesn't load properly. I want to delete the newer kernel. The problem is I don't understand how to delete one without deleting the other...

Please help me.

---

### Post by 73ckn797 on 2009-03-14
> **chilimac02 said:**
> I use 2.6.27-7 (8.10 install CD). It upgraded to 2.6.27-13, which doesn't load properly. I want to delete the newer kernel. The problem is I don't understand how to delete one without deleting the other...

Please help me.


Is the older kernel still listed in the boot selection menu? If so, you can select that one on boot-up. You can also edit grub to default boot from the kernel that works.

You can also enter "#" at the first of each line of the kernel that is giving the problem and it will not show on the boot menu.

You will have to go to Accessories/Applications/Terminal and enter:

```
gksudo gedit /boot/grub/menu.lst
```Then, at the top, change the default boot to the line listed at the end of the "menu.lst"  from "0" to whichever option for older kernel is available. Remember, "0" is the first then 1, 2 and so forth. Ignore any commented lines that begin with "#". 

It will look similar to this:

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
```The boot options look similar to this:


```
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        1e255a58-8589-4385-a5a2-9321ee72f3a5
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1e255a58-8589-4385-a5a2-9321ee72f3a5 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        1e255a58-8589-4385-a5a2-9321ee72f3a5
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1e255a58-8589-4385-a5a2-9321ee72f3a5 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        1e255a58-8589-4385-a5a2-9321ee72f3a5
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1e255a58-8589-4385-a5a2-9321ee72f3a5 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        1e255a58-8589-4385-a5a2-9321ee72f3a5
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1e255a58-8589-4385-a5a2-9321ee72f3a5 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        1e255a58-8589-4385-a5a2-9321ee72f3a5
kernel        /boot/memtest86+.bin
quiet
```You can also go to  System/Administration/Synaptic Package Manager and uninstall the latest kernel. Lower left side select "status" and select "installed" option listed at top left. Look for "linux-headers-2.6.27-13" and select that to uninstall. You will have to right click over the kernel version listed and select "uninstall".

---

### Post by chilimac02 on 2009-03-14
Ahhh, now it works... Thanks!!

---

