---
title: "browser says sorry applet not found"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by medhat1 on 2010-10-23
after last system update the browser no longer has java applets that were ok before on same web  site now I go to the web site and I get the "sorry"message , I tried to "undo" the update ala "system restore in windows" but could not , then tried to reinstall java but could not open the bin file as instructions are too cryptic for me & I dont know the password for the root .I installed 2 other browsers firefox and chrome ,still no java applet.
plz help , will the bug report below shed some light ?

ProblemType: Bug
Architecture: lpia
Date: Mon Sep 20  21:21:16 2010
DistroRelease: Ubuntu 8.04
ExecutablePath:  /usr/bin/gnome-system-monitor
NonfreeKernelModules: wl
Package:  gnome-system-monitor 2.22.3-0ubuntu2
PackageArchitecture: lpia
ProcEnviron:
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage:  gnome-system-monitor
Uname: Linux 2.6.24-27-lpia i686

---

### Post by kerry_s on 2010-10-23
use "ubuntu-restricted-extras" for those kind of drivers, that way they stay up-to-date with your system.

---

### Post by medhat1 on 2010-10-23
thanks , I looked at synaptic & this  restricted package did not show up under installed or even under "all" how can I install it?

---

### Post by the.phantom on 2010-10-23
try
applications/ubuntu software center

then top right do a search for "restricted extras" and do the version you have ( ubuntu,kubuntu or what)

NOTE:

there are two java's
sun java and the free java
if you just want sun java
applications/ubuntu software center/connical partners and look for sun java
jre

---

