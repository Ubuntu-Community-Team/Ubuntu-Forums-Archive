---
title: "access ntfs usb hard drive"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2009-01-11
How do I mount an external hard drive with usb connection?

In windows I just plug it in.  In ubuntu, I plug it in and nothing happens.

I tried googling around a bit and tried lsusb, and can see it there, I just don't know what to do next?

---

### Post by insane_alien on 2009-01-11
it should just mount, or at least it always has for me.

check ntfs-3g is installed.

either go to synaptic and check there is a little green box next to the package 'ntfs-3g' 

or go to the terminal and type 'sudo aptitude install ntfs-3g' without the quotes obviously.

---

