---
title: "shell script for java -jar"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by pala2003 on 2011-04-25
i'm new to java shell script dtls. in windows env.. _**java -jar yyy.jar**_ works when ***_.mf_*** has all the entris off othr jars. now if i want to pass classpath in java -classpath <drive>\jarFolder; -jar yyy.jar then it is not working.. in shell script how to do that. also.. can outside folder set to class path pls help..:confused:

---

### Post by akoskm on 2011-04-25
> **pala2003 said:**
> ...
java -classpath <drive>\jarFolder; -jar yyy.jar


Hi!
Use **/** instead of **\** in your path. Separate the classpath elements with **:** instead of **;**.

In shell scripts do the same

```

#!/bin/sh
java -jar -classpath .:some/path/:another/path yyyy.jar

```.

---

### Post by adit on 2011-04-25
> i'm new to java shell script
Are you new to linux?  Can you post exactly what you typed in terminal window?  Also post the output you got.

---

### Post by pala2003 on 2011-04-27
Thanks to all..
Yes, I'm new to linux/unix
actually I have three jar (created by me) . _yyy.jar_ (where the main method is present) and to helper jar is like _xx.jar_ and _zz.jar_ and _one confugartion folder having the config.properties_. 

No I want to set the classpath on runtime for these entries and the common jars like avalon.., db2jcc, mysql etc.

so, I'm want to write one shell scripts like 

[I]set $CLASSPATH = $CLASSPATH + '.:some/path/:another/path:/anotherPath/Config/';
java -jar yyy.jar INPUT -VMARGUS;
[/I]
but it is not able to find the classes.

* when I put the entries in to the MANIFEST.MF (all the class entries) and make a jar for Config.properts and put into the MANIFEST.MF and   then in windows
*_java -jar myfoledr/workdir/yyy.jar INPUT -VMARGUS_*;
command is working fine.

*only constrain is that I need to put all the required classes(user jars and also the common jars) into the same folder (workdir) where the yyy.jar is there.

is it also work in Unix..

Thanks again for the help.

---

### Post by akoskm on 2011-04-29
> **pala2003 said:**
> Thanks to all..
Yes, I'm new to linux/unix
actually I have three jar (created by me) . _yyy.jar_ (where the main method is present) and to helper jar is like _xx.jar_ and _zz.jar_ and _one confugartion folder having the config.properties_. 

No I want to set the classpath on runtime for these entries and the common jars like avalon.., db2jcc, mysql etc.

so, I'm want to write one shell scripts like 

[I]set $CLASSPATH = $CLASSPATH + '.:some/path/:another/path:/anotherPath/Config/';
java -jar yyy.jar INPUT -VMARGUS;
[/I]
but it is not able to find the classes.

* when I put the entries in to the MANIFEST.MF (all the class entries) and make a jar for Config.properts and put into the MANIFEST.MF and   then in windows
*_java -jar myfoledr/workdir/yyy.jar INPUT -VMARGUS_*;
command is working fine.

*only constrain is that I need to put all the required classes(user jars and also the common jars) into the same folder (workdir) where the yyy.jar is there.

is it also work in Unix..

Thanks again for the help.
It should work like this:
```

#!/bin/sh
CLASSPATH=.:some/path/:another/path:/anotherPath/Config/:$CLASSPATH
export CLASSPATH
java -jar yyy.jar INPUT -VMARGUS;

```

---

