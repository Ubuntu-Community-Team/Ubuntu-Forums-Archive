---
title: "is this java ok?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by adduds on 2011-03-18
Is this java ok? i presume openJDK means its the opensource version

is there better out there?

```
toews@kidlapp:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)

```

---

### Post by quirks on 2011-03-18
> i presume openJDK means its the opensource version

That is correct.

> Is this java ok?

Personally, I sometimes find that Java applications do not run properly with OpenJDK. As long as the applications that you use run fine, then there is no need to look for a different one.

> is there better out there?

I recommend using the Java implementation by the inventors of Java - Sun Microsystems (now part of Oracle). Refer to this document for instructions on how to install Sun's Java:
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by adduds on 2011-03-18
thanks very much!

i would like to purge all the java i have on my computer to make sure the new sun install goes smoothly and works

how would i go about that

sudo apt-get remove --purge java-common?

---

### Post by andrewthomas on 2011-03-18
```
sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-jdk 
```You may not have the openjdk-6-jdk, if not just leave it off.

Then: 

```
sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
sudo apt-get update   
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```

---

### Post by adduds on 2011-03-18
> **andrewthomas said:**
> ```
sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-jdk 
```You may not have the openjdk-6-jdk, if not just leave it off.

Then: 

```
sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
sudo apt-get update   
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```

thanks berry much!

install looks ok..

```

toews@kidlapp:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)

```

when i ran the final piece of code

```
sudo update-alternatives --config java
```

i got
> 
There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java

thanks for the quick responses!

just wondering why people prefer Sun java...i've read other places people prefer it to openJDK aswell

---

### Post by Old_Man_Unix on 2011-03-19
> **adduds said:**
> 

just wondering why people prefer Sun java...i've read other places people prefer it to openJDK aswell

There's a perception among some people that the Oracle/Sun version of Java "works better" than the FOSS version.  Of course, none of them can objectively  define what "works better" actually means.   

I think that this perception may go back to statements made many years ago  by James Gosling, the 'father' of Java, before Sun was taken over by Oracle and when FOSS Java was still in its toddler stage.  A lot has happened since then.

The official test of a Java implementation is the Java Compatibility Kit (JCK).  A Java implementation that passes the JCK is considered to be  "100% Java" with no ifs, ands or buts.  The FOSS implementation in Ubuntu passes that test - that's been true for at least a couple of years now.

If a Java application doesn't run on a Java implementation that has passed the JCK, that's  a bug in the application, not in the implementation.  Some commentators apparently don't see it that way. But poorly written or purposely broken applications shouldn't be the criteria for anything, unless it is how to write incorrect code .   

That having been said, the great thing about FOSS OS's is that you can pretty much do what you want with them, such as install non-FOSS software if you so choose.  Even rewrite the OS  (so long as you keep to the terms of the license).

---

