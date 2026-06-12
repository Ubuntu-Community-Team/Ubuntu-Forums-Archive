---
title: "Wifi problems in ubuntu 8.10"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by krishh123 on 2009-02-28
I have installed my ehome wireless adapter thru NDISWRAPPER 1.54.Everything works out fine but after restarting my pc i need to install the driver again by typing the following commands

depmod -a
modeprobe ndiswrapper

Can anyone suggest me how to make tis driver persistent.Is there any shell script that could run these two commands everytime i logon to ubuntu at the startup itself.

---

### Post by adult swim on 2009-02-28
run this```
gksudo gedit /etc/modules
``` and make a new line at the end of the file and put in ```
ndiswrapper
``` then save and close the file

---

