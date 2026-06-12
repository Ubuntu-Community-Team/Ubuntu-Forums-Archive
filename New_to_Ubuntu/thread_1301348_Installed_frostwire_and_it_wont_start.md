---
title: "Installed frostwire and it wont start?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by segamaster222 on 2009-10-25
I installed frostwire and I go to run it and this happens 

[img]http://imgur.com/y91Nw.png[/img]

This is what it says in the box

> FrostWire version 4.17
Java version 1.6.0_0 from Sun Microsystems Inc.
Linux v. 2.6.28-16-generic on i386
Free/total memory: 4791368/5177344

java.lang.NoClassDefFoundError: com/google/inject/Module
	at com.limegroup.gnutella.gui.Initializer.createLimeWire(Unknown Source)
	at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: com.google.inject.Module
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 8 more

STARTUP ERROR!

Thanks.

---

### Post by segamaster222 on 2009-10-26
Uninstalled frostwire and used this deb 

[http://www.mediafire.com/?zenzgvyl4wa](http://www.mediafire.com/?zenzgvyl4wa)

all is good.

---

