---
title: "chkrootkit suspicious file question"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-11-23
When running chkrootkit, the following came up:

> Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/firefox-3.6.12/.autoreg /usr/lib/xulrunner-1.9.2.12/.autoreg /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.22/.systemPrefs /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/thunderbird-3.1.6/.autoreg


Is this normal or should I be worried about something?

---

### Post by DogMatix on 2010-11-23
Most probably false positives.

Read this thread: [http://ubuntuforums.org/showthread.php?t=1544017](http://ubuntuforums.org/showthread.php?t=1544017)

---

### Post by twizler on 2011-03-18
I have the same version of ubuntu and also found the /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/xulrunner-1.9.2.12/.autoreg /usr/lib/firefox-3.6.12/.autoreg /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.22/.systemPrefs

Searching for suspicious files and dirs, it may take a while... 

I would agree most likely a false positive.

(or we have the same root kit installed)

---

