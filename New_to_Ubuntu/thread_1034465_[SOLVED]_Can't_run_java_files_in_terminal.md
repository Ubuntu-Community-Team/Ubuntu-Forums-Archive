---
title: "[SOLVED] Can't run java files in terminal"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by pipyui on 2009-01-08
Bear with me, for I'm a n00b to linux.

For some  reason, I can't run my java class files in terminal.

**My Java code:**
```
public class HelloWorld{
	public static void main(String args[]){
		System.out.println("Hello, World!");
	}
}
```

**My terminal commands:**
```
alex@alex-netbook:~$ javac ~/Java/HelloWorld.java
alex@alex-netbook:~$ java ~/Java/HelloWorld.class
Exception in thread "main" java.lang.NoClassDefFoundError: /home/alex/Java/HelloWorld/class
Caused by: java.lang.ClassNotFoundException: .home.alex.Java.HelloWorld.class
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: /home/alex/Java/HelloWorld.class. Program will exit.

```

I DON'T KNOW WHAT'S WRONG! Did I make a stupid error somewhere? Did I call "java" wrong? Please help!

---

### Post by TVTrukChik on 2009-01-08
Just type "java HelloWorld" without the .class on the end of it.

---

### Post by lovelyvik293 on 2009-01-08
You don't have to use the ".class" when you are running or interpreting the java program.

---

### Post by Vantrax on 2009-01-08
If this is solved (and it appears so) please mark the thread as solved.

---

### Post by pipyui on 2009-01-08
Thanks for your help.
Not only did I have to remove the ".class", I also had to be in the directory I was accessing. (e.i. alex@alex-netbook:~/Java$ java HelloWorld)

---

