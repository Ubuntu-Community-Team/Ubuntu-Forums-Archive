---
title: "Editing the menu.lst?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by xreaper on 2009-05-10
Hey everyone, me again. This time, I was playing around with g-parted, and for some reason beyond my logic, I could not resize my 9.2gb ext4 partion to anything higher than what it originally was. (Even though my hard drive has an extra 30gb spare.) Now, I've created a second ext4 partion and copied the original files on my 9.2gb partion, and I was wondering if it is possible to edit my menu.lst to boot the new 30gb partion rather than my old 9.2 one? Or even to delete the 30gb partion and just resize my 9.2gb partion?

sudo fdisk -lu:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+   7  HPFS/NTFS
/dev/sdb2           18238       19457     9799650   83  Linux
/dev/sdb3           13055       18237    41632447+   5  Extended
/dev/sdb5           13055       14270     9767488+  82  Linux swap / Solaris
/dev/sdb6           14271       18237    31864896   83  Linux

```Menu.lst is as follows:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /vmlinuz-2.6.28-11-generic root=UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c ro splash vga=795 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /vmlinuz-2.6.28-11-generic root=UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /memtest86+.bin
quiet

title        Other operating systems:
root

title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by pastalavista on 2009-05-10
You can't edit a mounted partition. You need to boot from a LiveCD, either the Ubuntu installer or another bootable disk. Look into a Gparted disk or try a Super Grub Disk. You say you copied the entire '/' partition to another partition? I don't knw. It may or may not be possible to boot from it but you'd have to setup grub all over again after you did it. The MBR (master boot record) will usually be in the first primary drive but it doesn't show as the boot drive in your fdisk output. Is that all of it? What happened to sda?

---

### Post by xreaper on 2009-05-10
I was using the live cd when I was trying to resize the partition, how would I go about getting info for my first hdd? (the one with all the boot files)

---

### Post by xreaper on 2009-05-10
Nevermind, I sorted my own problem, was an issue with an extended partion, but everything is sweet now :D

---

### Post by pastalavista on 2009-05-10
> how would I go about getting info for my first hdd? (the one with all the boot files) I wouldn't know. You never mentioned it. It should have shown up when you ran fdisk. To unmount a drive in gparted, right-click on it and select unmount.

---

