---
title: "So many boot choices!"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by skootar on 2009-02-08
I have 15 different ubuntu options on the boot screen. How do I pick the right one? I know I don't want recovery. Can I edit down the list to just 2? Normal, and recovery?

---

### Post by taurus on 2009-02-08
Usually, you want to use the latest kernel and yes, you can edit to include only the ones that you want.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And place a # in front of the lines to comment them out.

---

### Post by konqueror7 on 2009-02-08
you can just select the latest (top) ubuntu, you just probably updated you system...

you can edit you grub thru...
```
sudo gedit /boot/grub/menu.lst
```

you can then comment out those you don't want to display anay more by adding '#' in front of them...

or to be much easier, you can download *StartUp Manager* from the add/remove menu,,,it helps you manage you booting settings and stuffs...

---

### Post by sam_delta on 2009-02-08
if you prefer a graphical way, install startupmanager, to manage your boot menu, and select only to keep the last 2 kernels

sam

---

