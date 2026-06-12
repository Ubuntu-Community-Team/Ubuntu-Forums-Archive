---
title: "adsl usb modem, eciadsl driver, pppoe"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by nataraj on 2005-06-29
when i tried to install the driver for my globespan virata wan adsl modem under ubuntu hoary, i get the following error:
nut@ubuntu:~$ sudo dpkg -i /media/download/eciadsl-usermode_0.10-1_i386.deb
(Reading database ... 58812 files and directories currently installed.)
Preparing to replace eciadsl-usermode 0.10-1 (using .../eciadsl-usermode_0.10-1_i386.deb) ...
Unpacking replacement eciadsl-usermode ...
dpkg: dependency problems prevent configuration of eciadsl-usermode:
eciadsl-usermode depends on pppoe; however:
Package pppoe is not installed.
dpkg: error processing eciadsl-usermode (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
eciadsl-usermode
i'm a newbie to linux -
can you please help me- how to proceed?

---

