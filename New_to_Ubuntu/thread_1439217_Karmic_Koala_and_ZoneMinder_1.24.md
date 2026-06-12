---
title: "Karmic Koala and ZoneMinder 1.24"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Pythaules on 2010-03-25
I have been trying all day to get ZoneMinder 1.24 on my new Ubuntu 9.10 desktop.  
I get this:

DBI connect('database=zm;host=localhost','zmuser',...) failed: Unknown database 'zm' at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/bin/zmupdate.pl line 49.
BEGIN failed--compilation aborted at /usr/bin/zmupdate.pl line 49.
dpkg: error processing zoneminder (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder


Does anyone out there now how I might correct this issue.

---

### Post by no2498 on 2010-03-26
if you only have 1 cam get wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope this helps

---

