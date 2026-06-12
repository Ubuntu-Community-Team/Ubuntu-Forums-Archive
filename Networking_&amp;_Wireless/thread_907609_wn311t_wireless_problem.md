---
title: "wn311t wireless problem"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by stryker1800 on 2008-09-01
i just installed ubuntu 8.04 on my desktop that has the netgear wn311t wireless pci card in it. i have followed various tutorials and was able to get the driver installed and windows wireless drivers tells me the driver is installed and the hardware is present but i cant configure a network and havent found a tutorial or post anywhere that adresses my problem.

---

### Post by Wardish on 2008-11-19
Installing the wn311t driver for the pci wireless card.  Installs with a bad message and does not operate.  Running 8.04.

Message is: Couldn't find models section "linksys"


The driver isn't completely installed.  but shows up where it's supposed to.

iwconfig see's it but is unable to change any parameters.
Ditto for the graphical interface.

I've read many posts with varying instructions for installs and have tried most of them with variations.  No luck with this problem.  I've not found any reference to this particular problem in the forums.

Thanks for the help,

Ward

---

### Post by Wardish on 2008-11-20
Ok, it's working now.

Found a thread that said the driver files produced by unpacking on a linux/ubuntu system were different from the same named files produced on an winxp system.

The same thread also supplied a zip file with the .inf file and the .sys file.

Removed the old installation and installed with these files and no errors were reported.

Everything set up and working now.

NOTE: This connection will not work if the router is not set up to broadcast the ssid.  I've a few idea's why but it's working and I'm tired of fooling with wireless.

A BIG THANK YOU for all the posters in various threads that helped me over a number of issues along the way.

Ward

---

