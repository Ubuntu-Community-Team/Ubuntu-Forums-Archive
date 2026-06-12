---
title: "Problems running Puzzle Pirates (Game)"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by MikeylovesJade on 2009-01-22
Okay i installed it and i've installed Java but when i run the game it says  this in the terminal..

open@terminator:~$ /home/open/yohoho/yohoho
/home/open/yohoho/yohoho: 16: java: not found
open@terminator:~$ 

I tryed clicking the icon n it wont do anything, and i've tried going to home n opening the yohoho exe yet none of the options work, any ideas?

---

### Post by taurus on 2009-01-22
What is the output of this command from a terminal?

```
java -version
```

---

### Post by MikeylovesJade on 2009-01-22
open@terminator:~$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * cacao
 * openjdk-6-jre-headless
 * jamvm
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
open@terminator:~$ 

it said when i installed it it was done



now it says...

open@terminator:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
open@terminator:~$ 

but now instead of it saying java isnt there it just shows this...


open@terminator:~$ /home/open/yohoho/yohoho
open@terminator:~$

---

### Post by taurus on 2009-01-22
How did you install it?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and return to accept it.  Then run this command again to see if it is using the right version.

```
java -version
```

---

### Post by MikeylovesJade on 2009-01-22
open@terminator:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
open@terminator:~$ 

is wat it says now, is that right?

Edit: It still doesnt do anything when trying to open yohoho though :/

---

### Post by taurus on 2009-01-22
You probably need the Sun's version.  Look at the commands from my previous post on how to install it.

---

### Post by MikeylovesJade on 2009-01-22
K thank you, but if i get it installed correctly n it still says nothing when trying to open the exe is there any advice u may have?

Sry to be a bother lol.


edit:

\open@terminator:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-pugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
open@terminator:~$

---

### Post by taurus on 2009-01-22
Repeat this.

"Linux is not windows."
"Linux is not windows."
"Linux is not windows."

You _cannot_ run .exe in Linux without using wine.

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by taurus on 2009-01-22
If you already installed the Sun's version and the system is still using the openJDK, reconfigure it with

```
sudo update-alternatives --config java
```
Make sure the Sun's java is the default.

---

### Post by MikeylovesJade on 2009-01-22
Thank you so much it works now :d

---

