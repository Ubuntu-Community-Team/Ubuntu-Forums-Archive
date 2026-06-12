---
title: "Use SSL Network Extender"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by AlanAbbott on 2010-12-17
I get

This software requires Sun Java to be installed and enabled.If you are prompted to confirm the use of Java, make sure that you select 'Always' in the Confirmation message.

You might need to restart your browser before attempting to connect again.

When SNX/extender (SSL Network Extender) in invoked
it tries to run snx_install.sh and I get "The following plug-in has crashed: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
 
The JAVA i'm using is:
alan@AlanA1ubu:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu2)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

And Ubuntu is 10.10 on a 32bit machine, I tried to no avail on a 64bit machine with Ubuntu 10.04 and now 10.10

---

### Post by cariboo on 2010-12-18
Have you installed Sun java instead, it's in the partner repositories. If you have all the repositories enabled, you should be able to install it using Synaptic, by searching for:

```
sun-java
```

---

### Post by AlanAbbott on 2010-12-26
My problem is that I get "The following plug-in has crashed: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
This is a part of JAVA.
May be this is not the correct place to post this.

---

