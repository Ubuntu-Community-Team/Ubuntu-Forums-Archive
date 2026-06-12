---
title: "Epson PX-101 doesn't work"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by ookiimarukochan on 2009-10-23
I'm running Ubuntu 9.04 64-bit.
The Epson PX-101 is apparently supported by Gutenprint.
I installed the gutenprint database for foomatic (from synaptic) but it didn't get added.
I then got the latest tarball for gutenprint, and built/installed that. I can now see the driver but trying to add a PX-101 printer gives the following error:

Cannot read file /usr/share/foomatic/db/source/printer/Epson-PX_101.xml!
Cannot read file /usr/share/foomatic/db/source/printer/Epson-PX_101.xml!
Entity: line 837: parser error : Opening and ending tag mismatch: printer line 0 and foomatic
</foomatic>
           ^
No printer ID found
"<printer>" tag not found!
Could not run "foomatic-combo-xml"/"foomatic-perl-data"! at /usr/share/perl5/Foomatic/DB.pm line 1078.
 * Reloading Common Unix Printing System: cupsd                          [ OK ] 

I've tried using the 64 bit DEB file from linuxprinting.org but nothing has changed.

---

