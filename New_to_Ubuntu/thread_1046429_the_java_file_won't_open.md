---
title: "the java file won't open"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by KanineN on 2009-01-21
Hello! I am trying to open a .jar program on my computer. The code I am using is

```
java -jar /pedro/MeBoyBuilder.jar
```

Then I get the following message.

```
	
The "java" can be found in the following package:
  * Java-gcj-compat-head less
  * Cacao-oj6-jre-head less
  * Gij-4.2
  * Coffee
  * CACAO
  * Openjdk-6-jre-head less
  * Jamvm
  * Gij-4.3
  * Sablevm
Try: sudo apt-get install <chosen package>
```

---

### Post by igknighted on 2009-01-21
Did you install a java runtime environment (jre)?  If not, install the package 'sun-java6-jre'.

---

### Post by opscure on 2009-01-21
You have a few different things going on here. 

First, you don't have java installed on your machine, but you wouldn't need it to view the contents of a jar.  

A Jar file usually contains compiled .java files into .class files and archived into a .jar.  If you simply want to look at what the .jar file contains just rename it to filename.zip and extract the files normally.  

If you want to decompile the class files then you will need a decompiler like jad.  You can download it here: [http://www.kpdus.com/jad/linux/jadlx158.zip](http://www.kpdus.com/jad/linux/jadlx158.zip)
then just extract jad to /usr/bin and you will be able to call it from the command line like:
```
jad -p filename.class 
```

If you are looking to compile java files into a jar then you will need to install java by doing a 
```
sudo apt-get install sun-java6-jdk 
```and the runtime with
```
sudo apt-get install sun-java6-jre 
```

---

### Post by Michael.Godawski on 2009-01-21
hi

basically you need these three packages:
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by binbash on 2009-01-21
Yes, you need sun's java.Install it and you will be fine

---

