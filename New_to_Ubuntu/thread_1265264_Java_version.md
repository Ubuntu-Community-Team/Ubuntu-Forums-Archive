---
title: "Java version"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Chris1000 on 2009-09-13
Hallo,

I have a question to Java. As I wanted to install a program, I got the error message that the program required Java Runtime Environment 1.5.0.  I upgradedubuntu and when I checked the Java version on Ubuntu I got the following message: :???:

```

chris@chris-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

```

Now I have two questions.

1. Why is ubuntu using a different runtime environment version than can be found on the sun's webpages? Is there coming an update soon?

2. And if I am using sun's version, will it be automatically updated with the ubuntu update manager or do I have to do it manually? 

Thanks
Chris ):P

---

### Post by yeats on 2009-09-13
> 1. Why is ubuntu using a different runtime environment version than can be found on the sun's webpages? Is there coming an update soon?

The Sun version is not free/open source software and cannot be included by default in Ubuntu.  You have to accept the Sun license to use the Sun version.  The OpenJDK version is an attempt to provide the same functionality in a free/open source way.  Functionality-wise, it does not work very well as a replacement for the Sun version (IMHO).


> 2. And if I am using sun's version, will it be automatically updated with the ubuntu update manager or do I have to do it manually?


Yes.  Go to synaptic and search for Sun Java.  Installing that version will make the Sun version the default.

---

### Post by Penguin Guy on 2009-09-13
OpenJDK is an open source version of Java, if you want a different version; [take a look in the repositories]("http://www.psychocats.net/ubuntu/installingsoftware"). Anything in the repositories will be updated automatically, anything else will not. A different version of Java is used purely for religious reasons - this is unlikely to change anytime soon.

---

### Post by lykeion on 2009-09-13
1. It's a licensing issue. IcedTea java is based on the opensource OpenJDK, whereas Sun Java is proprietary.

2. Sun Java JRE (sun-java5-jdk, sun-java6-jdk) is in the multiverse repository and is updated automatically for you.

Read this for more info:

[https://help.ubuntu.com/community/JavaInstallation]("https://help.ubuntu.com/community/JavaInstallation")

Hope this will answer your questions.

---

### Post by Chris1000 on 2009-09-13
Hi,

many thanks :D.

I deleted the open version and continue with sun's as long as I depend on programs which need sun's java

Chris

---

