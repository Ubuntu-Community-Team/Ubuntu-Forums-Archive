---
title: "How do I log in as the superuser"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by vijaya.vtk on 2009-11-08
how to login as super-user

---

### Post by cariboo on 2009-11-08
For ]aAny command the you need to be root to do, just use sudo or gksudo.

Sudo is used for command line commands, and Gksudo is used for graphical commands eg:

```
sudo mv file1 file2
```

or

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by GimmeCoffe on 2009-11-08
```
gksudo nautilus
```

---

### Post by jrothwell97 on 2009-11-08
You should avoid logging in as the superuser and use sudo and gksudo instead.

If you want a root console, open up a normal terminal and run sudo -i.

---

### Post by tommynz1975 on 2009-11-08
vijaya.vtk
just for the record, root has no password and you are advised to leave it that way. unlike apple iphones that have a default obvious password.

as said before use sudo etc

---

### Post by jmszr on 2009-11-08
vijaya.vtk,

Here is the "Forum policy on log-in-as-root tutorials": [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

It explains why it is unnecessary and unwise.

---

