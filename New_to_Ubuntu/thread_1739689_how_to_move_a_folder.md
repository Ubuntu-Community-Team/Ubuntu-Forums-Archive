---
title: "how to move a folder"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-04-26
i want to move a folder /home/ray/3danime to /usr/share/backgrounds
i own the first folder but root owns the second
what would be the command to move to usr/share/backgrounds
and what would be the command to remove it 
tks

---

### Post by TeoBigusGeekus on 2011-04-26
```
sudo mv /home/ray/3danime /usr/share/backgrounds
```
to move it and
```
sudo rm -r /usr/share/backgrounds/3danime
```
to delete it afterwards.

---

### Post by rburkartjo on 2011-04-26
teo has always tks

---

### Post by rburkartjo on 2011-04-26
the reason i had to do that is because ubuntu tweak when using in 11.04 wont let you access any folder but /usr/share/backgrounds to change the login screen. with 10.10 it didnt matter what folder you wanted to use.

---

