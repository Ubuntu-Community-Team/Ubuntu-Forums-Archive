---
title: "Java model railway interface (jmri)"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by PhilRDavies on 2009-09-25
Hi All,
 
I am trying to install JMRI on an Acer Netbook running Ubuntu 9.04 Netbook Remix.
 
I have followed the install guide "Installing JMRI on Ubuntu GNU/Linux" [http://jmri.sourceforge.net/install/Ubuntu.shtml](http://jmri.sourceforge.net/install/Ubuntu.shtml) up to point 3.2 . When I try to run ./RXTXinstall I get the following error:
 
"
Exception in thread "main" java.lang.NoClassDefFoundError: GetJavaHome
Caused by: java.lang.ClassNotFoundException: GetJavaHome
at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.java:188) (This keeps displaying as a smilie - should end one eight eight , close bracket.
at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
 
Could not find the main class: GetJavaHome. Program will exit.
 
Java not found on this computer
Please check that it is included in your path and that it is installed
your current path is displayed below
 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 
The command to change your path will most probably be:
 
PATH=/usr/lib/jvm/java-6-sun/jre/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
"
 
I downloaded sun-java6-jdk using Synaptic Package Manager and it is shown in the package manager as installed.
How do I edit the path to include "=/usr/lib/jvm/java-6-sun/jre/bin/"
Any help to get past this step would be appreciated.
 
Phil

---

### Post by SoCalWizard on 2009-10-11
I got the same error, however I'm using 8.04 Ubunto preloaded on a Dell Mini 10.  I did install the sun-java6-jdk as outlined in the installation guide but when I ran the TXTXinstall I got:

Exception in thread "main" java.lang.NoClassDefFoundError: GetJavaHome
Caused by: java.lang.ClassNotFoundException: GetJavaHome
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

Java not found on this computer
Please check that it is included in
your path and that it is installed
your current path is displayed below
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
The command to change your path will most probably be:

PATH=/usr/lib/jvm/java-6-sun/jre/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Here is what Synaptic Package Manager reports:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/sun-java6-jdk
/usr/share/doc/sun-java6-jdk/README.html
/usr/share/doc/sun-java6-jdk/README.alternatives
/usr/share/doc/sun-java6-jdk/copyright
/usr/share/doc/sun-java6-jdk/changelog.Debian.gz
/usr/share/applications
/usr/share/applications/sun-java6-jconsole.desktop
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/sun-java6-jdk
/usr/share/doc-base
/usr/share/doc-base/sun-java6-jdk-readme
/usr/share/menu
/usr/share/menu/sun-java6-jdk
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-6-sun-1.6.0.06
/usr/lib/jvm/java-6-sun-1.6.0.06/jre
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386
/usr/lib/jvm/java-6-sun-1.6.0.06/man
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/apt.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/extcheck.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/idlj.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jar.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/javac.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/javadoc.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/javah.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/javap.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jconsole.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jdb.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jhat.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jmap.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jps.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jrunscript.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jsadebugd.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jstack.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jstatd.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/native2ascii.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/rmic.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/serialver.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/wsgen.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/wsimport.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/xjc.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/appletviewer.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jarsigner.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jinfo.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/jstat.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/man1/schemagen.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/apt.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/extcheck.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/idlj.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jar.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/javac.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/javadoc.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/javah.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/javap.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jconsole.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jdb.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jhat.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jmap.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jps.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jrunscript.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jsadebugd.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jstack.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jstatd.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/native2ascii.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/rmic.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/serialver.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/wsgen.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/wsimport.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/xjc.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/appletviewer.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jarsigner.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jinfo.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/jstat.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/man/ja/man1/schemagen.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.06/bin
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/javac
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/javadoc
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/apt
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/javah
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/idlj
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jarsigner
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/java-rmi.cgi
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jar
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/xjc
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/schemagen
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/wsgen
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/wsimport
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/appletviewer
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/rmic
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/javap
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/native2ascii
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/serialver
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jps
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jstat
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jstatd
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jsadebugd
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jstack
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jmap
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jinfo
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jconsole
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jrunscript
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jhat
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/extcheck
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/jdb
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/HtmlConverter
/usr/lib/jvm/java-6-sun-1.6.0.06/include
/usr/lib/jvm/java-6-sun-1.6.0.06/include/jni.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/linux
/usr/lib/jvm/java-6-sun-1.6.0.06/include/linux/jni_md.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/linux/jawt_md.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/jvmti.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/classfile_constants.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/jawt.h
/usr/lib/jvm/java-6-sun-1.6.0.06/include/jdwpTransport.h
/usr/lib/jvm/java-6-sun-1.6.0.06/lib
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/jconsole.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/sa-jdi.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/ct.sym
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/orb.idl
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/ir.idl
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/jexec
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/dt.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/htmlconverter.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/tools.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/README.html
/usr/lib/jvm/java-6-sun-1.6.0.06/COPYRIGHT
/usr/lib/jvm/java-6-sun-1.6.0.06/LICENSE
/usr/lib/jvm/java-6-sun-1.6.0.06/THIRDPARTYLICENSEREADME.txt





Did you ever get it to work?

---

