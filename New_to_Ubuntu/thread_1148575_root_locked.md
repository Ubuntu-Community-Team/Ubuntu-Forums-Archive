---
title: "root locked"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by fminmexico on 2009-05-04
My root folder is locked,the permissions are all grayed out.How do I unlock it.
          fminmexico

---

### Post by halitech on 2009-05-04
Unless you have a certain reason for going into the root folder, you shouldn't be copying anything in there as you don't "own" anything outside your home folder.

If you need to, you can either use the terminal and use
```
sudo cp /location/of/original/file /location/you/want/file
```
or Press ALT+F2 and run
```
gksudo nautilus
```to open a root nautilus. Be very careful with both as you can seriously damage your system.

---

### Post by fminmexico on 2009-05-04
> **halitech said:**
> Unless you have a certain reason for going into the root folder, you shouldn't be copying anything in there as you don't "own" anything outside your home folder.

If you need to, you can either use the terminal and use
```
sudo cp /location/of/original/file /location/you/want/file
```
or Press ALT+F2 and run
```
gksudo nautilus
```to open a root nautilus. Be very careful with both as you can seriously damage your system.

1. no such file or directory.
2. nothing happened.  
 fminmexico.

---

### Post by halitech on 2009-05-04
1. did you change the /locations/ to where the file actually is and where you want it?

2. sorry, my bad. in Xubuntu it would be gksudo thunar

---

### Post by fminmexico on 2009-05-04
> **halitech said:**
> 1. did you change the /locations/ to where the file actually is and where you want it?

2. sorry, my bad. in Xubuntu it would be gksudo thunar

thank you that worked.
   fminmexico

---

