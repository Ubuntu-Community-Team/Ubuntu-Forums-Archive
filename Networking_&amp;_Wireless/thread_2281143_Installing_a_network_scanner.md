---
title: "Installing a network scanner"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by bjohnson210 on 2015-06-04
First off my apologies if this should have been in Hardware.

I have a multifunction laser printer, Samsung SCX-3400 series.  I got the printer installed and working fine, just needing to get the scanner working.  I looked at online resources and it gave information on how to do it, but being new to Ubuntu, its a bit advanced for me.  I was able to get xsane installed through a terminal, but after that I get a bit lost.

Any help would be greatly appreciated!  So happy to be learning a new OS!

---

### Post by mccalleyt on 2015-06-07
What flavor of linux do you have and what version?

---

### Post by kurt18947 on 2015-06-09
How did you install your Samsung printer? I have a Samsung MFD (not sure the model, newish though). The printer portion will install without external drivers but not the scanner. I use Samsung's installer. It installs both the printer & scanner drivers and helps with network connection. Does this look familiar?

[http://www.samsung.com/us/support/owners/product/SCX-3405FW/XAA](http://www.samsung.com/us/support/owners/product/SCX-3405FW/XAA)

The drivers are installed via a BASH script. If you're not familiar I'm sure someone can help. tar.gz files are similar to .zip if you're not familiar with the file type. 

There were improvements with the switch from Gnome 2 to Gnome 3/Unity but printer management was not one. Part of my post-install install is to add the app "system-config-printer" from the repositories. The "printers" app present by default is pretty limited. System-config-printer can be launched by pressing <alt-F2> or via the command line. I'm using Ubuntu-Gnome but I believe the same commands work in Ubuntu with Unity.

---

