---
title: "Help me to run .JAR"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Mr.TAEL on 2010-05-01
Hey,

I want to run a JAR package. I'm using Ubuntu 10.04 with OpenJDK Java 6 Runtime/Web Start installed.

This is my JAR : [http://dl.free.fr/pfvUO2S4U](http://dl.free.fr/pfvUO2S4U)

Thanks a lot.

---

### Post by -Robert- on 2010-05-01
This should work: [http://ubuntuforums.org/showthread.php?t=281932](http://ubuntuforums.org/showthread.php?t=281932)

---

### Post by Mr.TAEL on 2010-05-01
> **-Robert- said:**
> This should work: [http://ubuntuforums.org/showthread.php?t=281932](http://ubuntuforums.org/showthread.php?t=281932)
I tried it. When I enter "java -jar ....", It says "Properties?". Also I entered "java ..." and it says:
```

Exception in thread "main" java.lang.NoClassDefFoundError: APJP/jar
Caused by: java.lang.ClassNotFoundException: APJP.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: APJP.jar. Program will exit.

```

---

### Post by Mr.TAEL on 2010-05-02
Bump! :rolleyes:

---

### Post by mechro on 2010-05-02
I think you're missing some files for this to run. There is a "PROPERTIES" file that needs configuring.

Does this link help?...

[http://code.google.com/p/apjp/downloads/list](http://code.google.com/p/apjp/downloads/list)

---

