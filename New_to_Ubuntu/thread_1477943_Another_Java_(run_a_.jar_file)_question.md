---
title: "Another Java (run a .jar file) question:"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by BertOlton on 2010-05-09
In trying to run a program called Versatile Maintenance Tracker, I've downloaded it and put the VMT_2.3.2.jar on my desktop without extracting anything.  I do have Java installed, but when I right click on the .jar file and select "Open With Sun Java 6 Runtime", all I get is VMT's copyright statement.

In a terminal I've tried the command: ```
java _jar VMT_2.3.2.jar

```
and receive the output:

Exception in thread "main" java.lang.NoClassDefFoundError: _jar
Caused by: java.lang.ClassNotFoundException: _jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: _jar.  Program will exit.

What am I doing wrong/what's gone wrong?  Btw, though I'll be upgrading soon, I'm still on 9.10.

---

### Post by r-senior on 2010-05-09
Don't you want "java -jar", rather than "java _jar"?

---

### Post by BertOlton on 2010-05-09
> **r-senior said:**
> Don't you want "java -jar", rather than "java _jar"?

Heh...that was part of the problem but correcting that, I now receive: Unable to access jarfile VMT_2.3.2.jar

---

### Post by r-senior on 2010-05-09
Are you in the right directory?

$ cd ~/Desktop
$ java -jar VMT_2.3.2.jar

or ...

$ java -jar ~/Desktop/VMT_2.3.2.jar

---

### Post by BertOlton on 2010-05-09
> **r-senior said:**
> Are you in the right directory?

$ cd ~/Desktop
$ java -jar VMT_2.3.2.jar

or ...

$ java -jar ~/Desktop/VMT_2.3.2.jar

Yes sir, I was.  Just kept getting that copyright statement, but I finally woke up enough to realize the "File" and "About" menu items were active on that window.  Clicking on "File", then entering a 'new' "input" got things running.  The program has been ready to go all along, I've just been asleep at the wheel.

My apologies for the waste of time.

---

### Post by gdonwallace on 2010-05-09
Have You tried to run with OpenJDK Java alt?  I have a couple .jar files on my machine and use OpenJDK Java 6 and I don't seem to have any problems.

---

