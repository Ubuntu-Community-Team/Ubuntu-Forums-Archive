---
title: "How do i use ndiswrapper in windows?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Robert98374 on 2009-02-08
I am trying to get my wireless USB adapter to work in Ubuntu but i am not sure how to use ndiswrapper. My Adapter is a D-Link DWA-130, and i found that it can be done but i am unsure on how in windows so i would be able to burn the files to CD or something along those lines?

---

### Post by Kevbert on 2009-02-08
> **Robert98374 said:**
> I am trying to get my wireless USB adapter to work in Ubuntu but i am not sure how to use ndiswrapper. My Adapter is a D-Link DWA-130, and i found that it can be done but i am unsure on how in windows so i would be able to burn the files to CD or something along those lines?

To install in Ubuntu... Do you have the windows .inf and .sys driver (it should be on a driver disk/CD with the USB drive) ? You need to use the one for Windows XP.
You'll need to install the firmware via ndiswrapper (to install the windows drivers). You can install ndiswrapper and ndisgtk via the installation CD if you haven't already. Pop the Cd in the drive and browse to /pool/main/n in there you'll find folder for ndiswrapper and ndisgtk. In each of these you'll find a .deb file, double click on each of the .deb files to install them.
Now you need the windows drivers. Copy the .inf and .sys files to your home folder by right clicking on them and selecting Save Link As.
Now go to System-Administration-Windows Wireless Drivers (this is ndisgtk).
Click on Install New Driver and point it to your downloaded .inf file that you've just saved.
It should now be possible to turn on and use wireless (I'm not sure if you need to perform a reboot first).
If you don't have these driver files please connect your USB adapter and then go to Applications-Accessories-Terminal and enter
```
lsusb
```
(list USB devices) and post back the result here.

---

### Post by Robert98374 on 2009-02-08
Awesome! Its going now thanks :D

---

### Post by tanha on 2009-04-28
> **Robert98374 said:**
> Awesome! Its going now thanks :D

Are you using x86 or x86_64? Are you using it in 802.11g or 802.11n mode?

---

