---
title: "Cant get wireless to work"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by kd1 on 2010-05-24
hi i just upgraded to ubuntu 10.04 from windows xp and i cant get my wireless connection to work what do i need to do my wired connection works great. please help i know there are loads of sites regarding this but i cant seem to get it to work

---

### Post by Sealbhach on 2010-05-24
First thing to do is look in System/Administration/Hardware Drivers and see if there are any drivers there for you to install.

Also, to help us help you, please open a terminal (Applications/Accessories/Terminal) and run this copy

```
lshw -C network
```

and copy and paste the result back here.

.

---

### Post by chiefster on 2010-05-24
through package manager you can download a program called NDISwrapper (download the GUI as well).  this lets you use windows wireless drivers in ubuntu.  Once you have installed NDISwarpper you can selct the GUI in system->administration

You need to download the windows driver for your specific card from the interweb and it must be in .inf format.

You can find out what wireless card you have by typing the following into a terminal
lspci | grep Wireless
I (and many others) have problems with atheros wireless cards in ubuntu.  the windows driver is the only way I can get the damn thing working.


EDIT:  listen to the other guy, he almost certainly knows a lot more than me :)

---

