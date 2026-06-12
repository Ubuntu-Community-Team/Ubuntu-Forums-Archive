---
title: "Wireshark install"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-03-27
Which repository is wireshark in?
Using Dapper 6.06 did a search in synaptic but returned nothing.
As far as i know i have all repositories enabled in synaptic.
Am told that wireshark is in there.

tried building from source but got a GTK+ not found error.
Even though GTK+ is installed in my system.
Does ubuntu install GTK+ in a different place?
is so where?

---

### Post by Floppyjoe on 2007-03-27
On Edgy 6.10 wireshark is in the networking section in the universe repository.

---

### Post by caliskan on 2007-04-02
I built Wireshark 0.99.5 from source using the "manual install" instructions at:

[http://opensource.qwertzy.com/wireshark_tutorial.php](http://opensource.qwertzy.com/wireshark_tutorial.php)

and things worked fine.  For your reference, the instructions at that site are:

-------------------------------
MANUAL INSTALL:

Install the compilation tools:

#apt-get install build-essential

To compile Wireshark successfully, you need to install the development files for the GTK+ and GLib libraries.

#apt-get install libgtk2.0-dev libglib2.0-dev

Install Checkinstall to easier manage your softwares installed from their source code.

#apt-get install checkinstall
Download and uncompress the Wireshark source code:

#tar -xvf wireshark-0.99.5.tar.gz
Check the Wireshark dependencies:

#cd wireshark-0.99.5
#./configure
If you see this error message, you need to install the GTK+ and GLib libraries as indicated above:

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: GLib2 distribution not found.

Compile and install the tool:

#make
#checkinstall

To launch Wireshark:

#wireshark
-----------------------

---

