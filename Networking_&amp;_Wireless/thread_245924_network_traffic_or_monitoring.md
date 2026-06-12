---
title: "network traffic or monitoring"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by bubi1980 on 2006-08-28
hi again,

is there a program for ubuntu which is made for monitoring the network?
what i really need is a program which shows me the signal strength of my connection (wireless card - acces point) and the amount of sent/received data.

thx

---

### Post by pyros on 2006-08-28
right click on an empty spot on the panel, choose "add to panel" look for the network monitor applet. it should have a meter showing strength and more information when you open it.

---

### Post by bubi1980 on 2006-08-28
i did it, but when i click on it i get an ERROR.
it says 
"Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device"

what now? internet is working....

and one more question, how to open and run .deb file which i ve just downloaded?

thx for the quick reply

---

### Post by pyros on 2006-08-28
Just to be sure, you are using the network monitor, not the modem monitor, right?

You might be getting that error because the monitor is looking at the wrong device by default. If it is adding the icon of the two computers to the toolbar, double-click on it and look for the drop-down menu under "connection" and to the right of "name". 

It probably says something like eth0 or lo, click the arrow at the right and look for other options. If your internet connection is working, one of those should be the right network adapter.

You can just double click on the .deb file, if it works with the ubuntu repositories it should give you an option to install.

---

