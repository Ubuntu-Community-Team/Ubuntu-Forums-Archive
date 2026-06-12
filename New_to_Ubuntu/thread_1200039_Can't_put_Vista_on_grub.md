---
title: "Can't put Vista on grub"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by brunoskrebs on 2009-06-29
Hi, I have just installed windows vista on my computer then I followed this link [Recovering]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to recover grub. I followed all the steps but Vista didn't show up on grub loader.

Then I edited /boot/grub/menu.lst still following that how to. But I got the error:

error 23 cant parse something

So can anyone help me??

This is my menu.lst in this very moment

```

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		182335e4-74a1-4bea-9ad4-f225f333ff03
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=182335e4-74a1-4bea-9ad4-f225f333ff03 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		182335e4-74a1-4bea-9ad4-f225f333ff03
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=182335e4-74a1-4bea-9ad4-f225f333ff03 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		182335e4-74a1-4bea-9ad4-f225f333ff03
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=182335e4-74a1-4bea-9ad4-f225f333ff03 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		182335e4-74a1-4bea-9ad4-f225f333ff03
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=182335e4-74a1-4bea-9ad4-f225f333ff03 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		182335e4-74a1-4bea-9ad4-f225f333ff03
kernel		/boot/memtest86+.bin
quiet

title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
rootnoverify (sda1,0) # This is the location of the windows partition
makeactive
chainloader +1

```

and this is the output of fdsik -l:

> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923062+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           10200       19457    74364885    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           10200       10381     1461883+  82  Linux swap / Solaris
/dev/sda6           10382       19457    72902938+  83  Linux


Thanks in advance...

---

### Post by oldfred on 2009-06-29
I am not sure if GRUB allows the comments a the end of a line. And GRUB uses a different nomenclature for for drives. In linux sda1 is the a - the first drive and 1 - the first partition. In GRUB it starts at zero and uses hd so the first drive is hd0.
You need to change your sda1 to hd0.
These are my windows Grub lines for XP, and  I think Vista uses rootnoverify where XP can use either root or rootnoverify.
# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by swerdna on 2009-06-29
Great if that works, if not, then try this:
```
title windows vista
rootnoverify (hd0,0)
chainloader (hd0,0)+1
```

---

### Post by brunoskrebs on 2009-06-30
Ohh yeah, that was the mistake. hd0 instead of sda1.
Now I have both on my Grub
thanks people...

---

