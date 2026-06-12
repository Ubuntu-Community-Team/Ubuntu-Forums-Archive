---
title: "Terminal Command"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Eddie002Fast on 2008-12-14
Anyone know the Terminal Command for the Update Manager? Thx!!! :D

---

### Post by Izek on 2008-12-14
I believe it's **apt-get update upgrade**. Or are you looking for the execution for the GUI Update Manager?

That would be **/usr/bin/update-manager** or just **update-manager**

---

### Post by spiderbatdad on 2008-12-14
```
update-manager
```:popcorn:

---

### Post by Patricrawley on 2008-12-14
update-manager
update-manager -d if you want to upgrade the ditribution.

---

### Post by Eddie002Fast on 2008-12-14
Thanks guys! I was looking for Exe command but both exe and upgrade commands i will need too know thx !

Im finding that its more helpful if i have a problem too run something threw the Terminal and copy paste the error into the forums post/thread rather than just tell someone what the problem is ! :lolflag:

---

### Post by Eddie002Fast on 2008-12-14
What's the Terminal Command for checking for updates then what command for installing updates........I want to run the whole process in the Terminal because if I have an error message I can copy it from there and paste it  in a forum ! :popcorn:

---

### Post by hrod beraht on 2008-12-14
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Patricrawley on 2008-12-14
```
sudo apt-get update
```
Check Packages
```
sudo apt-get upgrade
```
Upgrade outdated packages

---

### Post by Michael.Godawski on 2008-12-14
hi,

although for the server the info is usable:
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)

---

