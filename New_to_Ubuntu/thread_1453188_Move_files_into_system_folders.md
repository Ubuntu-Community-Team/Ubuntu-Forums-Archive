---
title: "Move files into system folders"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by tottetotte on 2010-04-12
Apparently I dont have the premission to delete, rename or move files into the system folder as /etc/x11/. I kinda deleted a file with the terminal in that folder but I have a back up. So how do I get premission to move in a file? I have ubuntu 9.10 if needed to know.

---

### Post by mgranet on 2010-04-12
If you wish to do it graphically:
```
gksudo nautilus
```

From the terminal:
```
sudo mv *filename* *destination*
```

---

### Post by Iowan on 2010-04-12
Have you tried with **sudo**
 (**ie. sudo mv ./myfile /etc/new/location**)?

---

### Post by tottetotte on 2010-04-12
thx it worked <3

---

