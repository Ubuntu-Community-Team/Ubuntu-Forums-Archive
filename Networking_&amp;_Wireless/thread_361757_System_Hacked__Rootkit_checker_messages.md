---
title: "System Hacked??  Rootkit checker messages"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by jcconnor on 2007-02-14
I have recently run a rootkit checker on my machine and got the following messages (most of them said nothing found, not infected, not detected, that kind of thing) but I got this and was wondering if I needed to be concerned:

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/xulrunner/.autoreg
/lib/modules/2.6.17-11-generic/volatile/.mounted

and I got this message too:

Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security

Has this system been compromised? 

Thanks,

John

---

### Post by revertex on 2007-02-14
take a closer look at these files, they are pointed because are hidden files.

the java related files seems default, but dunno about the others.

---

### Post by scrooge_74 on 2007-02-14
[http://www.ubuntuforums.org/showthread.php?t=278695](http://www.ubuntuforums.org/showthread.php?t=278695)

---

### Post by jcconnor on 2007-02-14
Thanks for the help!!

I know, I should have done a search on OBSD first but my enthusiasm got the better of me.

But I appreciate the quick response!

John

---

