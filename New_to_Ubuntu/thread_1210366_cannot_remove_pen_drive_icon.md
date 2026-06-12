---
title: "cannot remove pen drive icon"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by davedarkstar on 2009-07-11
hi all,im new to ubuntu as of today.heres my problem,when i place a pen/flash drive into usb the icon comes on to the desktop ok and every things fine but when i remove it the icon remains and icannot deleat it to the recycle bin,i now have 3 icons for the same flash drive on the desk top which i cannot remove,dose anyone no how to remove them and thanks in advance..regards   dave jones.     ):P

---

### Post by adit on 2009-07-11
Your pen drives are mounted on /media directory.
Type
```
$ cd /media
$ ls
```You will get a list of devices mounted.  Then type:
$ sudo umount <name-of-device>
*(without <> characters)*.
The icons in the Desktop will be cleared.

---

### Post by the.phantom on 2009-07-11
are you right clicking on the icon and selecting UNmount when you want to remove it?
Ubuntu can detect it and mount it but you need to UNmount it before you unplug it

---

### Post by LewRockwell on 2009-07-11
> **davedarkstar said:**
> hi all,im new to ubuntu as of today.heres my problem,when i place a pen/flash drive into usb the icon comes on to the desktop ok and every things fine but when i remove it the icon remains and icannot deleat it to the recycle bin,i now have 3 icons for the same flash drive on the desk top which i cannot remove,dose anyone no how to remove them and thanks in advance..regards   dave jones.     ):P

it is customary to unmount media before removing it

typically this is done with a right-click and the unmount selection

.

---

### Post by colau on 2009-08-16
> **davedarkstar said:**
> hi all,im new to ubuntu as of today.heres my problem,when i place a pen/flash drive into usb the icon comes on to the desktop ok and every things fine but when i remove it the icon remains and icannot deleat it to the recycle bin,i now have 3 icons for the same flash drive on the desk top which i cannot remove,dose anyone no how to remove them and thanks in advance..regards   dave jones.     ):P
You can unmount the pendrive right clicking the icon.
Or
```

sudo umount /media/<pendrivename>

```
It's better to umount before you unplug.

---

