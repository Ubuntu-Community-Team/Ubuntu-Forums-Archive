---
title: "Frostwire will not load"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by crazylepew on 2009-07-26
frostwire will download but when i open the program i get.

FrostWire version 4.17
Java version 1.6.0_14 from Sun Microsystems Inc.
Linux v. 2.6.28-13-generic on i386
Free/total memory: 44778712/47841280

java.lang.NoClassDefFoundError: com/google/inject/Module
    at com.limegroup.gnutella.gui.Initializer.createLimeWire(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: com.google.inject.Module
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 8 more

STARTUP ERROR!

i checked and i have the latest sun java installed HELP!!

---

### Post by mikechant on 2009-07-27
This thread on the frostwire forums
[http://forum.frostwire.com/viewtopic.php?t=6241&f=1](http://forum.frostwire.com/viewtopic.php?t=6241&f=1)
has some posts near the end which claim to get around this problem.

---

### Post by Soul-Sing on 2009-07-27
```
sudo update-alternatives --config java
```

Use the sun java, or set it as "active".

---

