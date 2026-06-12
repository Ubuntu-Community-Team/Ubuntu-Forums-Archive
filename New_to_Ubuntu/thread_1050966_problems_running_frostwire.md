---
title: "problems running frostwire"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Bigadada_saba on 2009-01-26
Hi i have installed Frostwire and it doenst run what doe i have to doe to get it to run

---

### Post by taurus on 2009-01-26
Do you have java (the Sun version) installed on your machine?  Run it from a terminal to see what's the error message.

Applications -> Accessories -> Terminal
```
frostwire
```

---

### Post by Bigadada_saba on 2009-01-26
this is what i got when i ran frostwire in terminal

wingrove@wingrove-laptop:~$ frostwire
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
HOSTNAME IS wingrove-laptop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
wingrove@wingrove-laptop:~$

---

### Post by taurus on 2009-01-26
How did you install frostwire?  Looks like you don't have the right version of java installed on your machine.

```
java -version
```

---

### Post by Bigadada_saba on 2009-01-26
wingrove@wingrove-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * jamvm
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
wingrove@wingrove-laptop:~$

---

### Post by taurus on 2009-01-26
To install java, run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  Once the installation is done, check to make sure you have to right version running.

```
java -version
```

---

### Post by Bigadada_saba on 2009-01-26
wingrove@wingrove-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wingrove@wingrove-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * jamvm
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
wingrove@wingrove-laptop:~$

---

### Post by taurus on 2009-01-26
What is the output of this command?

```
sudo update-alternatives --config java
```

---

### Post by Bigadada_saba on 2009-01-26
There is only 1 program which provides java
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java). Nothing to configure.
wingrove@wingrove-laptop:~$

---

