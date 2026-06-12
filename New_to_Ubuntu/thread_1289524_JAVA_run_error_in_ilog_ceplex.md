---
title: "JAVA run error in ilog ceplex"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by eman99 on 2009-10-12
Hi All,
I am installing Ilog ceplex and planning to use the JAVA concert technology. so when I compile the java file (name: LPex1.java, saved under my home directory not the usr one) I have no problem but when I try to run it I got some errors related to the library.
 
 
The LPex1.java under my home directory
 
the ilog folder is under the /usr/local folder which has the .jar file in the library at the mintioned path
they are in different directories so if I want to run the LPex1 should I save it under the /usr/local directory!
 
the following was the way that I got from the ilogcplex tutorial to run java:
 
eman@eman-laptop:~$ javac -classpath /usr/local/ilog/cplex90/lib/cplex.jar LPex1.java
eman@eman-laptop:~$ java -Djava.library.path=/usr/local/ilog/cplex90/bin/i86_linux2_glibc2.3_gcc3.2 LPex1Exception in thread "main" java.lang.NoClassDefFoundError: LPex1
at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: LPex1 not found in gnu.gcj.runtime.SystemClassLoader{urls=[[[COLOR=#0033aa]file:/usr/local/ilog/cplex90/lib/cplex.jar[/COLOR]]("file:///usr/local/ilog/cplex90/lib/cplex.jar")], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
at java.net.URLClassLoader.findClass(libgcj.so.90)
at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
at java.lang.ClassLoader.loadClass(libgcj.so.90)
at java.lang.ClassLoader.loadClass(libgcj.so.90)
at gnu.java.lang.MainThread.run(libgcj.so.90)
 
Please help me get this file run!

---

### Post by Mighty_Joe on 2009-10-12
> **eman99 said:**
> 
eman@eman-laptop:~$ java -Djava.library.path=/usr/local/ilog/cplex90/bin/i86_linux2_glibc2.3_gcc3.2 LPex1
Exception in thread "main" java.lang.NoClassDefFoundError: LPex1


You have to specify the classpath at runtime too, and include the directory LPex1.class is in.

---

### Post by eman99 on 2009-10-12
thank you for your replay, but can you give me the complete command since I am not familier with the advance command in linux.

---

### Post by Mighty_Joe on 2009-10-13
You used the classpath flag when you compiled.  Use it again when you run:

```
java -classpath /usr/local/ilog/cplex90/lib/cplex.jar:. -Djava.library.path=/usr/local/ilog/cplex90/bin/i86_linux2_glibc2.3_gcc3.2 LPex1
```

Note I added the current directory "." to the classpath to pick up your LPex1.class file.

---

### Post by eman99 on 2009-10-13
Thanks alot, you are genius,,, it works! :)

---

