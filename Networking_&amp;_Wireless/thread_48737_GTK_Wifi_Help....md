---
title: "GTK Wifi Help..."
date: 2005-07-13
forum: Networking &amp; Wireless
---

### Post by Nalos Surith on 2005-07-13
So here's the deal, i cant seem to install python-gnome2-extras, python-gtk, nor python-gnome2. And I can't seem to understand why I keep getting similar errors like this...

> kawn@rhsubuntu:~/Desktop$ sudo dpkg -i python2.3-gnome2_2.10.0-2_i386.deb Selecting previously deselected package python2.3-gnome2.
(Reading database ... 71627 files and directories currently installed.)
Unpacking python2.3-gnome2 (from python2.3-gnome2_2.10.0-2_i386.deb) ...
dpkg: dependency problems prevent configuration of python2.3-gnome2:
 python2.3-gnome2 depends on python2.3-gtk2 (>= 2.4); however:
  Package python2.3-gtk2 is not installed.
 python2.3-gnome2 depends on python2.3-pyorbit; however:
  Package python2.3-pyorbit is not installed.
 python2.3-gnome2 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 python2.3-gnome2 depends on python2.3; however:
  Package python2.3 is not installed.
dpkg: error processing python2.3-gnome2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.3-gnome2

It's like all my dependancy files are are not registering that they are  installed...am I doing something wrong here....

Was their something in the package that i may have installed that could screw this up??

Can anyone help?   :???:

---

### Post by Nalos Surith on 2005-07-13
I can't even install firefox 1.05, does any one know what the problem is im getting an error "Fatal error [-618]: Couldn't open xpistub library" ...I think i might have to re install ubuntu -.-

---

### Post by varunus on 2005-07-13
Try installing the python packages from synaptic instead of the console; dpkg doesn't want to download new files, i think.  Synaptic can do that for you.

How did you install firefox 1.0.5?  From a .deb?  Or from their website?

---

### Post by Nalos Surith on 2005-07-13
i downloaded it from their website and clicked on the install icon.

---

