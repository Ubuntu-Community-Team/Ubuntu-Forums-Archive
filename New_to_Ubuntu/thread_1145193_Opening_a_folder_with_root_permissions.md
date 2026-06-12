---
title: "Opening a folder with root permissions"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by user 123 on 2009-05-01
I'm trying to move a tar.bz2 folder into a folder on my filesystem to extract it there, however when i try to move it i get a 'permission denied' error. How can i access the folder with root permissions to allow me to do this?

Thanks

---

### Post by Michael.Godawski on 2009-05-01
hi,

try in terminal 
```
gksudo nautilus
```
but be cautious because now you have root privileges and you can terribly mess up your system :).

Where is the folder you want to move? Where do you want to move the folder?

---

### Post by Pisi-Deff on 2009-05-01
You can open a file browser with root permission by using 
```
gksudo nautilus
```
in the terminal.

Be careful though, you might break your system using root :)

edit:// oh you gotta be kidding me... sniped...

---

