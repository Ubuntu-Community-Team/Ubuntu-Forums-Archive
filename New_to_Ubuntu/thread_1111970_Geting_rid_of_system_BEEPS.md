---
title: "Geting rid of system BEEPS"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by jose187 on 2009-03-31
I have managed to dissable every sound my laptop makes, apart from one loud beep whenever i logout / shutdown / restart.

Please tell me how i can get rid of it.
Thanks

---

### Post by tarps87 on 2009-03-31
Have you looked in System -> preferences -> sound -> sounds(tab) and System -> administration login window -> accessibility ?

---

### Post by damis648 on 2009-03-31
First, open a terminal and type in
```
sudo rmmod pcspkr
```
and if that removes the system beep, then do the following:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and put in as a new line at the bottom:
```
blacklist pcspkr
```:popcorn:

---

### Post by antitroll on 2009-03-31
Follow the directions here to remove the pc speaker driver from memory and blacklist it from ever starting again.

[http://blog.wolffmyren.com/2008/10/20/disable-ubuntu-system-beep/](http://blog.wolffmyren.com/2008/10/20/disable-ubuntu-system-beep/)

---

### Post by jose187 on 2009-03-31
> **damis648 said:**
> First, open a terminal and type in
```
sudo rmmod pcspkr
```
and if that removes the system beep, then do the following:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and put in as a new line at the bottom:
```
blacklist pcspkr
```:popcorn:

Thanks - that's done the trick.

---

