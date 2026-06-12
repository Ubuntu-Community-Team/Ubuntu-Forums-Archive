---
title: "Issue in setting Java path"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by dilantha on 2011-01-13
Hi All,

Really sorry for re-posting the topic again. provided solutions for the previous threads didn't work for me. Im just trying to compile and run a simple java program (test.java). But it gives me below error all the time when i tried to run it (java test).
```

 Exception in thread "main" java.lang.NoClassDefFoundError: test
Caused by: java.lang.ClassNotFoundException: test
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: test.  Program will exit.


```when i used 
```

 java -classpath . test

```Then it worked perfectly fine. I went through the previous threads and set the class path accordingly but still the situation same. Here is my environment file

```

 PATH="/usr/lib/jvm/java-6-sun/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
CLASSPATH="/usr/lib/jvm/java-6-sun/lib:."

```

Can any one help me to figure out the isse ? Thanks in advance..

---

### Post by dileepm on 2011-01-25
You dont need . in PATH and remove entire CLASSPATH and retest. To run a simple java program PATH and JAVA_HOME is more than enough. The 'java' would recognize the lib folder by itself, its relative path.

---

