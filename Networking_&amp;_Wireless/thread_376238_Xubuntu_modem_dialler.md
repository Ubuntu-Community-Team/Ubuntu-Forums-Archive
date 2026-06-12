---
title: "Xubuntu modem dialler"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Linux_Zoo on 2007-03-04
I've got Xubuntu installed and running, using the pon and poff scripts to connect to the internet via an internal PCTel dialup modem.

I'm setting the machine up for my mother, and I'd like her to have a simple way to connect and disconnect, as 'on demand' settings (with their idle time) have been too difficult for her to grasp in the past.

I've tried adding launchers, one called 'Connect' that calls the pon comman, and the other called 'Disconnect' that calls the poff command.  Problem is that the internal modem does not make any dialling sound, so there is no feedback that dialling is actually happening.

Does anyone know:
a) How to make the PCTel modem actually make a dialling noise (I've tried adding commands in the ATDT section of the dial commands, but it makes no difference), or

b) A visual dialling interface for Xubuntu / XFCE (like Modem Lights?) that gives visual feedback?

Thanks for your help.

---

### Post by Linux_Zoo on 2007-03-06
Seems nobody knows the answer!

I've ended up installing Gnome PPP.  It works OK, but not sure about the gnome overhead I'm now incurring on an otherwise XFCE system.

---

