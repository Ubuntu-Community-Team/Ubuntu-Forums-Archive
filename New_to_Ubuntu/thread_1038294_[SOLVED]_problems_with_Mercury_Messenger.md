---
title: "[SOLVED] problems with Mercury Messenger"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by tekne on 2009-01-12
Hello, i am running Ubuntu 8.10 and am a linux user for the first time. Though i've been able to fix some of the obstacles i've been having, i can't seem to find the problem with this one and i hope you can help :)

i installed mercury messenger through the console, where i wrote

sudo apt-get install mercury

everything seemed to be fine, because the installation went out perfectly.

but every time i try to run it, it's always missing some lib files which i cannot understand why:

```
...:~$ mercury
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-6-openjdk/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```


thanks for reading and i hope you can teach me the solution :)

---

### Post by jimmy the saint on 2009-01-12
open up add/remove and type in "java"
the Sun Java 6 Runtime app should show up at the top.  Is the box next to it checked?  If not, check it and press the "apply changes" button.  This will install the java runtime environment.  Since the messenger app you want is a java app, Java must be installed first.

---

### Post by HotShotDJ on 2009-01-12
> **tekne said:**
> thanks for reading and i hope you can teach me the solution :)Looks to me like a java error.  Have you installed sun-java6 from the repositories?  If not, you can do so using Applications --> Add/Remove... and selecting "Sun java 6 Runtime and Sun Java 6.0 Plugin.  OR, to get Sun Java 6 AND a bunch of other good stuff, install Ubuntu Restricted Extras, which will get the Java for you, plus Adobe Flash, MP3, AVI, etc. support.

---

### Post by jimmy the saint on 2009-01-12
+1 for the ubuntu restricted extras.  In terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

I forgot that java was in there!

---

