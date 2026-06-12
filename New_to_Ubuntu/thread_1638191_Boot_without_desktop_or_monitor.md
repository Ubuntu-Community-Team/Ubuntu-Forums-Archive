---
title: "Boot without desktop or monitor"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Shellbak3 on 2010-12-05
I'm new to Ubuntu but have used Unix a bit in the past (15 years ago).  I'm expecting delivery of 4 PC-104 computers in two or three weeks.  The computers will ultimately be installed in an aircraft to control research instruments, gather, and store data.  One of them, the "master" will be used by the operator and have a small display, mouse, and keyboard - the others will communicate with the master via a wired LAN and will not have monitors, keyboard, etc.  The idea is that when the main power switch is turned on all the computers will boot, a program will start and they will start to initialize and the clients will connect to the master.

I'd like to configure the clients so that if there is a monitor and keyboard attached (probably back at the lab) the user will have a few seconds to select a command line boot, or a desktop boot.  If not in a desktop  boot I don't want the computer attempting to access the LAN for updates etc.  The machines do not have CD/DVD drives (but will have USB ports).  Obviously the boot cannot require a password for this!

My questions are: What is the degree of difficulty to achieve this?   Are there books or articles I should read first?  Any suggestions on the path to take?

TIA

---

### Post by HermanAB on 2010-12-05
Howdy,

COnfigure them to always boot without a GUI and in the Lab, type 'startx' at the command prompt.

---

### Post by CharlesA on 2010-12-05
> **HermanAB said:**
> Howdy,

COnfigure them to always boot without a GUI and in the Lab, type 'startx' at the command prompt.
You'd have to stop gmd in order to prevent the GUI from loading automatically don't you?

---

### Post by Shellbak3 on 2010-12-07
Thanks, all, with your comments I was able to find a how-to and I'm posting the link as a reference.

[http://blog.zloether.com/2009/09/disable-gui-in-ubuntudebian.html](http://blog.zloether.com/2009/09/disable-gui-in-ubuntudebian.html)

---

