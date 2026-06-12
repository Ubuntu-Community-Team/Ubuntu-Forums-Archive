---
title: "[SOLVED] Failure to download updates"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-12-06
Today I tried to run my updates and got this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I try to run the dpkg I get a message that superuser permission is required.  What now?  To whom am I supposed to report that the second command failed?

---

### Post by oilchangeguy on 2008-12-06
at the terminal (command line) type sudo dpkg --configure -a  and press enter.

---

### Post by wheelerrver on 2008-12-07
This fixed my problem, many thanks.

---

