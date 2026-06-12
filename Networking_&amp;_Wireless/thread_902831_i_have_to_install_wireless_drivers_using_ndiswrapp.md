---
title: "i have to install wireless drivers using ndiswrapper everytime i switch on my laptop."
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-08-27
Hey i have ubuntu 8.04 installed on my system...and earlier when i insatlled my windows drivers using ndiswrapper it worked everytime ..but now..i don't know what actually happened...
i have to install the drivers everytime i switch on my system...
though it shows that it is installed..
but wlan0 doesn't show up when i type ifconfig..
may be its not activated..
but how do i activate it..

---

### Post by caljohnsmith on 2008-08-27
It's difficult to tell for sure from your description, but it may be that ndiswrapper is not getting loaded on startup. Have you put ndiswrapper in /etc/modules? Please do the following:
```
gksudo gedit /etc/modules 
```
And is there a line with "ndiswrapper"? If not, add one. That might be your problem.

---

### Post by shredder12 on 2008-08-28
Ya it had only 3 names 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

so i added ndiswrapper at the end and saved the file..
i hope will it work...!!

---

### Post by shredder12 on 2008-08-29
hey caljohnsmith...
thanks..
it worked....

---

