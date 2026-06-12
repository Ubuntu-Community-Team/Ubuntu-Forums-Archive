---
title: "k-9 copy codex"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-16
I tried to add these codex i thought i already had them trying to rip one of my own dvd's!!!!!
[I]darin@darin-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add – && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
[sudo] password for darin: 
/etc/apt/sources.list.d/medibuntu.list: No such file or directory
darin@darin-desktop:~$ [/I]

---

### Post by oldos2er on 2009-08-16
Run
```
sudo touch /etc/apt/sources.list.d/medibuntu.list
```
then retry your command.

---

### Post by DarinB on 2009-08-17
please explain the touch command?????

---

### Post by DarinB on 2009-08-17
Ok still don't understand what is happening??? its in the download sources!!!![ATTACH]125221[/ATTACH]

darin@darin-desktop:~$ sudo touch /etc/apt/sources.list.d/medibuntu.list
[sudo] password for darin: 
touch: cannot touch `/etc/apt/sources.list.d/medibuntu.list': No such file or directory
darin@darin-desktop:~$

---

### Post by oldos2er on 2009-08-17
**touch** creates an empty file of a name you specify (see **man touch**).

 Can you post the output of **ls -la /etc/apt/sources.list.d** ?

 Have you tried running** sudo apt-get update && sudo apt-get install ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 **?

---

