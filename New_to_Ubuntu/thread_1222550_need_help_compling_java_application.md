---
title: "need help compling java application"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by kylehotchkiss on 2009-07-25
Here is an old application I found I would like to check out.
The only problem is I have no idea how to use / compile it.

It's called kinetic typography engine and it's at [http://johnnylee.net/kt/dist/](http://johnnylee.net/kt/dist/). Could anyone help me please =)

---

### Post by MadViper on 2009-07-25
I believe ubuntu has everything you need already built in. just download the .java file, open the terminal and navigate to the folder that you downloaded the java files. first you'll need to compile it so type javac NameOfFile.java, if it doesn't have errors your next set is simply to type java NameOfFile. You should be good to go, but if it doesn't work explain back what happened and i'll try to help you out

---

### Post by kylehotchkiss on 2009-07-25
this is kinda confusing me =/ It is a folder full of .class and .java files. It has no help and I am confused as to how to run the thing as a whole, would you mind downloading this file: [http://johnnylee.net/kt/dist/files/11-26-02/kinetic.zip](http://johnnylee.net/kt/dist/files/11-26-02/kinetic.zip) and taking a look around? As there is no makefile or any of that stuff, it's all the more confusing... does it need to be installed?

---

### Post by mthalis on 2009-07-25
First of you must install Java for you're computer, after that open terminal type javac
if it works you successfully install Java
Next you must fine main method in you're project then you compile that Java file and run it.
> javac test.java
java test

---

### Post by kylehotchkiss on 2009-07-25
When I try to compile the .java files (any of them) I get:
```
Note: KTEdit.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
24 errors

```

and when I try to run the already existing .class files  I get

```
xception in thread "main" java.lang.NoClassDefFoundError: KTEdit (wrong name: KTEditor/KTEdit)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: KTEdit. Program will exit.

```


this software was written in 2002 btw.

---

### Post by mthalis on 2009-07-25
Are you sure you're program is correct(no file missing)?

---

### Post by kylehotchkiss on 2009-07-25
Well it was written in 2002, poorly documented and there is nothing else about it on the internet. guess that's a lost cause lol!

---

### Post by MadViper on 2009-07-25
Yeah, i'm going to agree with mthalis on this one. It seems like the the main class is missing

---

### Post by nomarior on 2009-08-13
If the main class could not be found, then there is a problem with the path to that main class. 

kylehotchkiss 's example looks as if he didn't take the package directory into account. Anyhow, with all classes including the class with the main routine, its fairly easy to pack everthing in a jar file.

The only main class I found was in the KT_Test.zip archive. From that I generated a jar file which is trivial to run:

java -jar kt_test.jar

And it does start (haven't tested anything more though). 

I know that already 2 weeks passed and it's most likely not of interest anylonger, but if anyone wants to try it, drop me a p.m.

Cheers

---

