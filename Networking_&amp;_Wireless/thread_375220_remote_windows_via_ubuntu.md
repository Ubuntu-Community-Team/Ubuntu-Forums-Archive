---
title: "remote windows via ubuntu"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Khaled Khalil on 2007-03-03
hi folks
is there any way to remote windows from ubuntu ?
ubuntu from windows works like ubuntu from ubuntu, but the problem is when windows is the guest

---

### Post by solar george on 2007-03-04
What exactly is the problem.
What are you using to connect to windows remotely.

---

### Post by Khaled Khalil on 2007-03-04
hi solar george, thanks for reply
i use [.NET VNC Viewer]("http://dotnetvnc.sourceforge.net/") on windows and the vnc viewer installed already on Ubuntu Edgy ([RealVNC]("http://www.realvnc.com/") as i found on man).
i connect to ubuntu from windows easily, but i never succeed to connect to windows from ubuntu.
is there some service that must be run on windows ?
i also don't have any fire wall on windows that may prevent the connection !

---

### Post by solar george on 2007-03-04
You could use rdp (aka Remote Access under windows) to connect from linux to windows, just enable it in the system setting in the control panel (I may be wrong about where it is, I don't use windows all that much). Once you have enabled that you can connect using rdesktop under linux.

```
rdesktop *windows*
```
Replacing *windows* with the IP of your windows machine.

---

### Post by gradedcheese on 2007-03-04
The GUI way is Applications->Internet->Terminal Server Client, which should work fine for connecting to a Windows box running Terminal Services.

---

### Post by noMScraig on 2007-03-28
I am very new but got it to finally work easily by downloading the linux version veiwer at realvnc.com under ENTERPRISE EDITION.  I was looking all over of course before I tried the enterprise edition download area.  So at least for me that is an important piece of information.

After downloading simply right click on the file and make it an exectuable program.  Voila...it works just like windoze.

-c

---

