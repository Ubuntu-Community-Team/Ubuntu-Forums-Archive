---
title: "java library path problem"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by 007casper on 2009-05-12
I am trying to launch an application.  It used to work, after restarting the computer, I have tried to launch the app... this is what I get in the log.

The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.13/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib


In the terminal I wrote

rex@pary:~$ ls -l /usr/lib/jvm
total 12
drwxr-xr-x 7 root root 4096 2009-01-03 23:02 java-1.5.0-gcj-4.3-1.5.0.0
lrwxrwxrwx 1 root root   23 2009-05-06 15:30 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.18
drwxr-xr-x 6 root root 4096 2009-05-06 15:30 java-1.5.0-sun-1.5.0.18
lrwxrwxrwx 1 root root   19 2009-05-06 15:30 java-6-sun -> java-6-sun-1.6.0.13
drwxr-xr-x 8 root root 4096 2009-05-06 15:30 java-6-sun-1.6.0.13
lrwxrwxrwx 1 root root   26 2009-01-03 23:01 java-gcj -> java-1.5.0-gcj-4.3-1.5.0.0


under ~/.bashrc on the last line I have 

#Java
export JAVA_HOME=/usr/lib/jvm/java-6-sun

I dont understand what is going on?  Is something corrupt?:(

Please, help

Thank you.

---

### Post by spiderbatdad on 2009-05-12
try adding this below your other entry```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jvm/java-6-sun
```

---

### Post by 007casper on 2009-05-12
I am new at this.

You mean under ~/.bashrc right after 

#Java
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jvm/java-6-sun


Is that right?

Thank you

---

### Post by spiderbatdad on 2009-05-12
indeed.

---

### Post by spiderbatdad on 2009-05-12
see next post...lol

---

### Post by spiderbatdad on 2009-05-12
What I have found on that error is this:
It means that the APR lib is not installed. You can install it via:


    ```
sudo apt-get install libtcnative-1
```
Restart server.

[http://michael.smyers.net/?p=70](http://michael.smyers.net/?p=70)

---

### Post by 007casper on 2009-05-12
rex@pary:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory

I tried 
#Java
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jvm/java-6-sun

I still got errors.  

Initializing Spring root WebApplicationContext
21:38:17,083 ERROR [ContextLoader:220] Context initialization failed
java.lang.StackOverflowError

It used to work before.  I wonder what the problem could be...

---

### Post by 007casper on 2009-05-12
I just installed libtcnative-1 with synaptic package manager

---

### Post by 007casper on 2009-05-12
it was a path problem, I just had to fix the path for tomcat... now the application launches but I am still getting the same thing in the log file

INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.13/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib

???

by the way I uninstall libtcnative-1 because it was giving me fail to connect

---

