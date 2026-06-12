---
title: "Problem after installing java"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by dhd1956 on 2009-09-25
Although java is installed. A Package configuration message appeared at the end of the session followed by terms and conditions in a window within the terminal session. It had <Ok> in the bottom but would not accept any keystrokes of ctrl keystrokes and ubuntu needed to be restarted to unlock outstanding commands. Now when I try to enter a sudo dpkg or apt-get command, it goes back to the java 6 window and hangs the terminal session once more.

Java works ok. But I cannot configure oracle-xe or install libaio1. It reverts back to the java terms and conditions screen and hangs.

Here's a sample...

dave@dave-desktop:~$ sudo apt-get install libaio1
[sudo] password for dave:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
dave@dave-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of oracle-xe-universal:
 oracle-xe-universal depends on libaio (>= 0.3.96) | libaio1 (>= 0.3.96); however:
  Package libaio is not installed.
  Package libaio1 is not installed.
dpkg: error processing oracle-xe-universal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oracle-xe-universal
dave@dave-desktop:~$ sudo apt-get install libaio1
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  libaio1
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded , 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.



Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472; [etc...]

---

### Post by credobyte on 2009-09-25
```
sudo apt-get -d sun-java6-jre && dpkg -i sun-java6-jre

```Try again.

---

### Post by dhd1956 on 2009-09-25
Thanks for the reply, however I got the following error when executing the code...

dave@dave-desktop:~$ sudo apt-get -d sun-java6-jre && dpkg -i sun-java6-jre
[sudo] password for dave: 
E: Invalid operation sun-java6-jre
dave@dave-desktop:~$ 

dave@dave-desktop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)
dave@dave-desktop:~$

---

### Post by sandyd on 2009-09-25
when you get to the java terms & conditions window, press TAB.

that should take you to the <ok> button

---

### Post by dhd1956 on 2009-09-25
Thank you very much! The tab button worked and I'm out of the frying pan. 

Now I'll try reinstalling oracle-xe and see if I get past the following command:

sudo /etc/init.d/oracle-xe configure
sudo: /etc/init.d/oracle-xe: command not found

---

