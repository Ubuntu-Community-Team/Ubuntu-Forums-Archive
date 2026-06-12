---
title: "I want install apache at my Ubuntu 11.04"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by tarcisiocorte on 2011-09-03
Hi, I had a follow problem
tarcisio@ubuntu:~$ sudo apt-get install tomcat6

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
 tomcat6 : Depends: tomcat6-common (>= 6.0.28-10ubuntu2) but it is not going to be installed
           Recommends: authbind but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


How to install tomcat 6 or tomcat 7 preferentily

---

### Post by cariboo on 2011-09-04
Make sure you have the partner repositories enabled in System->Administration->Software Sources, then using your favorite method of installing packages search for **sun-java**

---

