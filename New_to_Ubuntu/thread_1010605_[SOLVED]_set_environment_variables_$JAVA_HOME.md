---
title: "[SOLVED] set environment variables $JAVA_HOME"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-13
I am trying to set environment variables $JAVA_HOME

when I was using java5-jdk
I would set the jvm to...
/usr/lib/jvm/java-1.5.0-sun 
and it would work

I have installed java6-jdk version "6-10-0ubuntu2" instead of java5

I tried to set the jvm to...
/usr/lib/jvm/java-6-sun-1.6.0.00

and it doesnt work... what am I missing? 

in the terminal I wrote 
java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-BIT Server VM (build 11.0-b15, mixed mode)
--------------

thank you

---

### Post by kpkeerthi on 2008-12-14
What does ```
echo $JAVA_HOME
``` print?

---

### Post by 007casper on 2008-12-14
when I write ```
echo $JAVA_HOME
```
it jumps one line and I get nothing... see down below
```

root@rex:~# echo $JAVA_HOME

root@rex:~#
```

?

I checked in synaptic... I got sun-java6-fonts, sun-java6-bin, sun-java6-jre, sun-java6-demo, sun-java6-jdk installed.

---

### Post by kpkeerthi on 2008-12-14
OK. That means JAVA_HOME is not set. You seem to be in your 'root' account. Is that where you want 'java' visible ? Possibly not.

Anyway, to set JAVA_HOME, add the below line to ~/.bashrc
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun

```
Close and open terminal again and type export $JAVA_HOME

If you are not sure, where Java is installed, post the output of:
```

ls -l /usr/lib/jvm

```

---

### Post by 007casper on 2008-12-14
no I dont want it to be in root... oh... here we go

echo $JAVA_HOME
/usr/lib/jvm/java-6-sun

ls -l /usr/lib/jvm
total 12
drwxr-xr-x 7 root root 4096 2008-12-05 00:18 java-1.5.0-gcj-4.3-1.5.0.0
drwxr-xr-x 5 root root 4096 2008-12-05 23:56 java-6-openjdk
lrwxrwxrwx 1 root root   19 2008-12-05 21:38 java-6-sun -> java-6-sun-1.6.0.10
drwxr-xr-x 9 root root 4096 2008-12-05 21:44 java-6-sun-1.6.0.10
lrwxrwxrwx 1 root root   26 2008-12-05 00:18 java-gcj -> java-1.5.0-gcj-4.3-1.5.0.0

---

### Post by kpkeerthi on 2008-12-14
OK. You Java HOME is infact /usr/lib/jvm/java-6-sun and has been set properly now :)

---

### Post by kpkeerthi on 2008-12-14
To make sure you are using the right Java (since you have 4 versions of it installed), type
```
java -version
```
The output should print **Sun Java version 1.6.0.10**.

---

### Post by 007casper on 2008-12-14
java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

---

### Post by kpkeerthi on 2008-12-14
Perfect.
You may want to uninstall the other Java implementations (using Synaptic and its search feature) if you no longer need them. Should free up a lot of space.

---

### Post by 007casper on 2008-12-14
Thank you so much... I got a stupid question... 
what are the differences in these java applications?  Thank you.

drwxr-xr-x 7 root root 4096 2008-12-05 00:18 java-1.5.0-gcj-4.3-1.5.0.0
drwxr-xr-x 5 root root 4096 2008-12-05 23:56 java-6-openjdk
lrwxrwxrwx 1 root root 19 2008-12-05 21:38 java-6-sun -> java-6-sun-1.6.0.10
drwxr-xr-x 9 root root 4096 2008-12-05 21:44 java-6-sun-1.6.0.10
lrwxrwxrwx 1 root root 26 2008-12-05 00:18 java-gcj -> java-1.5.0-gcj-4.3-1.5.0.0

---

### Post by Nepherte on 2008-12-14
You have 3 java versions installed:
[LIST]
[*]java-6-sun-1.6.0.10: The official sun java 6 update 10. java-6-sun just points to this version.
[*]java-6-openjdk: The open source java 6 (so not sun's).
[*]java-1.5.0-gcj-4.3-1.5.0.0: This is a small java compatible version to run the most basic java things. This is an old version and should not be used. Again, java-gcj points to this version.
[/LIST]

---

### Post by 007casper on 2008-12-14
drwxr-xr-x 7 root root 4096 2008-12-05 00:18 java-1.5.0-gcj-4.3-1.5.0.0 ~ delete/uninstall

drwxr-xr-x 5 root root 4096 2008-12-05 23:56 java-6-openjdk ~ delete/uninstall

lrwxrwxrwx 1 root root 19 2008-12-05 21:38 java-6-sun -> java-6-sun-1.6.0.10 ~keep
drwxr-xr-x 9 root root 4096 2008-12-05 21:44 java-6-sun-1.6.0.10 ~keep

lrwxrwxrwx 1 root root 26 2008-12-05 00:18 java-gcj -> java-1.5.0-gcj-4.3-1.5.0.0 ~ delete/uninstall


so I can delete those that I point out as "~delete/uninstall"

---

### Post by Nepherte on 2008-12-15
Indeed (unless there's a specific reason why you'd want to have multiple java installs, mostly for developpers). But don't just remove the directory, remove it with synaptics instead.

---

### Post by 007casper on 2008-12-19
thank you so much

cheers have a wonderful weekend

---

### Post by Spricklywell on 2009-01-16
I have set my $JAVA_HOME but I need to unset it, the problem being that I have set it to the jvm/java-1.5.0-sun-1.5.0.16 instead of the link. I have tried vi to remove the declaration in etc/environment(successfully) but the variable is still set.

To set it I used:  sudo bash -c "echo JAVA_HOME=/path/>>/etc/environment"

---

### Post by rgm3 on 2010-10-22
In my ~/.bashrc I have:

```

export JAVA_HOME=$( dirname  $( dirname $( readlink -e /usr/bin/java ) ) )

```

That finds the target of wherever the /usr/bin/java symlink is pointing, strips off the "bin/java" directory/program, and stuffs the result in the JAVA_HOME environment variable.  It should update to the correct value even after you change JVMs / JREs with update-alternatives, as long as you log in anew (or re-source ~/.bashrc).

There's probably a better way.  Mac OSX provides /usr/libexec/java_home for doing just about the same thing.

---

