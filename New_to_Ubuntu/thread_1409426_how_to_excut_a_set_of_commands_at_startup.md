---
title: "how to excut a set of commands at startup?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-02-17
I need to auto mount my partitions when the system starting up, i used these commands:
[PHP]sudo gedit sudo gedit /etc/init.d/modem-init
[/PHP] then i write the commands :
[PHP]#!/bin/bash
sudo mount /dev/sda2 /media/1
sudo mount /dev/sda4 /media/2
[/PHP]to run these commands at start up :
[PHP]chmod +x /etc/init.d/modem-init
ln /etc/init.d/modem-init /etc/rc5.d/modem-init
[/PHP]the question is :
the system can't run this script when boots up, because the sudo password is needed,
how to bypass this problem???

thanks

---

### Post by tom.swartz07 on 2010-02-17
> **MBG1987 said:**
> I need to auto mount my partitions when the system starting up, i used these commands:
[PHP]sudo gedit sudo gedit /etc/init.d/modem-init
[/PHP] then i write the commands :
[PHP]#!/bin/bash
sudo mount /dev/sda2 /media/1
sudo mount /dev/sda4 /media/2
[/PHP]to run these commands at start up :
[PHP]chmod +x /etc/init.d/modem-init
ln /etc/init.d/modem-init /etc/rc5.d/modem-init
[/PHP]the question is :
the system can't run this script when boots up, because the sudo password is needed,
how to bypass this problem???

thanks

If youre trying to mount your partitions at startup, just use fstab. 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Note: be careful with that file, read and make sure you know what youre doing.

---

### Post by MBG1987 on 2010-02-17
thank u, but what if i want to execute other commands such as mkdir,apt-get,...?

---

### Post by achase79 on 2010-02-17
Init.d runs the scripts in the root userspace so you don't need to use sudo

---

