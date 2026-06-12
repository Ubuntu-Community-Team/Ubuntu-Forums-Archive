---
title: "Alternate CD Wireless Drivers that do not Work after Reboot"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by FrodoB on 2006-11-22
Several folks have had the experience of installing from the Alternate CD for Edgy Eft and many wireless devices just work out of the box, and then after installation they disappear. This is a problem especially if you do not yet have internet access. 

Here is the procedure for getting wireless back after and install from the Alternate CD for Edgy, even with internet access:

1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

