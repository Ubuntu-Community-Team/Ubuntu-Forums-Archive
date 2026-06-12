---
title: "Changing system wide java version"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by moody_mark on 2009-10-16
I though this would be easy but it seems to have eluded me. I need to change my system wide java version from 1.6.0.14 to 1.6.0.13. I downloaded the 1.6.0.13 jre from Sun, run the installer (as sudo) from /usr/lib/jvm. It run ok, but everytime i run the command to find the java version its still the 1.6.0.14 version;

```
:/usr/lib/jvm$ ls -l
total 8
lrwxrwxrwx 1 root root   19 2009-07-03 10:59 java-6-sun -> java-6-sun-1.6.0.14
drwxr-xr-x 6 root root 4096 2009-07-03 10:59 java-6-sun-1.6.0.14
drwxr-xr-x 8 root root 4096 2009-10-16 12:48 jre1.6.0_13

:/usr/lib/jvm$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)
```

Im really stuck I even have a java control panel under "System -> Preferences" but it wont allow me to change system wide settings, even as sudo user.

---

### Post by tarps87 on 2009-10-16
Have you tried this?
```
sudo update-java-alternatives -l
```
```
sudo update-java-alternatives -s **javaVersion**
```

---

### Post by moody_mark on 2009-10-16
Hi, thanks for your quick response

```
:~$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun

:~$ sudo update-java-alternatives -s jre1.6.0_13
update-java-alternatives: file does not exist: /usr/lib/jvm/.jre1.6.0_13.jinfo

```

Where does that "...jinfo" file come from?

---

### Post by Mighty_Joe on 2009-10-16
> **moody_mark said:**
> 
Where does that "...jinfo" file come from?

Probably the package.  I don't think you can use update-java-alternatives to change your system-wide Java version to one that is outside the package management system.  
Is there some pressing need for 1.6.0.13?

---

### Post by moody_mark on 2009-10-16
> **Mighty_Joe said:**
> Is there some pressing need for 1.6.0.13?

Unfortunately yes there is. I use this machine for work and we have a java application that will only run on certain versions of java 1.6.0.13 being one of them.

---

### Post by tarps87 on 2009-10-16
> **Mighty_Joe said:**
> Probably the package.  I don't think you can use update-java-alternatives to change your system-wide Java version to one that is outside the package management system.  
Is there some pressing need for 1.6.0.13?

I believe that is true, I just relised you want to go between updates rather than versions

> **moody_mark said:**
> Unfortunately yes there is. I use this machine for work and we have a java application that will only run on certain versions of java 1.6.0.13 being one of them.

You could either run that app using java 1.6.0.13 or you can install java 1.6.0.14 and link java 1.6.0.13 into the path.
How did you install java 1.6.0.13?

---

### Post by moody_mark on 2009-10-16
> **tarps87 said:**
> How did you install java 1.6.0.13?

I downloaded the .bin file from the SUN website and run it as sudo under /usr/lib/jvm

The file is a .jsp file which is run from a browser it seems? Can I run it from the command line you think?

---

### Post by Mighty_Joe on 2009-10-16
> **moody_mark said:**
> 
The file is a .jsp file which is run from a browser it seems? Can I run it from the command line you think?

A [Java Server Page]("http://en.wikipedia.org/wiki/JavaServer_Pages") is an abstraction of a [Servlet]("http://en.wikipedia.org/wiki/Java_servlet"), which has to be run inside a [servlet container]("http://en.wikipedia.org/wiki/Servlet_container#Servlet_containers") (Glassfish, Tomcat, Weblogic, Websphere, etc).  
You can easily configure a servlet container to run on a particular version of Java by altering the startup scripts.  Exactly how one would do it is dependent on the container.

---

### Post by moody_mark on 2009-10-16
Your right, sorry its actually run when i go visit a certain page. This is where my java knowledge goes a bit flaky.

What can I do then?

---

### Post by Mighty_Joe on 2009-10-16
Are you running the server locally?  If not, the local Java version does not matter.

---

### Post by moody_mark on 2009-10-16
Solved! Heres what I did; (its in /etc/alternatives)

Find the link to the current java

```
curtis@Homer:/etc/alternatives$ ls -l java
lrwxrwxrwx 1 root root 36 2009-10-16 12:33 java -> /usr/lib/jvm/java-6-sun/jre/bin/java

```

Rename it (rather than delete it)

```
curtis@Homer:/etc/alternatives$ sudo mv java java.bkp

```

Make a new one then test it

```
curtis@Homer:/etc/alternatives$ sudo ln -s /usr/lib/jvm/jre1.6.0_13/bin/java java

curtis@Homer:/etc/alternatives$ which java
/usr/bin/java

curtis@Homer:/etc/alternatives$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)

```

Im assuming this is correct? now my app works ok anyway :)

---

### Post by tarps87 on 2009-10-16
That is one way, I was going to suggest editing the systems path variable but you way works so I'd leave it.  As you installed Java from the website it should also be excluded from system update but you may want to make sure when you update.

---

