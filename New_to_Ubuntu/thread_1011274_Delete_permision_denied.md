---
title: "Delete permision denied"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by nnjond on 2008-12-14
Hi, I have some directories in my wastebasket i can't delete because permission is denied. How can i solve this?

Thanks

---

### Post by taurus on 2008-12-14
Root probably owns those files.  You can run nautilus with root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Don't forget to empty trash bin in root too.

---

### Post by vandorjw on 2008-12-14
[http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

---

### Post by drs305 on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

The tutorial is about finding and deleting root trash. See Section 7.

---

