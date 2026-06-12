---
title: "Installing WTK in Ubuntu"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by anapob on 2009-10-19
Hey guys, i wanted to install WTK to develop mobile apps , but i seem to face a bit of problem installing it my system.

1 ] I installed netbeans [6.5] from synaptic. [sudo apt-get install netbeans]
2 ] I had to install WTK for programming J2ME apps.
3 ] I downloaded the file from sun's website. [version 2.5.1]
4 ] When i tried to install it , it gives me a error saying "no suitable java interpreter found"

```
Enter a path to the Java 2 SDK: /usr/lib/jvm/java-6-sun/bin    
/usr/lib/jvm/java-6-sun/bin/java
Testing /usr/lib/jvm/java-6-sun/bin/java...
Exception in thread "main" java.lang.ClassFormatError: Extra bytes at the end of class file com/sun/kvem/environment/JavaVersionTester
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.sun.kvem.environment.JavaVersionTester.  Program will exit.
/usr/lib/jvm/java-6-sun/bin is not a suitable Java interpreter
Enter a path to a Java 2 SDK (For example: /user/jdk1.4/bin). You can type "exit" to cancel installation.

```

5 ] i tried searching in many forums and found that the problem had been solved in their cases by changing the interpreter directory[:confused:]

i tried it 
```
sudo update-alternatives --config java
```
and found that the path to the interpreter in my case was 
```
/usr/lib/jvm/java-6-sun/jre/bin/java
```

i did use that path but the error seems to be happening even in this case.

Does having multiple interpreters cause the problems , i did try with just the sun-6-java and no openjdk but the problem was still there, Are there any workarounds for this.

---

### Post by Hospadar on 2009-10-19
do you have the jdk installed?
I think it's sun-java6-jdk

---

### Post by anapob on 2009-10-20
Yes i have installed sun-java6-jdk + sun-java6-jre.

The output of my  

```
update-alternatives --config java
```

is

```
 Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java

```

should i change me selection or using java6-sun is fine

i tried using 4 , but i got error saying its not a suitable interpreter

```
Enter a path to the Java 2 SDK: /usr/lib/jvm/java-gcj/bin         
/usr/lib/jvm/java-gcj/bin/java
Testing /usr/lib/jvm/java-gcj/bin/java...
Exception in thread "main" java.lang.ClassFormatError: com.sun.kvem.environment.JavaVersionTester (unused data before end of file)
   at java.lang.VMClassLoader.defineClass(libgcj.so.90)
   at java.lang.ClassLoader.defineClass(libgcj.so.90)
   at java.security.SecureClassLoader.defineClass(libgcj.so.90)
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)
/usr/lib/jvm/java-gcj/bin is not a suitable Java interpreter
```

---

### Post by anapob on 2009-10-20
Its my bad, The version i was using was 2.2 which had problemss [checked in many forums] , i executed the 2.5 version and it is solved now.



Thanx :)

---

