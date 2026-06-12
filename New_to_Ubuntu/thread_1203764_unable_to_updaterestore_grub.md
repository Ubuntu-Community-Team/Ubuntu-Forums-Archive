---
title: "unable to update/restore grub"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by pranayama on 2009-07-03
I have upgraded to 9.04 and I've been using KGRUBEditor (in Gnome), but reset it to defaults.

sudo update-grub gives:

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

The kernel options listed in /boot/grub/menu.lst are:
```

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro quiet splash 
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro  single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro quiet splash 
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro quiet splash 
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=188271b9-4a75-4a9e-bb59-dc17089f1c5f ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            188271b9-4a75-4a9e-bb59-dc17089f1c5f
kernel          /boot/memtest86+.bin
quiet
```

And uname -a says I am running 2.6.27-11. If I have the latest kernel 2.6.28-13 installed I don't understand why update-grub doesn't put it in the menu. Please help.

---

### Post by TeoBigusGeekus on 2009-07-04
Updating grub will just update the grub *application*. 
You have to update your whole system for a new kernel to be used.

---

### Post by linoob13 on 2009-07-04
I found the same after updating to 9.0.4, so I just edited the **/boot/grub/menu.lst** manually (deleted the old entries and set the default choice to the first entry).

BTW - when doing this, you can also get rid of the splash screen ;)

---

### Post by pranayama on 2009-07-04
Thanks.

But before I started using KGRUBEditor, whenever there were kernel updates, then they would appear automatically in the menu. I don't understand why they don't anymore. Maybe KGRUBEditor is keeping a lockfile somewhere. If I can't find out I suppose the next thing I will try is purging KGRUBEditor from the system.

I could manually edit /boot/grub/menu.lst and add in the "/boot/vmlinuz-" stuff but I have no idea how to compute the "UUID" hashsums (are they hashsums?).

---

### Post by louieb on 2009-07-04
> **pranayama said:**
> but I have no idea how to compute the "UUID" hashsums (are they hashsums?).

just an id - should be unique. to list

```
sudo blkid -c /dev/null
```to make one
```
uuidgen
```

---

### Post by linoob13 on 2009-07-04
Why would you want to edit the hash sums??? Just delete everything you don't need/want and leave those vmlinuz... entries as they are if you want to use them.

The old entries in the grub-list vanished on my system after I installed some kernel-specific stuff (guess the system recognizes, that it can't run the old entries).

BTW - the more you are willing to mess with the system, the more you'll learn by repairing it again :P

---

### Post by pranayama on 2009-07-04
Thanks / solved.

(But I still blame this KGRUBEditor program for all my problems!)

---

