---
title: "Problem installing a game"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-04
I was trying to install .deb game on my computer but something went wrong. Can you tell me what?


z@z-pc:~$ cd /home/z/downloads
z@z-pc:~/downloads$ sudo dpkg -i openlierox.deb
Selecting previously deselected package openlierox.
(Reading database ... 120048 files and directories currently installed.)
Unpacking openlierox (from openlierox.deb) ...
dpkg: dependency problems prevent configuration of openlierox:
 openlierox depends on libsdl-image1.2 (>= 1.2.5); however:
  Package libsdl-image1.2 is not installed.
 openlierox depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Package libsdl-mixer1.2 is not installed.
 openlierox depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Package libsdl-mixer1.2 is not installed.
 openlierox depends on libsdl-image1.2 (>= 1.2.5); however:
  Package libsdl-image1.2 is not installed.
dpkg: error processing openlierox (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 openlierox

---

### Post by Paul820 on 2010-11-04
Open up synaptic package manager, in the top right hand corner, click on search, enter **libsdl**.

According to the errors you need:
libsdl-image1.2 (>= 1.2.5)
libsdl-mixer1.2 (>= 1.2.6)

Just check the box next to those and install them.

---

### Post by Jetso on 2010-11-04
Have you just tried double clicking it where ever it is? Then it will say your dependencies you need.

---

### Post by wannabeterminalpro on 2010-11-04
Thanks, I got the game working :D It's amazing how fast you get answers on here :)

---

### Post by Paul820 on 2010-11-04
We all know how frustrating it can be when you first use Ubuntu. Everyone on here is very helpful :)

---

### Post by anewguy on 2010-11-04
As an extra note, when you run into this type of problem, it is normally because you didn't use the package manager to install the software.  The package manager will make sure to also install the dependencies.

If you do a manual download and get this message, try:

sudo apt-get build-dep <package-name>

in your case it would have been:

sudo apt-get build-dep openlierox

and it should get the dependencies so you can try again.

Dave ;)

---

### Post by sandyd on 2010-11-04
> **anewguy said:**
> As an extra note, when you run into this type of problem, it is normally because you didn't use the package manager to install the software.  The package manager will make sure to also install the dependencies.

If you do a manual download and get this message, try:

sudo apt-get build-dep <package-name>

in your case it would have been:

sudo apt-get build-dep openlierox

and it should get the dependencies so you can try again.

Dave ;)
that is only if you install non-deb programs that you need to compile btw

---

