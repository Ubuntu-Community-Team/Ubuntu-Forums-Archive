---
title: "modprobe config already contains alias directive"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by brotherajnin on 2007-01-13
I have a Dell E1505 and I followed all the steps from the HOW TO on getting the wireless card to work using ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I completed all the steps to the point where I enter:

sudo ndiswrapper -l

I thus get:

Installed ndis drivers:
bcmwl5          driver present, hardware present

So good so far?  And then I try sudo ndiswrapper -m and get:

modprobe config already contains alias directive

And then sudo modprobe ndiswrapper returns nothing... my wireless does not come on.  I have tried modifying the BIOS as earlier posted suggested... any suggestions?  The card works fine in Windows... I've been trying to get this for a while now... thanks.

---

### Post by Floppyjoe on 2007-01-13
What is the result of :
```
iwconfig
```

---

### Post by brotherajnin on 2007-01-15
When I enter iwconfig I get:

lo     no wireless connections

eht0  no wireless connections

sit0   no wireless connections

---

### Post by alaw005 on 2007-01-19
I have exact same problem for Marvell Technology Group Ltd. 88w8335 wireless card. Just installed Ubuntu Edgy 6.10 and ndiswrapper with driver from cd.

Can someone please help!!!!!

---

