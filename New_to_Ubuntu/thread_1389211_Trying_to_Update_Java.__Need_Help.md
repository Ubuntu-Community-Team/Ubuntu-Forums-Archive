---
title: "Trying to Update Java.  Need Help"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by tvillamil on 2010-01-24
Hello, 

I'm trying to update to JRE1.6.0_18.  I followed the instructions in the following thread:

[http://ubuntuforums.org/showthread.php?t=539423](http://ubuntuforums.org/showthread.php?t=539423)

and made sure to replace it with  JRE1.6.0_18.

I supposedly configured the sym links...

I ran the jave -version and it comes up with the following:

java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)
Java HotSpot(TM) 64-Bit Server VM (build 16.0-b13, mixed mode)

but when I go to the Java.com site and check my java version, I get the following message:

**Oops! You don't have the recommended Java installed.**

 									[B]Your Java version is Version 6 Update 15

[/B]When checking the sym link (java-6-sun), it looks like it hasn't changed.  It is still pointing to the older version.

Can someone help me out and tell me what I need to do to change the sym link to point to Update 18???

the directory where java-6-sun and jre1.6.0_18 are located is in:  /usr/lib/jvm

Thanks

---

### Post by tvillamil on 2010-01-24
Solved:

Did a little more digging and found this in the forum:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Regards

---

