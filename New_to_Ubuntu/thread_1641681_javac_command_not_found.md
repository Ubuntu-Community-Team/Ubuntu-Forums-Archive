---
title: "javac command not found"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by adit on 2010-12-09
I removed openjdk-6-jdk (which I previously installed) and now I installed sun-java6-jdk (through Canonical Partners repository).```

~$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Client VM (build 17.1-b03, mixed mode, sharing)
```
```
:~$ javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>
```
What happened to javac?

---

### Post by brishu on 2010-12-09
Just because 'java' works doesn't necessarily mean that 'javac' works as well.

For 'java' to work, you just need the JRE (Java Runtime Environment), which has the 'java' command in it. For 'javac' you neeed the JDK (Java Development Kit). 

Ubuntu doesn't come with JDK pre-installed, only the JRE. So, you have the 'java' command, but not the 'javac' command. Just install one of the packages recommended below and javac will work again.

---

### Post by adit on 2010-12-09
sun-java6-jdk is already installed.  But the command 'javac' does not work.

---

### Post by m_duck on 2010-12-09
This is only a suggestion which may or may not be helpful, but have you logged out or rebooted since installing the JDK? Ubuntu may need to source a file to set JAVA_HOME (I think), to be able to use javac. You could source it directly but I've no idea which file it would be (it's /etc/profile in Arch).

---

### Post by nalinc on 2012-01-26
i encountered the same problem on ubuntu 11.04..
whats the solution?
please help

thanks

---

### Post by nalinc on 2012-01-26
***/detailed info/***
i did install jdk6 using command

sudo apt-get install sun-java6-jdk sun-java6-jre

(it installed to /usr/lib/jvm/java-6-sun$ )

then to set the JAVA_HOME at its right path

i went to directory /etc/

appended the .bashrc file with following code:

JAVA_HOME=/usr/lib/jvm/java-6-sun
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

then when i typed
echo $JAVA_HOME
it showed
/usr/lib/jvm/java-6-sun
(everything seemd good till now)

bt when i compiled the code
javac hello.java

 it displayed

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>


please help

---

### Post by eric.cartman on 2012-03-09
javac is not included in the sun-java6-jdk or sun-java6-jre packages.

You should:
sudo apt-get install openjdk-6-jdk

which will install javac (among other things)

---

### Post by zombiezparadize on 2012-07-25
> **nalinc said:**
> ***/detailed info/***
i did install jdk6 using command

sudo apt-get install sun-java6-jdk sun-java6-jre

(it installed to /usr/lib/jvm/java-6-sun$ )

then to set the JAVA_HOME at its right path

i went to directory /etc/

appended the .bashrc file with following code:

JAVA_HOME=/usr/lib/jvm/java-6-sun
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

then when i typed
echo $JAVA_HOME
it showed
/usr/lib/jvm/java-6-sun
(everything seemd good till now)

bt when i compiled the code
javac hello.java

 it displayed

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>


please help

I am pretty sure you've found your solution by now but did you source your .bashrc file after you appended the environment variable definitions to the .bashrc file? I followed the same steps as you did and then sourced my .bashrc by just typing ". ~/.bashrc" at the command line and voila! All's good.

---

