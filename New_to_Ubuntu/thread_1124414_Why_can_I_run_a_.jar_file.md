---
title: "Why can I run a .jar file?????"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by tekkieguy on 2009-04-13
I get this code when trying to run Vuze from the .jar
and yes, i know that there is the other way, but there are other .jar archives and i want to load them this is what i get ```
montel@montel-linux:~/vuze$ java -jar v.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLine
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: org.gudy.azureus2.ui.common.Main. Program will exit.

```

---

### Post by Hospadar on 2009-04-13
What JRE (java runtime environment) are you using?  And where are the installation/running instructions for vuze so that we might scrutinize them?

java -version

will tell you your version and jre

---

### Post by miegiel on 2009-04-13
I had some problems running vuze because I was using the wrong java version. If that's not it, I have no idea what might be wrong.

---

### Post by tekkieguy on 2009-04-13
```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu6)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

```


That is what it gave me.

---

### Post by miegiel on 2009-04-13
I'm using :
```
:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)
```

That's in 64bit ubuntu hardy, running vuze 4.2.0.2 64bit

---

### Post by Hospadar on 2009-04-13
if you "sudo apt-get install sun-java6-jdk" it'll install all the java stuff you might need most likely.

If after you install the sun version of the jre (as above), if you run java -version and still it tells you that you're using OpenJDK, you can switch with "sudo update-alternatives --config java" and select sun's java

---

### Post by tekkieguy on 2009-04-13
Do you know of like an .jar program that I can download to test that it works?
Like anything?

---

### Post by Malta paul on 2009-04-13
Yes try [http://sourceforge.net/projects/stripper](http://sourceforge.net/projects/stripper)
Works great. or you could try [http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)
Java version.
Have fun ;)

---

### Post by tekkieguy on 2009-04-13
Thanks a lot [Malta paul]("http://ubuntuforums.org/member.php?u=166032"). It worked great, must be vuze.

---

