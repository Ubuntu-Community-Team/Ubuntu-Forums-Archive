---
title: "problem setting PATH for Java"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by spearfish on 2010-05-28
Hi,

I need help getting my PATH pointed to the right version of Java.  Right now it's going to the GNU Java 1.5 version, not the correct version of Java 1.6 that I have installed:

$ java -version
java version "1.5.0"


Java 6 is installed on my system and it lives in the following dir:

/usr/ilb/jvm/java-6-sun.1.6.0.20

I use Eclipse and program for Android, and Eclipse is going to the directory where java-6-sun.1.6.0.20 is.

Also, my .bashrc file has the following path info:

PATH=$PATH:/home/spearfish/android-sdk-linux_86/tools
PATH=$PATH:/home/spearfish/eclipse
PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.20
PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin
export PATH

However, when I type: echo $PATH  I get a bunch of extra stuff that's not in my .bashrc file:

spearfish@computer:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/home/spearfish/android-sdk-linux_86/tools:/home/spearfish/eclipse:/usr/lib/jvm/java-6-sun-1.6.0.20:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin
spearfish@computer:~$ 

What the heck?  Where did /usr/bin  come from?  That's not in my .bashrc file.  When I go there and type $ java -version it comes up with the GNU 1.5 version.  So I think the system is looking there first and never seeing my copy of Java 6.

Anyway, I need help pointing the PATH to the correct version of Java-6 that lives in my:  /usr/lib/jvm/java-6-sun-1.6.0.20  folder.

thanks! 8)

---

### Post by 2hot6ft2 on 2010-05-28
Run this to see what versions are installed
```
sudo update-java-alternatives -l
```
it will return something like this
> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
Run this to set it to use the sun version
```
sudo update-java-alternatives -s java-6-sun
```
If you get errors make sure you have default-jre installed and try again
```
sudo apt-get install default-jre
```
Restart firefox and check the version of Java being used by testing it here:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

If you're still having problems see this thread
[Removing openjdk and installing suns version]("http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40")
:popcorn:

---

