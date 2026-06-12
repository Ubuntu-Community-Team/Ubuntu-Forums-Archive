---
title: "I can't install gnu-crypto library"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by benaddi on 2009-10-27
Hi,
I want to install gnu-crypto library in my pc.
I downloaded the package from the web site [http://www.gnu.org/software/gnu-crypto/](http://www.gnu.org/software/gnu-crypto/).
Then i extracted it.
After i wanted to install this package using the following commands ./configure -> make -> make install.
 When i launched ./configure, i got the following result:
[B][I]assouma@assouma-laptop:~/Téléchargement/gnu-crypto-2.1.0$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
You have no CLASSPATH, I hope it is good
checking for jikes... no
checking for javac... javac
checking if javac works... yes
checking for kaffe... no
checking for java... java
checking for uudecode... yes
checking if uudecode can decode base 64 file... yes
checking if java works... configure: error: The Java VM java failed (see config.log, check the CLASSPATH?)
[/I][/B]
I trayed to inderstand the cause with the config.log file, so i had this cause:
[I][B]configure:2295: checking if java works
configure:2328: java  Test
Exception in thread "main" java.lang.NoClassDefFoundError: Test
Caused by: java.lang.ClassNotFoundException: Test
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: Test. Program will exit.
configure:2331: $? = 1
configure: failed program was:
/* [#]line 2305 "configure" */
public class Test {
public static void main (String args[]) {
    System.exit (0);
} }
configure:2337: error: The Java VM java failed (see config.log, check the CLASSPATH?)
[/B][/I]
So any one please suggest how i can install this package.
 
Thanks & Regards,
Asma

---

### Post by bribera on 2009-10-27
Does your config.log list the CLASSPATH anywhere?

There's a similar bug in the Gentoo forums that pins this error message on a misconfigured CLASSPATH; it would be helpful if you could post what yours was during the build.

[http://bugs.gentoo.org/show_bug.cgi?id=88538#c9](http://bugs.gentoo.org/show_bug.cgi?id=88538#c9)

---

