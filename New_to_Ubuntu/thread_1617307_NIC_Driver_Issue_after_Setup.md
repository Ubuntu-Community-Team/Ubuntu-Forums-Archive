---
title: "NIC Driver Issue after Setup"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by HBE66 on 2010-11-09
ive recently setup the current ubuntu server on a asrock ion330 pro machine

the problem is, after istallation it seems that i have no lan connectivity

the settings are correct, but i see no lights flashing and the cable works too

for me it seems as if the lan drivers where missing, but i dont know what nic is installed - is there maybe a way to find out? something like aida for windows

or does someone even have drivers that could work?

thank you!

---

### Post by toekneewood on 2010-11-09
Have a go at any of the following
```

lsusb
lspci
cat /var/log/messages | grep eth
sudo ifconfig -a

```
lsusb will show USB devices
lspci will show PCI devices
cat /var/log/messages | grep eth Will show you what eth number it has decided to use
sudo ifconfig -a     display all interfaces which are currently available, even if down

---

### Post by Hippytaff on 2010-11-09
Also
```

lsmod

```
to see if your driver is installed :-)

---

### Post by toekneewood on 2010-11-09
This might also help [https://help.ubuntu.com/community/Loadable_Modules]("https://help.ubuntu.com/community/Loadable_Modules")

---

### Post by HBE66 on 2010-11-09
that did the trick, thanks toekneewood! :guitar:

---

### Post by Hippytaff on 2010-11-09
Remeber to mark your thread as solved in the thread tools at the top of the page so others can benefit from what you did :-)

---

