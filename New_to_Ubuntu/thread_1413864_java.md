---
title: "java"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by patchido on 2010-02-23
how can i find out where is the java's jdk home directory and also the bin directory?

---

### Post by theDaveTheRave on 2010-02-23
patchido,

try

```

locate jdk |more

```

that will throw out all occurances of 'jdk' in the directory tree, the purpose of doing the '|more' is that you will then get the info 1 page at a time.

You could probably also do 
```

locate jdk | grep 'etc'

```

Otherwise I think what you really want is to know what the path is to the JVM

depending on your default shell, I assume you are using the standard 'bash' shell, the following will give you the info you are after.

```

more .bash_profile

```

I hope that generally answers you question.

this [link]("http://osdir.com/ml/lang.jython.user/2003-04/msg00074.html") should give you more details.

I've also attached a short file on adding stuff to the classpath etc on system. have fun...

David

---

### Post by The Cog on 2010-02-23
The command **which java** or **which javac** will tell you which one is in your path. But that's likely to be a symlink so then do file <filename> to see where it links to. Then keep doin file <filename> until you reach a non-symlink file. Like this:
> steve@StevesPC:~$ which java
/usr/local/bin/java
steve@StevesPC:~$ file /usr/local/bin/java
/usr/local/bin/java: symbolic link to `/opt/jdk1.6.0_18/jre/bin/java'
steve@StevesPC:~$ file /opt/jdk1.6.0_18/jre/bin/java
/opt/jdk1.6.0_18/jre/bin/java: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, not stripped


---

