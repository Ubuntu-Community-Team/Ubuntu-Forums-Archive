---
title: "Change config files?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Unixp on 2009-12-20
Hello i haev tryed to get to know how i can change my config files? 

Like for example in /etc/rc.local 

i whant to change that file, but i dont know how to do it, can anyone help me?

/alec

---

### Post by milosz.galazka on 2009-12-20
There are couple solutions:
1. From Gnome. Hit ALT + F2 and enter: 
```
gksu gedit /etc/rc.local
```
then enter your password
2. From terminal (gnome-terminal for example). Enter in terminal:
```
sudo su -
```
then your password.
```
nano /etc/rc.local
```

---

### Post by Unixp on 2009-12-20
Thanks for an exelent answer!

It solved my problem!

---

### Post by audiomick on 2009-12-20
Hallo.
If you do
```
gksu /path/and/filename
```
in a terminal, it will open the file in gedit as a super user. You should then be able to edit and save it.

Be very careful using this, it allows you to break your system if you do something wrong.

If you are changing system files, it is a good idea to comment out (put a # at the start of) the old line and add a new one, and a comment about what you did, in case you want to go back at some stage.

```
# old line that you want to change
# comment: the following is the line I added
new line
```

---

