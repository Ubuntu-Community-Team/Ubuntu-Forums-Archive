---
title: "Problem with VirtualBox OSE"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by sharbeloun on 2009-02-02
Hey all,

i have installed Windows XP SP3 using the virtualbox but the problem is
that this windows xp doesnt recognize the CD-ROM or the USB's ! 

does anybody know what to do ?

thanks

---

### Post by js_fr on 2009-02-02
The OSE edition of VirtualBox does not contain USB support (see [http://www.virtualbox.org/wiki/Editions]("http://www.virtualbox.org/wiki/Editions"))
You have to install the non-OSE version of VirtualBox for this. Instructions can be found here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by sharbeloun on 2009-02-02
so which means that the non-OSE edition of virtualbox would also recognize the usb inputs ?

---

### Post by sharbeloun on 2009-02-02
and CD-ROM

---

### Post by sharbeloun on 2009-02-02
I have downloaded the appropriate package and installed it.. 

no how can i use the Virtual .. where is it found ?

---

### Post by js_fr on 2009-02-02
You should find an entry for virtualbox in the menu under Applications -> System Tools. If not you can add an entry manually and / or start it from a console with the command ```
VirtualBox
```
By the way, you don't have to download and install VirtualBox manully, you can add a line to your /etc/apt/sources.list like it is described on the download page [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads"). For intrepid the line would be: ```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```
Then you can install it via Synaptic as any other package.

---

