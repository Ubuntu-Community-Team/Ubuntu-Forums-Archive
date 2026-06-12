---
title: "unable to start frostwire"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by lunaz on 2009-05-31
it's been a while since i've used this, but never remember having issue getting it to start.

i tried using the sun-java 5 and 6 packages, both give me this error:

is this package broken now or is there a fix?

```
FrostWire version 4.17
Java version 1.6.0_07 from Sun Microsystems Inc.
Linux v. 2.6.24-24-generic on i386
Free/total memory: 4499752/5177344

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.limewire.util.VersionUtils
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 6 more

STARTUP ERROR!
```

---

### Post by lunaz on 2009-06-03
update: i was able to get frostwire installed using the method here:
[http://forum.frostwire.com/viewtopic.php?f=1&t=6241#p23108](http://forum.frostwire.com/viewtopic.php?f=1&t=6241#p23108)

but every time i restart frostwire, i have to redo the configs.

---

