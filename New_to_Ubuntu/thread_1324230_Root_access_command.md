---
title: "Root access command?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-11-12
Is there a way to gain access to the root account in the shell, so instead of user@...:~ is it root@....:~ ?

---

### Post by ukripper on 2009-11-12
```
sudo su
```

---

### Post by sisco311 on 2009-11-12
Please don't use *sudo su* or *sudo su -* until you know exactly what are you doing.

If you really need a root shell, type:
```
sudo -i
```
to logout, type:
```
exit
```
or press Ctrl+d

for details:
[uhelp]community/RootSudo[/uhelp]

---

