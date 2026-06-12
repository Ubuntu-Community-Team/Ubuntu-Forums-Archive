---
title: "New install, No wireless or Ethernet"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by straylight01 on 2011-03-07
Hey guys, 
Just installed xubuntu on my friends Toshiba Satellite L635. 
Issues are:

Not detecting ethernet
Not detecting wireless

I googled around for a bit, found the driver listed as
RTL8191SE-VA2

Pulled it off the realtek website (was unable to find it anywhere else) According to the enclosed readme file I am supposed to compile the driver from the source code. 

Currently researching how to do that, wondering if anyone else could offer some assistance with how to get the thing online.

---

### Post by bwang on 2011-03-07
You will need to grab build-essential and all of its dependencies manually and install them.

---

### Post by straylight01 on 2011-03-07
Right, so will I be able to compile it on this system, and then transfer the the compiled driver to the the Toshiba with a USB? 

Or will I need to compile the source code with the Toshiba, and if so, is there a way to get build-essential without access to Ethernet, or wireless?

---

### Post by straylight01 on 2011-03-07
Ok, uninstalled xubuntu, and installed ubuntu 10.10 notebook.

Was able to find the ethernet, attempted to compile the wireless driver from source code, and was given the following error messg:


Selecting previously deselected package rtl8192se-linux-2.6.0019.1207.2010.
(Reading database ... 135775 files and directories currently installed.)
Unpacking rtl8192se-linux-2.6.0019.1207.2010 (from .../rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb) ...
dpkg: error processing /usr/local/src/rtl8192se_linux_2.6.0019.1207.2010/rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb (--install):
 unable to create `/etc/realtek/wireless-rtl-ac-dc-power.sh.dpkg-new' (while processing `./etc/realtek/wireless-rtl-ac-dc-power.sh'): No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/local/src/rtl8192se_linux_2.6.0019.1207.2010/rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb



Any ideas?

---

