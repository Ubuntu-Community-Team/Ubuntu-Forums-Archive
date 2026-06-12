---
title: "GCALdaemon throws Java exception when starting...trying to sync Google Calendar"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-05-03
Hi, all:

I'm getting an exception when I try to start GCALdaemon from the command line.  Here's the error:

~ : Yes, Supreme Empress? $ cd /usr/local/sbin/GCALDaemon/bin
/usr/local/sbin/GCALDaemon/bin : Yes, Supreme Empress? $ ./standalone-start.sh
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/log4j/Layout
        at org.gcaldaemon.standalone.Main.main(Main.java:66)
Caused by: java.lang.ClassNotFoundException: org.apache.log4j.Layout
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
        ... 1 more

I have Java 1.6 installed; is this a problem with Apache, and if so, what packages do I need to install to resolve the exception?

Thanks!

---

### Post by tarahmarie on 2009-05-04
bump

---

### Post by amadib on 2010-03-11
were you able to figure this out?

---

