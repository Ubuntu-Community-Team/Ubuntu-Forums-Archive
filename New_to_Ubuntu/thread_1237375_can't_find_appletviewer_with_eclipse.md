---
title: "can't find appletviewer with eclipse"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by purplearcanist on 2009-08-11
I run my java program, which is an applet, on eclipse, and I get this error:

Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/eliot/FudgeLike/src/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

How do I get the applet viewer to work with eclipse?

I am using the newest version of eclipse.

---

### Post by Dark Aspect on 2009-08-11
To run an applet, make sure the current project is still selected. Then select the menu option Run->Run as...->Java Applet. Eclipse will show a applet viewer and I believe you can launch your Java applet from that.

---

### Post by purplearcanist on 2009-08-11
> **Dark Aspect said:**
> To run an applet, make sure the current project is still selected. Then select the menu option Run->Run as...->Java Applet. Eclipse will show a applet viewer and I believe you can launch your Java applet from that.

I did that, it comes up with the error though.  I need to figure out how to fix it.

---

### Post by purplearcanist on 2009-08-11
tap?

---

### Post by purplearcanist on 2009-08-11
I fixed it, and it works fine:

[http://ubuntuforums.org/showthread.php?t=274141](http://ubuntuforums.org/showthread.php?t=274141)

---

