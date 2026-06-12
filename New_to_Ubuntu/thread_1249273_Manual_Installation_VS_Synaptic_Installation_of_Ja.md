---
title: "Manual Installation VS Synaptic Installation of Java"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by chandru155 on 2009-08-25
I downloaded Java 1.6 update 14 as a Bin file. My friend told me the install command is

SH JAVA1.6.BIN 

I tried this command, it installed. But the problem is it just installed in the directory where i kept the BIN file(DESKTOP). But usally it should install in USR/BIN/JVM/JDK1.6(Yesterday i installed via Synaptic).  How to make it automatically install to the correct folder?
Also, after installing, i typed JAVA in terminal and it displayed Something Like,
java is in more than one package
open jdk
xxxx
yyyy
zzzz
use apt-get install to install.

(I dont know the exact thing that was displayed. But it was like this only)


How to set the PATH for java.( we can use PATH VARIABLE) but yesterday with Synaptic manager, the java command in terminal worked fine. I didnt set manually the PATH variable

---

### Post by 3rdalbum on 2009-08-25
In order to install anything in a system-wide location such as /usr/bin, you need to run the installer as root. If the installer detects that it is not running as root, it will install for your user only. If it detects that it is running as root, then it will install system-wide automatically.

---

### Post by chandru155 on 2009-08-25
I used the SUDO command. But still its not working.

---

### Post by 3rdalbum on 2009-08-25
> **chandru155 said:**
> I used the SUDO command. But still its not working.

In what way?

---

### Post by chandru155 on 2009-08-25
sudo sh java1.6.bin     and it asked me the password, i gave it. But it installed in the current directory only. Then i logged in Root and tried    SH JAVA1.6.BIN    and still its not working

---

### Post by tarps87 on 2009-08-25
Try
```

sudo mkdir /usr/java
sudo cp java1.6.bin /usr/java
cd /usr/java
sudo sh java1.6.bin
sudo ln -s java*version*/bin/* /usr/bin

```

The message means there is more than one java package, sun-jre and sun-jdk are the sun java packages, open jdk is an open source version and the others are other versions

Edit: Are you tring to install the JDK or JRE?

---

### Post by chandru155 on 2009-08-25
I am trying to installing JDK only (jdk-6u16-linux-i586.bin) . In windows, it will install both jdk and jre. Just now i saw,there is no jre in that java installation folder. Should i manually download jre too?   The result for the code you gave is    chandru@ubuntu:/usr/share/java$ java  The program 'java' can be found in the following packages:   * gij-4.3  * java-gcj-compat-headless   * openjdk-6-jre-headless   * cacao  * gij-4.2  * jamvm   * kaffe  Try: sudo apt-get install  bash: java: command not found

---

### Post by tarps87 on 2009-08-25
Sorry my fault I had share in from a custom install, this is what I ment (note instead of using javaversion/bin* you can use /usr/bin/java /usr/bin/javac and so on for each program you want to use)

```
sudo mkdir /usr/java
sudo cp java1.6.bin /usr/java
cd /usr/java
sudo sh java1.6.bin
sudo ln -s javaversion/bin/* /usr/bin

```

I am surprised you don't have a jre folder, I have update 14 installed and do

---

### Post by fanglinyong on 2009-08-25
i think you should use this code ,its works good !
```
sudo apt-get install sun-java6-jre
```good luck!
for this command, you must hava a internate link!

---

### Post by tarps87 on 2009-08-25
The OP is trying to install the jdk which is
```
sudo apt-get install sun-java6-jdk
```
But I am assuming they want to do a manual install so it doesn't auto update or the version is more up to date than in the repos, is this correct?

---

### Post by chandru155 on 2009-08-25
I better go for apt-get. Manual installation is not working for me

---

### Post by tarps87 on 2009-08-25
How far did you get?
If you just want to install java I would suggest using the repo version (apt-get) as it will update it for you

---

