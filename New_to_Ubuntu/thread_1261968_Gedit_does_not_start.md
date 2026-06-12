---
title: "Gedit does not start"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by adit on 2009-09-09
I tried to start Text Editor by clicking
Main Menu -> Accessories -> Text Editor.  The program didn't start.
I typed in terminal
```
~$ gedit
```There is no output.  Command prompt returns back.
```
~$ which gedit
/usr/bin/gedit

```I don't know what happens.  Today only this problem occurs.  Previously I was using gedit in this same computer.  I am using ubuntu 8.04

---

### Post by Penguin Guy on 2009-09-09
You could try reinstalling it:
```
apt-get install --reinstall gedit
```

---

### Post by adit on 2009-09-09
I reinstalled.  Gedit is working now.  But what could be the cause of this problem?

---

