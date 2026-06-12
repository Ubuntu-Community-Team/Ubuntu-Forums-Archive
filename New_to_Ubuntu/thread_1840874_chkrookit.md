---
title: "chkrookit ?"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by jbalazs on 2011-09-08
After running chkrootkit I got this, what dose it mean ?

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/xulrunner-1.9.2.22/.autoreg /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.26/.systemPrefs

---

### Post by Frogs Hair on 2011-09-08
Here is the readme for the application and I don't see that output listed . I have also read about false positives in the past connected to chirootkit.
[http://www.chkrootkit.org/README](http://www.chkrootkit.org/README)

---

### Post by gandaran on 2011-09-08
> **jbalazs said:**
> After running chkrootkit I got this, what dose it mean ?

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/xulrunner-1.9.2.22/.autoreg /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.26/.systemPrefs
it's just a warning about found hidden files, those files are normal for some applications that use hidden configuration files, you should only worry about them if you didn't actually installed the trusted application.

---

### Post by Grenage on 2011-09-08
I think that chkrookit actually causes more problems than it fixes (not that it's the app's fault).  How many 'false' positive panics have we seen, compared to actual rootkit installs?

---

### Post by jbalazs on 2011-09-08
Thanks for the info my friends

---

### Post by j*tech on 2011-09-08
Ya, your good, those 2 always pop up on my scans...

---

