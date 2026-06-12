---
title: "Installing brother MFC 210C"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by maheshjr2000 on 2009-02-22
Im trying to install the lpr and the cupswrappers for the Brother MFC 210C and even though Im following instructions it gives me an error saying 
Setting up mfc210clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC210C': No such file or directory
chown: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC210C': No such file or directory
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so': File exists

and for the cups:
(Reading database ... 231700 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
touch: cannot touch `/usr/share/cups/model/brmfc210c_cups.ppd': No such file or directory
/usr/share/cups/model/brmfc210c_cups.ppd: No such file or directory.
dpkg: error processing cupswrappermfc210c (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrappermfc210c

It cant be a permissions issue because I was using root terminal. Any ideas :(.

---

### Post by ramjet_1953 on 2009-02-22
Have you checked out this link?

[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

Regards,
Roger :D

---

### Post by maheshjr2000 on 2009-02-22
I swear to god I am an idiot sometimes, I read through the instructions but IGNORED the prerequisite procedures the first time around. Thank you VERY much ramjet for pointing me to that link again.

EDIT: and in CONTINUING to be an idiot I didnt read your name there. Thank you roger!

---

