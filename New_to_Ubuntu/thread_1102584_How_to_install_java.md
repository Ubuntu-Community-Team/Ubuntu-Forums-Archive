---
title: "How to install java?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by eilios on 2009-03-21
I can get flash to work, but java is a mystery to me.

---

### Post by taurus on 2009-03-21
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Ben Crisford on 2009-03-21
I can't really expand on what taurus said, but the tutorial on the sun microsystems website is pretty neat.

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

Scroll down to the linux section, and click instructions next to the appropriate package.

---

### Post by RedSingularity on 2009-03-21
Yeah thats what i did.  Their instructions were easy to follow.

---

### Post by eilios on 2009-03-21
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
davis@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for davis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
davis@ubuntu:~$ 

I already used sudo apt-get update this day, so I figured it would be useless.

EDIT: Ben's guide does not work.

---

### Post by theozzlives on 2009-03-21
All I did was install the ubuntu-restricted-extras

---

### Post by eilios on 2009-03-21
> **theozzlives said:**
> All I did was install the ubuntu-restricted-extras
How?

---

### Post by Therion on 2009-03-21
That was going to be my suggestion as well...
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by taurus on 2009-03-21
Open System -> Administration -> Software Sources and enable all the repos (universe & multiverse).  Click the 3rd-Party tab and enable the one for canonical also.  Close Software Sources and run those two commands again from a terminal.

---

### Post by eilios on 2009-03-21
> **taurus said:**
> Open System -> Administration -> Software Sources and enable all the repos (universe & multiverse).  Click the 3rd-Party tab and enable the one for canonical also.  Close Software Sources and run those two commands again from a terminal.
Still nothing. The restricted extras work, but it's out of date, and as such I cannot do anything. :/

---

### Post by eilios on 2009-03-21
> **eilios said:**
> Still nothing. The restricted extras work, but it's out of date, and as such I cannot do anything. :/
Bump.

---

### Post by presence1960 on 2009-03-21
are you using 32bit or 64bit?

---

### Post by taurus on 2009-03-21
What are the outputs of these commands?

```
uname -m
java -version
```

---

### Post by eilios on 2009-03-22
[code]
***@ubuntu:~$ uname -m
x86_64
***@ubuntu:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

---

### Post by oldos2er on 2009-03-22
I don't think there is a sun-java6-plugin package for 8.10.

 See [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by eilios on 2009-03-22
> **oldos2er said:**
> I don't think there is a sun-java6-plugin package for 8.10.

 See [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)
Works, thanks, problem solved. :D

---

### Post by rath358 on 2009-03-22
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

This worked for installing java, but it did not install the correct version of java. How would I change the commands to get java 6 update 12?

---

### Post by presence1960 on 2009-03-22
> **eilios said:**
> [code]
***@ubuntu:~$ uname -m
x86_64
***@ubuntu:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)


Since you are using 64 bit you can install the most recent java plugin for firefox. It is snappier than the previous versions. I gotta acknowledge zika for turning me onto this : http://ubuntuforums.org/showpost.php?p=6791349&postcount=59

this is the resulting install

> raz@raz-desktop ~ $ java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

---

