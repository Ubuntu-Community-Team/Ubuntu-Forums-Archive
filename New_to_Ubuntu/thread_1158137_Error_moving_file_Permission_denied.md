---
title: "Error moving file: Permission denied"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by holeman14 on 2009-05-13
Ok...So, I am trying to change my lock screen look. I downloaded the file and extracted it to find this file.... lock-dialog-default.glade.

I have to replace that file with the current on which is the same name in this directory: 
**/usr/share/gnome-screensaver/.**


I try to copy and paste and overwrite everything when it tells me I do not have permission to do this????...I am the only user on the computer with all of the rights...what is the problem? How do I fix this??

Thanks!

---

### Post by TeoBigusGeekus on 2009-05-13
Linux does not allow to change anything other than your home folder just like that. You have to have root permissions to do it.
```
gksudo nautilus
```
Give your password and do your thing.

---

### Post by lazyart on 2009-05-13
No, you don't have all the rights.  SUDO does.  Do this from the source directory:```
sudo cp -f ./lock-dialog-default.glade /usr/share/gnome-screensaver
```

---

### Post by holeman14 on 2009-05-13
Thanks guys. It worked.

---

