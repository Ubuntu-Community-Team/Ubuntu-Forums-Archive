---
title: "Linksys wireless card, how do i get it to work?"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by xVern on 2005-09-07
here are the driver details:

File;
C:\windows\system23\drivers\BCMWL5.SYS

Provider: Broadcom Corporation
File version: 3.30.15.0
Copyright: 1998-2002, Broadcom Corporation All Rights


is there anyway i can get linux drivers?
Or maybe just get these ones working in ubu?


thanks!

---

### Post by mjc2264 on 2005-09-07
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

check this out. this kind of worked for me although i'm still in the midst of getting this sorted out. i used kynaptic to install ndiswrapper-utils and ndiswrapper-source.

without source i got an error when trying to modprobe

after that the guide pretty much got my drivers + hardware detected. the weird part now is when i try to activate the device in KDE network device setup, it instantly disables itself again. anyone know why this is?

kwifimanager starts doing something but i can't get it to see any network. previously i tried linuxant or whatever. that saw some ssid's, but i couldn't get it to connect to anything either. i'm stuck.

i'm running kubutnu on a dell inspiron 8500 with a dell truemobile 1300 internal wireless card. any help would be appreciated.

---

