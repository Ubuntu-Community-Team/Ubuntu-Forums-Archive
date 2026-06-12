---
title: "Simple Scan, XSane, Brother MFC-240c all-in-one"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-05-09
I have a Brother MFC-240C inkjet printer & scanner. On installation of Natty Narwahl v. 11.04, my scanner function failed.

I added the same line into the file as for Lucid Lynx v. 10.04 and the scanner has now scanned perfectly in both Simple Scan and XSane.

The lines Brother gives are for the following file in:

Ubuntu 9.10, 10.04, 10.10, 11.04

1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

above is found at:

[http://welcome.solutions.brother.com...n1c.html#u9.10](http://welcome.solutions.brother.com...n1c.html#u9.10)

---

### Post by mrnettles on 2011-06-28
Hello, I've had a similar problem. I have a Brother DCP-195C and am running Ubuntu 10.10. I've followed Brother's instructions and installed the drivers from the .deb files. I have also added the libsane rule. The scan programs simplescan and xsane recognise that the scanner is there but won't connect to it. Xsane gives an 'invalid argument' error message.

---

### Post by mrnettles on 2011-06-28
No, it's fine. Worked on restart. Finally!

---

### Post by ParaGuy on 2011-07-13
noob question, how do you open this file where you can edit it?

---

### Post by plucky on 2011-07-14
> **ParaGuy said:**
> noob question, how do you open this file where you can edit it?

From a terminal ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
``` should do the necessary.

Good Luck

---

