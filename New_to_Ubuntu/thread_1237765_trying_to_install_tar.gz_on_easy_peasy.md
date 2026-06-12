---
title: "trying to install tar.gz on easy peasy"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by specter09 on 2009-08-11
I am trying to install aircrack on my Eee PC.  I've used the program on my windows laptop; however, I purchased the new computer to get the "questionable" software of the work computer.  To make a long story short, I am brand-new to Linux. 

I have the root terminal under system tools and the root program under programming.  The file is located in: /home/ryan/Desktop and its name is: aircrack-ng-1.0-rc4.tar.gz . I would greatly appreciate any help telling me what to type as well as where to type it so I can get this installed.  Yes, I have read countless forums and googled for hours, so please only post if you are willing to give constructive advice.  Thank you!

---

### Post by credobyte on 2009-08-11
Someone didn't searched properly: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) :p

---

### Post by jrothwell97 on 2009-08-11
Welcome to the Ubuntu forums! You don't need to use the .tar.gz file, it's in the package repositories - the advantage of this is that it can be kept up to date automatically.

Install aircrack-ng using Synaptic Package Manager or run

```
sudo apt-get install aircrack-ng
```

in a terminal.

---

### Post by specter09 on 2009-08-11
Thank you so much for replying.  I really, really appreciate it.  When I placed that code into the root terminal this is what I received.  Can you tell me what I need to do next in order to open the program?  Again, thanks.

root@ryan-laptop:/home/ryan# sudo apt-get install aircrack-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libcommons-collections3-java libxpp3-java libgcj9-0 libgcj-bc libbackport-util-concurrent-java openoffice.org-java-common
  libxom-java liblog4j1.2-java-gcj libjaxme-java libregexp-java libjaxp1.3-java-gcj liblog4j1.2-java libjdom1-java liblucene2-java
  libsuitesparse-3.1.0 libxerces2-java-gcj binutils-static libcommons-logging-java libcommons-codec-java libgcj-common libjaxp1.3-java
  linux-restricted-modules-common libxpp2-java libjline-java libgcj9-jar libxerces2-java libsaxonb-java libcommons-beanutils-java libblas3gf
  libdb-je-java liblapack3gf libcommons-digester-java libdb4.5-java-gcj libdb4.5-java libjtidy-java libservlet2.3-java libdom4j-java
  libjaxen-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  aircrack-ng
0 upgraded, 1 newly installed, 0 to remove and 103 not upgraded.
Need to get 1306kB of archives.
After this operation, 2290kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe aircrack-ng 1:1.0~rc1-2ubuntu1 [1306kB]
Fetched 1306kB in 29s (43.7kB/s)                                                                                                              
Selecting previously deselected package aircrack-ng.
(Reading database ... 110863 files and directories currently installed.)
Unpacking aircrack-ng (from .../aircrack-ng_1%3a1.0~rc1-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up aircrack-ng (1:1.0~rc1-2ubuntu1) ...
root@ryan-laptop:/home/ryan#

---

### Post by jrothwell97 on 2009-08-11
Firstly, it's not really a 'code', it's a 'command'. [/pedant] :)

Now, on Linux, aircrack doesn't have a GUI, so you have to use the command line. Instructions can be found on the aircrack-ng [website](http://www.aircrack-ng.org/doku.php).

**edit:** and by the way, you *really* shouldn't be logged in as root. It's incredibly insecure and dangerous.

---

### Post by Terl on 2009-08-11
Did it appear in your menu?  If not, sometimes you have to log out and back in for it to appear.  Of course you can always try starting it from terminal.  I took a quick look around via google as I've never used the program; it seems to be a command line program to me... you should find all you need to get started [on Aircrack home page]("http://www.aircrack-ng.org/doku.php")

---

### Post by specter09 on 2009-08-11
suggestions noted.  many thanks, jrothwell and terl!

---

