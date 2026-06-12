---
title: "Virtual Machine seemless mode"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-07-23
Hey guys and girls!
 Okay, I am looking to sooth a beast from a borked Windows dual boot. Looking at possibly doing a virtual machine. I have noticed a seemless mode choice in Virtual Box, but I can not choose it. Why? Is that a paid for option? I can not work off that tiny little screen that you normally get.

Tips tricks and ideas all welcome
Thanks

---

### Post by Nerflander on 2010-07-23
`Just host the virtual machine normal. give a nat adapter and your the way to go!

if you want to host stuff from it like webserver etc give a second virtual ethernet adaptar (host only)

for the rest virtualbox is open source and completely free. So i quess you just dont meet the requirements of the mode.

---

### Post by tarps87 on 2010-07-23
> **AndyP79 said:**
> Hey guys and girls!
 Okay, I am looking to sooth a beast from a borked Windows dual boot. Looking at possibly doing a virtual machine. I have noticed a seemless mode choice in Virtual Box, but I can not choose it. Why? Is that a paid for option? I can not work off that tiny little screen that you normally get.

Tips tricks and ideas all welcome
Thanks

You need to install guest additions to use seamless mode, Devices -> Install guest additions

If you just want to resize the screen, just set the desktop resolution using the normal method for you guest os. The one running in Virtual Box.

The differences between the open source version and closed source are found here:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

