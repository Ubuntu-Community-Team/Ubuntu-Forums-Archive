---
title: "Install a new app during Live USb boot"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by flaviocb on 2009-10-23
Hello, there is a way to automatically install a custom app (contained inside a .deb package) just after the boot ?
 
I am working in a educational package and I would like to distribute in a Live USB and preferably already installed at the end of the boot. 
 
I don't found where to leave a script to call dpkg to install my package and leave an icon on the desktop.
 
Any idea on to help me in this automatic install after Live USB boot ?
 
Regards,
 
Flavio

---

### Post by jeremyswalker on 2009-10-23
You could always use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom image for distribution.

---

### Post by az on 2009-10-23
IF you are dealing with a live USB system, just create a persistent home and install the deb.  Every time you reboot the live system using the persistent home, your app will already be installed.

If you need to distribute this system just redistribute the whole thing, including the persistent home.

---

### Post by flaviocb on 2009-10-24
Thank you, both tips are great !

I think the persistent home will be the easier. When you mention to creathe the /home as peristent do you mean to create it on the partition where the installbles are, or to crate a paritiion named /home on the USB pen drive ?


Regards,

---

### Post by flaviocb on 2009-10-24
Another question regarding the /home solution:

The app I am using installs some modules under /usr and other directories. I have a second package that should require some special library as a pre-req also. 

Do you think if I unpack all of those packages under /home I will be able to solve the dependencies or should I expect some problems ?

---

### Post by az on 2009-10-25
It's actually not a persistent home - calling it that is a legacy title - it's a persistent everything.  Just install any deb package and everything that is written to your system (home, usr, everything) will be preserved.

Use the USB Startup Disk Creator in System > Administration.  Move the slider at the bottom to allocate more or less space on your USB device.

---

