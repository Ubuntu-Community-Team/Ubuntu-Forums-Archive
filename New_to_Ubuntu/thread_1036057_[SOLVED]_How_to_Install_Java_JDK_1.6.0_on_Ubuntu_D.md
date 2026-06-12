---
title: "[SOLVED] How to Install Java JDK 1.6.0 on Ubuntu Desktop Edition"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by phmkem on 2009-01-10
Hi all

I am a Java Developer who is new to the Linux OS Altogether and cannot figure out how to configure the JRE I Believe my error lies in the class path variable because I keep getting Class Not Found Errors also I have no clue on how to setup the Applet Plugin.

Any Help is appreciated

---

### Post by namdung on 2009-01-10
Which IDE u intend to use?

For eg, BlueJ works with Sun Java only. 
[http://www.bluej.org/](http://www.bluej.org/)

Search and install JDK (Sun or OpenJDK) in *System==>Admin==>Synaptic Package Manager*.

Pls mention specific issues, if any.

---

### Post by phmkem on 2009-01-10
I Keep getting this Error While trying to run a Framed Application I use NetBeans IDE With Sun JDK

Exception in thread "main" java.lang.NoClassDefFoundError: TestFrame
   at java.lang.Class.initializeClass(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: javax.swing.GroupLayout not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)

---

### Post by phmkem on 2009-01-12
Bump

---

### Post by binbash on 2009-01-12
> **phmkem said:**
> I Keep getting this Error While trying to run a Framed Application I use NetBeans IDE With Sun JDK

Exception in thread "main" java.lang.NoClassDefFoundError: TestFrame
   at java.lang.Class.initializeClass(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: javax.swing.GroupLayout not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)

check out those : 

[http://forums.sun.com/thread.jspa?threadID=5313035](http://forums.sun.com/thread.jspa?threadID=5313035)
[http://ubuntuforums.org/archive/index.php/t-849352.html](http://ubuntuforums.org/archive/index.php/t-849352.html)

---

### Post by phmkem on 2009-01-12
Thank you very much binbash problem is solved

---

