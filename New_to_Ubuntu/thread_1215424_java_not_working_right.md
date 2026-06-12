---
title: "java not working right?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Defrector on 2009-07-17
I've been programming in java for years in ubuntu but came across a snag on a new install using xubuntu 9.04 and I can't figure out what is causing it:

> $ cat Test4.java
public class Test4
{
public static void main(String[] args)
 {
 System.out.println("test");
 }
} //end

$ javac Test4.java
$ java Test4

Exception in thread "main" java.lang.NoClassDefFoundError: Test4
Caused by: java.lang.ClassNotFoundException: Test4
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: Test4.  Program will exit.

$ java -version

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

...this error occurs when attempting to run any class files. I confirm that Test4.class is present in the current directory. Any ideas as to why java cannot see the class?

---

### Post by diwas on 2009-07-17
Same thing happens to me. Even a simple program doesnt compile or executes idk what's the matter.

I have to open XP for all of my Java stuffs. :@:@

---

### Post by diwas on 2009-07-17
BTW do u have javac in 
/bin/sh
?

I currently dont have Ubuntu so cannot say anything abt it.

---

### Post by Defrector on 2009-07-17
I don't quite understand the /bin/sh question; my /bin/sh is an executable. But here is some more info:

```
$ locate javac
/etc/alternatives/javac
/etc/alternatives/javac.1.gz
/usr/bin/javac
/usr/lib/jvm/java-6-sun-1.6.0.14/bin/javac
/usr/lib/jvm/java-6-sun-1.6.0.14/man/ja/man1/javac.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.14/man/man1/javac.1.gz
/usr/share/man/man1/javac.1.gz
/usr/share/vim/vim72/compiler/javac.vim
/usr/share/vim/vim72/syntax/javacc.vim
/var/lib/dpkg/alternatives/javac
```

```
$ echo $PATH
/usr/share/java:$/usr/share/java:$/usr/share/java:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

UPDATE: Cleaned up path:
```
$ echo $PATH
/usr/share/java:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

... No improvement.

Here is more info again:
```
$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

---

### Post by kpkeerthi on 2009-07-17
In the folder where your Test4.class exists, run this command:
```

java -cp . Test4

```

The -cp switch will direct the java vm to look for class files in the specified folder, which in our case is . (dot)

. refers to current folder. You may replace . with absolution path of the folder where your class files are located. Google **java classpath** for more

---

### Post by Defrector on 2009-07-17
It works!!! :KS

Using Eclipse in the past has made me forget. Thanks much!


[SOLVED]

---

### Post by The Cog on 2009-07-17
Good. 

That means there must be a CLASSPATH defined in your environment somewhere. I would be inclined to find where that gets set and remove it. It is not normally needed, and as you found, can sometimes cause problems.

---

