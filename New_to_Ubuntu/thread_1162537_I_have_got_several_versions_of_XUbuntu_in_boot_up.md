---
title: "I have got several versions of XUbuntu in boot up"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by jmarkybb on 2009-05-17
I have got several versions of XUbuntu in boot up


How do I uninstall the versions I don't use?


[[IMG]http://www.picamatic.com/show/2009/05/18/04/33/3674738_bigthumb.jpg[/IMG]](http://www.picamatic.com/view/3674738_IMG00033-20090517-1428/)

[[IMG]http://www.picamatic.com/show/2009/05/18/04/33/3674739_bigthumb.jpg[/IMG]](http://www.picamatic.com/view/3674739_IMG00034-20090517-1502/)


This happened because I did not install it correctly, so I tried to uninstall in Windows, I did and it did disappear in windows, but every time I rebooted, those were the options that were given to me.

---

### Post by cybergalvez on 2009-05-17
Not sure what you mean, in your grub menu, there are two ubuntu's, normal and recover, the third is a memeory test and then you have two vista loaders
In your windows boot loadter you have two ubuntu's but I don't know how to edit the new windows boot loader, in XP you could edit boot.ini, don't know it its the same in vista.  

So at least grub is not showing multiple installs, you will have to look at your windows boot.ini file (or what ever it is in vista) to see what it is seeing

---

### Post by Dr.Vista on 2009-05-17
Did you install it by using the method "Install inside of Windows?"

---

### Post by jmarkybb on 2009-05-18
I installed Xubuntu from CD, I installed Wubi Ubuntu 6 months ago inside windows, I deleted Wubi before installing Xubuntu

---

### Post by Wiebelhaus on 2009-05-18
```
Sudo nautilus
```

(or thunar if your using XFCE)

Surf to /boot/grub/menu.lst

Right click to edit with your text editor your menu.lst

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/memtest86+.bin
quiet

This is proper , sometimes with a kernel update the entries will be doubled like this:

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


title		Ubuntu 9.04, memtest86+
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/memtest86+.bin
quiet

They all are pointing to the same place so removing the ones you don't want will not damage anything as long as you leave atleast:

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4b41187d-ee0d-4220-995a-288da33d6636 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


title		Ubuntu 9.04, memtest86+
uuid		4b41187d-ee0d-4220-995a-288da33d6636
kernel		/boot/memtest86+.bin
quiet



One set of the default entries.

Cheers!

You can also edit right from the grub menu but this is easier.

---

