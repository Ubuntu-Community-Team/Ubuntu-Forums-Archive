---
title: "Eclipse: Error message on jvm"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by andrew222 on 2009-01-17
Hello,

I just installed java6 and Eclipse using the following tutorial which shows how to set up eclipse to use sun-java6-jdk

[http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6](http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6)


Now whenever I try to start up eclipse by clicking the icon (or by running command line), I get an error message that says:

"Could not launch Eclipse platform: The custom vm you have chosen is not a valid executable"

Can anyone tell me what I am doing wrong?  Any help is greatly appreciated...

---

### Post by igknighted on 2009-01-17
Can you run the command 'sudo update-alternatives --display java'?

---

### Post by andrew222 on 2009-01-17
Thank you...I just ran the command and below is the output



 andrew@andrew-laptop:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-6-sun/jre/bin/java
/usr/bin/gij-4.2 - priority 42
 slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz
/usr/bin/gij-4.3 - priority 43
 slave java.1.gz: /usr/share/man/man1/gij-4.3.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1042
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-

---

### Post by andrew222 on 2009-01-17
I switched to Gnome and Eclipse automatically worked,  so I removed Xubuntu.  I need to get some work done, so I am going to leave it as that........

Thank you for your help, hope you have a nice weekend...

---

