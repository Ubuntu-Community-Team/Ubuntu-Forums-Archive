---
title: "Inteltool too old?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Tom Collier on 2009-06-13
Using Jaunty 9.04....

Wanted to update Ekiga from 3.2.0; downloaded the tarball of 3.2.4 from the Ekiga site; extracted it, ran ./configure, and it filled the screen for a while, then stopped.

Informed me that the version of intltool installed was too old and said I needed ver. 0.35.0 or newer.  I checked using Synaptic and I have ver. 0.35.0 installed. Not sure what to do or where to go from here.

Was to be my maiden voyage compiling from source, (...I REALLY am getting into and  enjoying this Ubuntu/Linix stuff at the ripe old age of 65) but I seem to have struck this iceberg.

Any lifeboats out there?

Regards,
Tom

---

### Post by 123456789123456789123456 on 2009-06-13
possible, the version of the program you have installed now, how did you install it?

Some packages like that are not compatabile with debuin linux distrabutions, in which Ubuntu is a part of.  try this code, at terminal, tell me what it tells you.

sudo apt-get install ekiga

if it tells you that can't find packages, then it is a program that Ubuntu can not find, download, and install automatically.  serch for an already compiled version, either a .run, or .deb, if .run is exicuted correctly, it may be able to be installed, though those packages are not Ubuntu.  .deb is the best bet.  It is possible that the configuration process you did required certian dependencies, before attempting to install the upgrade, remove the current version of the program.

---

### Post by Tom Collier on 2009-06-14
Here's what I got.  I did know enough to remove any previous installation of Ekiga before i tried to install the updated version 3.2.4.  It looks like the terminal command installed the same version as before...3.2.0.

tomcollier@ubuntu:~$ sudo apt-get install ekiga
[sudo] password for tomcollier: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian po-debconf libmail-sendmail-perl
  gettext calendar-timezones html2text libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  siproxd gnugk mediaproxy ser openser rtpproxy asterisk yate callweaver
The following NEW packages will be installed:
  ekiga
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5598kB of archives.
After this operation, 15.4MB of additional disk space will be used.
Selecting previously deselected package ekiga.
(Reading database ... 106504 files and directories currently installed.)
Unpacking ekiga (from .../ekiga_3.2.0-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up ekiga (3.2.0-0ubuntu2) ...

---

### Post by 123456789123456789123456 on 2009-06-14
> **Tom Collier said:**
> Here's what I got.  I did know enough to remove any previous installation of Ekiga before i tried to install the updated version 3.2.4.  It looks like the terminal command installed the same version as before...3.2.0.

tomcollier@ubuntu:~$ sudo apt-get install ekiga
[sudo] password for tomcollier: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian po-debconf libmail-sendmail-perl
  gettext calendar-timezones html2text libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  siproxd gnugk mediaproxy ser openser rtpproxy asterisk yate callweaver
The following NEW packages will be installed:
  ekiga
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5598kB of archives.
After this operation, 15.4MB of additional disk space will be used.
Selecting previously deselected package ekiga.
(Reading database ... 106504 files and directories currently installed.)
Unpacking ekiga (from .../ekiga_3.2.0-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up ekiga (3.2.0-0ubuntu2) ...

ok, at least it is possible for Ubuntu to get the program
follow what it suggested, go to synaptic package program, remove the packages it listed as no longer needed.  Then go and add the packages it suggests to be installed.  from what it reports, the newest version has not yet been made in a .deb, however the older one has.  Remove the 3.2.0 version, and attempt to configure the new version.  This should take care of any dependencies, and or package conflicts.

---

### Post by Tom Collier on 2009-06-17
I think I'll log a little more flight time in the Ubuntu cockpit before I try compiling again.  I solved the Ekiga problem thought an update might do, simply by reducing the resolution on my webcam.  Now, Ekiga works with audio and video.

Thanks for your interest and assistance.

---

