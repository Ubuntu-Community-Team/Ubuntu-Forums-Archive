---
title: "Problem installing Java SE in Ubuntu 8.10"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by gofeddy on 2009-02-20
Hi,

I have the Ubuntu 8.10 distro. I wanted to install Java in the machine and went to the Sun website and downloaded the jdk-6u12-linux-i586.bin file and ran it in the terminal using the "./jdk-6u12-linux-i586.bin" command after executing "chmod a+x".

I agreed to the licence agreement and Java was setup. But then when I tried to install Greenfoot which was a .jar file using the command "java -jar greenfoot-installer-151.jar", I get an error message saying:

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

When I type in the command "whereis java" it gives me an output "/usr/share/java" and when I give the command "which java" it gives me no output. 

Is there any solution to this problem?:(

---

### Post by taurus on 2009-02-20
Unless you have a reason to install version 6.12 by hand, try installing the one in the repos, 6.11.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by gofeddy on 2009-02-20
So before installing v6.11, do I need to remove the previous installation or I can just start the new one without having to do any removal or deletion of the older install. This is because, I don't want to have any old versions or unused installations remaining on the system.

---

### Post by taurus on 2009-02-20
You can remove the one that you unpacked by hand now or later from a terminal.  Doesn't really matter at this point.  Make sure you remember where you've unpacked it since you need to remove that directory and everything under it.

---

