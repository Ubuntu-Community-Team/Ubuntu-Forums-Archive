---
title: "sudo dpkg"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by ray62 on 2009-09-23
E: dpkg was interupted you must manualy run sudo dpkg - configure -a to correct problem
E: cache > open () failed please report help please i am a newbie ???

---

### Post by halitech on 2009-09-23
open a terminal and run
```
sudo dpkg -configure -a
```

---

### Post by scragar on 2009-09-23
Manually run the command it specifies in a terminal(applications>accessories>terminal)```
sudo dpkg -configure -a
```

---

### Post by ray62 on 2009-09-23
ray62@ray62-laptop:~$ sudo dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
ray62@ray62-laptop:~$ 

confused sorry lol

---

### Post by halitech on 2009-09-23
type it in as they show it if you typed it in correctly the first time
```
sudo dpkg - configure -a
```

---

### Post by ray62 on 2009-09-23
ray62@ray62-laptop:~$ sudo dpkg - configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
ray62@ray62-laptop:~$ 

help please i av typed it in correct i copied and pasted ???

---

### Post by ray62 on 2009-09-23
any one help please ???

---

### Post by halitech on 2009-09-23
let's try it right
```
sudo dpkg --configure -a
```

you omited a - in front of configure

---

### Post by ray62 on 2009-09-23
ray62@ray62-laptop:~$ sudo dpkg --configure -a
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
ray62@ray62-laptop:~$ 

is that ok ???

---

### Post by halitech on 2009-09-23
thats exactly what we wanted. you should be able to use synaptic now

---

### Post by ray62 on 2009-09-23
Many thanks

---

### Post by dhd1956 on 2009-09-25
I get:

dave@dave-desktop:~$ sudo dpkg --configure -a
[sudo] password for dave: 
dpkg: status database area is locked by another process
dave@dave-desktop:

Before this happened I ran the following. Ever since installing java 6, the same screen shows that requires the terminal session to freeze and the computer restarted before dpkg or apt-get can be used again. Java appears to work ok on the computer but the java 6 Package configuration remains a problem:

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
2 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

//ending with...

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;
...

---

