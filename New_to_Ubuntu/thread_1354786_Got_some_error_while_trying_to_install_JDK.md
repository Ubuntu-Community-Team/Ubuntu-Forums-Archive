---
title: "Got some error while trying to install JDK"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by kannan.csea on 2009-12-14
kannan@kannan-laptop:~$ sudo apt-get install sun-java6-jdk 
[sudo] password for kannan: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kannan@kannan-laptop:~$ sudo dpkg --configure -a
kannan@kannan-laptop:~$ sudo apt-get install sun-java6-jdk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kannan@kannan-laptop:~$ sudo apt-get -f install sun-java6-jdk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What is causing this and now how can i install JDK.

---

### Post by Physical Hook on 2009-12-14
```
sudo apt-get -f install

```

What's the output ?

---

### Post by kannan.csea on 2009-12-14
> **Physical Hook said:**
> ```
sudo apt-get -f install

```What's the output ?

It goes and stops at a blue screen where it says


Package configuration

  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin

---

