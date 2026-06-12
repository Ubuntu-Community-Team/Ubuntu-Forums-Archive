---
title: "E: Unable to locate package"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by ittakesmoxie on 2011-07-30
When I try to install  packages I get this message  E: Unable to locate package <package>

---

### Post by scorchgeek on 2011-07-30
That error usually means that you typed the name of a package that doesn't exist.

Where are you trying to install a package from? What package are you trying to install?

---

### Post by ittakesmoxie on 2011-07-30
it is a financial package called gfp .  I downloaded it from source forge

---

### Post by ubudog on 2011-07-30
Ah, in this case, you must install it using the following commands, not with apt-get.

First, open a terminal (Konsole in Kubuntu I believe) and do this:
```
cd gfp
``` 
(or wherever you extracted it)

Next, to install, do:
```
./configure && make && sudo make install
```

You may have to enter your password once, it will be blank.
Let us know if you have any problems.  :-)

---

### Post by scorchgeek on 2011-07-30
I'm going to assume, since you didn't say this, that you were trying to use the 'apt-get install' command to install the software. That command is only for installing software that's in the Ubuntu software repository (you haven't downloaded it yet). Since GFP is not in the repository, the package manager can't locate the package you specified.

Also, this package is not a Debian package (the kind you get from the repository), it's a JAR package (written in Java). Normally you can simply run this file directly. I'm trying to get it to run, and I can't on my system, so I'll get back to you in a minute when I do.

---

### Post by ubudog on 2011-07-30
Correct; if it is a Java file, all you have to do is:
Open a terminal, and type the following:
```
java gfp.jar <enter>
```

---

### Post by scorchgeek on 2011-07-30
It appears the software you're trying to use is configured incorrectly. It also appears that the latest revision of the software was six years ago.

Is there some reason you urgently must use this software in particular? What are you trying to do with this software? There's probably some more mainstream software that you could use--maybe I could suggest a package for you.

EDIT: (Response to ubudog)

This is what I get when I try that:
```
Exception in thread "main" java.lang.NoClassDefFoundError: //gfp_0/5/5-20051213_src/jar
Caused by: java.lang.ClassNotFoundException: ..gfp_0.5.5-20051213_src.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: ./gfp_0.5.5-20051213_src.jar. Program will exit.
```

Thus I recommend trying some other software, rather than try to debug this package.

---

### Post by ittakesmoxie on 2011-07-30
> **ubudog said:**
> Correct; if it is a Java file, all you have to do is:
Open a terminal, and type the following:
```
java gfp.jar <enter>
```


I did this command and this is what came back
Exception in thread "main" java.lang.NoClassDefFoundError: gfp/jar
Caused by: java.lang.ClassNotFoundException: gfp.jar
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: gfp.jar. Program will exit.

---

### Post by scorchgeek on 2011-07-30
Like I said, it appears that the software is damaged or improperly configured, or it might just be that it's so old it no longer works with current versions of Java.

Is it possible that you might be able to use some other software? What does this package do? Ubuntu probably has a different package that would work well for you.

EDIT: Also, please use [ CODE ] tags when posting output of a command. Just click the little hash mark button and paste your text between the tags.

---

### Post by ubudog on 2011-07-30
> **scorchgeek said:**
> Like I said, it appears that the software is damaged or improperly configured, or it might just be that it's so old it no longer works with current versions of Java.

Is it possible that you might be able to use some other software? What does this package do? Ubuntu probably has a different package that would work well for you.

EDIT: Also, please use [ CODE ] tags when posting output of a command. Just click the little hash mark button and paste your text between the tags.

+1

gfp seems a little outdated.  I recommend gnucash, it's up to date and useful.  It can be installed like this:
```
sudo apt-get install gnucash
```

That's it.  It should be in the menu.

---

### Post by ittakesmoxie on 2011-07-30
[QUOTE=scorchgeek;11102992]Like I said, it appears that the software is damaged or improperly configured, or it might just be that it's so old it no longer works with current versions of Java.

I tried the command with another package and this is what came back from it

```
jeffrey@jeffrey-MS-7037:~$ java dsbudget.jar
Exception in thread "main" java.lang.NoClassDefFoundError: dsbudget/jar
Caused by: java.lang.ClassNotFoundException: dsbudget.jar
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: dsbudget.jar. Program will exit
```.

---

### Post by scorchgeek on 2011-07-30
It seems to me that this software is not going to work at all. Could you please answer the questions I have asked you so that we could suggest another package for you?

Is it possible that you might be able to use some other software? What are you trying to do with the software? Ubuntu probably has a different package that would work well for you.

Also, going off some assumptions about what you are trying to do, I might suggest that you try GnuCash--ubudog has already posted complete instructions for how to install it.

---

### Post by ittakesmoxie on 2011-07-30
> **scorchgeek said:**
> It seems to me that this software is not going to work at all. Could you please answer the questions I have asked you so that we could suggest another package for you?

Is it possible that you might be able to use some other software? What are you trying to do with the software? Ubuntu probably has a different package that would work well for you.

Also, going off some assumptions about what you are trying to do, I might suggest that you try GnuCash--ubudog has already posted complete instructions for how to install it.
I have already installed several other packages Gnu Cash kmymoney grisbi homebank.
kmymoney keeps crashing on me also when I try to change the sort order of the transactions it won't let me do it etc... gnucash has similar issues I want a program that lets me change the sort order of the transactions and allows me to enter the transactions directly into the register it needs to be able to create a budget  and not crash whenever it feels like it. 

I would like to say that I tried the java <program>.jar command on two different programs and got similar results that came back it seems to me that maybe the problem is something else besides the programs

---

### Post by scorchgeek on 2011-07-30
GnuCash supports sorting--choose View --> Sort By. As for instability, I've never had it crash on me.

Those packages are set up incorrectly, and fixing them would require debugging the programs, a task which I am certainly not up for, and I don't think you are either. I don't think the problem is with something else, because I can run another jar file just fine using the method we had you use, and the same package file that fails on yours fails on mine. If you really think neither GnuCash or some other package you've tried will serve your needs at all, I'm afraid you're going to have to keep looking.

---

### Post by ittakesmoxie on 2011-07-30
Hey thanks for all your help!!!

---

### Post by ubudog on 2011-07-30
Have you tried TurboCash?

[http://turbocash.net/](http://turbocash.net/)

---

### Post by ubudog on 2011-07-31
There might be a way to get gfp running.  Try this:
```
./gfp.jar
```

---

