---
title: "Exception in thread &quot;main&quot; java.lang.NoClassDefFoundError:"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by tonybraganza37 on 2011-09-02
i have installed the java jdk from software center of  ubuntu ,am unable to run the java programs even though javac is working program is compiled ,am getting message like 


Exception in thread "main" java.lang.NoClassDefFoundError: main
Caused by: java.lang.ClassNotFoundException: main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: main. Program will exit.

help me out for this ,where did have made mistake for this type error

---

### Post by rathin.saran on 2011-09-02
Try using the following command :

java -classpath . <your_program_name>

If the above command solves the issue you need to add the current folder to the classpath variable.

To set the classpath variable you might try the following

CLASSPATH=$CLASSPATH:.
export CLASSPATH

---

### Post by Kelvari on 2011-09-03
Actually, if you do ```
echo $CLASSPATH
``` you end up with a blank line. I'm trying to figure out how to set a classpath myself, to be honest, as I need a specific .jar file (provided by the instructor) to be able to do my assignments in school.

---

