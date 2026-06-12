---
title: "Can't install sun-java6-jdk"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by quad65 on 2010-04-23
**Update**
I am trying to install Frostwire and its deb package says "Error: Dependency is not satisfiable: sun-java6-jre"

How can I solve this?

--------------------------------------------------------------------------------------------------
Hello,

I need to install JDK on Ubuntu 10.04 RC. When I write "sudo apt-get install sun-java6-jdk", error appears saying "Package sun-java6-jdk is not available, but is referred to by another package."

How can I install Sun's JDK and JRE?

Thanks in advance.

Extra info: I also downloaded "jdk-6u20-linux-i586.bin" and tried installing that (it got installed to my desktop) but I don't know how to install it to a system-wide reachable area. So, even after installation, I write "java" in terminal and an error message comes up.

---

### Post by carl4926 on 2010-04-23
Try using software centre

---

### Post by quad65 on 2010-04-23
It does not exist. There is only openJDK-JRE.

---

### Post by quad65 on 2010-04-23
Update: Used default-jdk and it installed openJDK-jdk and openJDK-jre. Tried Netbeans and it seems to be working fine.

**However**, I am trying to install Frostwire and its deb package says "Error: Dependency is not satisfiable: sun-java6-jre"

How can I solve this?

---

### Post by xumuk37 on 2010-04-23
try to get Sun JDK from Sun's web [[COLOR="Blue"]here[/COLOR]]("http://www.sun.com/download/index.jsp") make it executable and run it by double click...

---

### Post by quad65 on 2010-04-23
> **xumuk37 said:**
> try to get Sun JDK from Sun's web [[COLOR="Blue"]here[/COLOR]]("http://www.sun.com/download/index.jsp") make it executable and run it by double click...

Actually, making it executable did not make it runnable by double click.

Having downloaded the file before, I copied it to /usr/lib/jvm folder, made it executable by chmod a+x, then 
```
./jdk-6u20-linux-i586.bin
```

Agreed to license and installed. But still, when I type "java" at terminal, it says 

> The program 'java' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>

When I write "./java -ver" under /bin directory, I can see that java is there. I need to make it system-wide somehow...

---

### Post by xumuk37 on 2010-04-23
no idea... I only have installed sun JDK & netbeans 6.8 and everything works great...

but running java -version returns

OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)

so,imo, it depends from open JDK...

---

### Post by quad65 on 2010-04-23
I believe 10.04 no longer has sun-java6- packages.

If only I could point "java, javac etc. commands" to my manual installation /bin directory...

---

### Post by xumuk37 on 2010-04-23
you also can add sun-java executables to $PATH variable... the case is that I never use terminal for do anything with java...

---

### Post by oldos2er on 2010-04-23
If you install java manually, you need to then tell the system it's there:
```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_16/bin/java" 1

sudo update-alternatives --set java /opt/java/32/jre1.6.0_16/bin/java
```
Change the path to whatever it is on your system.

---

### Post by arrrghhh on 2010-04-23
Sun's java has been moved to the partner repo.  Uncomment that repo, and you can install sun-java6-jdk

---

### Post by dearingj on 2010-04-23
My copy of 10.04 does have sun-java6-* packages available. Have you enabled the main, universe, restricted, and multiverse repositories?

---

### Post by ratcheer on 2010-04-23
To make your JRE accessible, add the following statements to your .bashrc:

```

JAVA_HOME=/usr/java/jre1.6.0_20
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=$JAVA_HOME/lib

```In the first statement, set it to where ever you installed it. /usr/java is just where I installed mine.

Tim

---

### Post by QIII on 2010-04-23
I have to repeat what one poster said:  Enable the partner repo and install Java from there.

That has Update 20 (if you are using Lucid) of both the JRE and the JDK (I believe) and you can use the normal update process to keep it updated as Oracle/Sun distributes it.

Otherwise, you can use this guy's method to install the JRE at least:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

In either case, take a look at the URL provided, as he gives the method for making sure that Sun Java is used over OpenJDK.  You need not alter .bashrc or any other file directly.

Just as a side note:  OpenJDK is the open source version of Java and they are getting very close to making it a perfect match.  Unless you have a specific need for the "real deal" closed source Java, it should work perfectly well for you.

In my case, some of my clients specify Java and my bank website does not recognize OpenJDK.  It even balks when a new Java Update comes out and I haven't installed it.

---

### Post by arrrghhh on 2010-04-23
> **dearingj said:**
> My copy of 10.04 does have sun-java6-* packages available. Have you enabled the main, universe, restricted, and multiverse repositories?

It's been moved to the partner repo for 10.04...

---

### Post by quad65 on 2010-04-24
> **QIII said:**
> Just as a side note:  OpenJDK is the open source version of Java and they are getting very close to making it a perfect match.  Unless you have a specific need for the "real deal" closed source Java, it should work perfectly well for you.

In my first message, I said I needed it because FrostWire .deb package said "it could not satisfy dependency: sun-java6-jre"

I gave up on Frostwire. So, I no longer need sun-java6-* Still, I made a manual installation of Sun's .bin file and I have been using NetBeans with it without any problems.

> **oldos2er said:**
> If you install java manually, you need to then tell the system it's there:
```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_16/bin/java" 1

sudo update-alternatives --set java /opt/java/32/jre1.6.0_16/bin/java
```
Change the path to whatever it is on your system.

Actually I tried. Not really sure about this, since I could've made a mistake; I had to define every executable (java, javac, ...) separately for my sun-java installation. Otherwise, typing java would run sun-java; but javac would run openJDK (openJDK was installed, too).

> **arrrghhh said:**
> Sun's java has been moved to the partner repo.  Uncomment that repo, and you can install sun-java6-jdk

Thank you. I must have missed it. It would have been much easier and I wouldn't have spent this much time on it.

Thanks a lot for your answers. Marked as solved.

---

### Post by lkraemer on 2010-04-24
[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)


Sun Java moved to the Partner repository

For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"


lk

---

### Post by PhazzedOut on 2010-05-06
Thank you everyone. I just installed sun-java6-jdk, I needed it for the same reason OP needed it for. I couldn't get Frostwire to run even from a Tarball. Limewire worked perfectly from a Tarball but I really wanted Frostwire. Now I can run it. Thank you everyone.

---

### Post by progone on 2010-12-17
> **QIII said:**
> I have to repeat what one poster said:  Enable the partner repo and install Java from there.

That has Update 20 (if you are using Lucid) of both the JRE and the JDK (I believe) and you can use the normal update process to keep it updated as Oracle/Sun distributes it.

Otherwise, you can use this guy's method to install the JRE at least:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

In either case, take a look at the URL provided, as he gives the method for making sure that Sun Java is used over OpenJDK.  You need not alter .bashrc or any other file directly.

Just as a side note:  OpenJDK is the open source version of Java and they are getting very close to making it a perfect match.  Unless you have a specific need for the "real deal" closed source Java, it should work perfectly well for you.

In my case, some of my clients specify Java and my bank website does not recognize OpenJDK.  It even balks when a new Java Update comes out and I haven't installed it.

these were the best instructions.  If you are using JDK, simply type jdk instead of jre and replace the jdk-6u22-linux with the  newest version.  At this time its jdk-6u23-linux

---

### Post by spearfish on 2010-12-28
> **ratcheer said:**
> To make your JRE accessible, add the following statements to your .bashrc:

```

JAVA_HOME=/usr/java/jre1.6.0_20
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=$JAVA_HOME/lib

```In the first statement, set it to where ever you installed it. /usr/java is just where I installed mine.

Tim

Just a follow-up:  I just installed a fresh copy of Ubuntu 10.10 on my laptop and then I downloaded jdk-6u23-linux-i586.bin from the Oracle/Sun Java site.

After installing Java 6, I was not able to run javac from the command line.  The above code from "ratcheer" was added to my .bashrc and that did the trick.  You just have to set the path properly in order to run java from the command line.

---

