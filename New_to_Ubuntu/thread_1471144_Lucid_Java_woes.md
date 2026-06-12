---
title: "Lucid Java woes"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by maphilli14 on 2010-05-03
I'm normally fairly savvy at finding answers, but I'm stumped by this one.

Java via CLI works (EG Sikuli)
Javaplugin via [How do I test whether Java is working on my computer? works and reports]("http://java.com/en/download/help/testvm.xml")

```
Your Java configuration is as follows:  Vendor: Sun Microsystems Inc. Version: Java 6 Update 20 Operating System: Linux 2.6.32-21-generic-pae Architecture: i386
```

However, using Cisco's WebEx Meetings doesn't!  It pops a java window via the plugin I think and to simulate it I went here:

[http://www.javatester.org/version.html]("http://www.javatester.org/version.html")

Here I get the following things listed in the console


```
load: class JavaVersionDisplayApplet.class not found.
java.lang.ClassNotFoundException: JavaVersionDisplayApplet.class
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:219)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
Caused by: java.io.IOException: open HTTP connection failed:http://www.javatester.org/JavaVersionDisplayApplet/class.class
	... 6 more
Exception: java.lang.ClassNotFoundException: JavaVersionDisplayApplet.class
load: class JavaVersionDisplayApplet.class not found.
```

I've tried different plugins from OpenJDK to Sun's to icedtea etc... via 

```
sudo update-alternatives --config java
```

nothing!

Please help!

---

### Post by lunatico on 2010-05-05
I just tested this and it worked for me.

I installed 10.04 32-bit on a Virtualbox VM.

Then I installed sun-java6-plugin and all its dependencies. Launched Cisco Webex Meetings in Firefox, and created an immediate meeting and it loaded the proper sun java plugin and it all worked.

Firefox 3.6.3
Java Plugin 1.6.0_20

```
~$ update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.
```

I then installed Chromium from daily repositories, launched Webex Meetings and it also worked fine.

Maybe you have too many java options installed and they're conflicting.

---

### Post by philinux on 2010-05-05
See the sticky in General Help re Lucid.

---

### Post by maphilli14 on 2010-05-06
I think I'm getting to the bottom of this:

[http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=195](http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=195)

---

