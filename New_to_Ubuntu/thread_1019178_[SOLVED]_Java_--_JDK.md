---
title: "[SOLVED] Java -- JDK"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-22
I want to write Java code in Ubuntu. I checked through the terminal, and the Java runtime engine is installed. But I'm not sure if that means the JDK for developing is installed as well. Here is what the readout said. 

```

joshua@Lattie:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

```

How to I determine whether not I have the compiler and libraries for developing on Ubuntu? I went to the Java website 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter)

But I'm not sure how to install binary files yet. I'm thinking it should already be on here, but maybe not, because I never installed it. It might just be the Java runtime engine for interpreting Java applets. Can anyone help me out? 

I just want to see if Java development kit is installed, and if not how to install it.

---

### Post by taurus on 2008-12-22
You want the sun-java6-jdk package.  Use Quick Search in synaptic to search for it.  Otherwise, you can install it from a terminal.

---

### Post by ken22 on 2008-12-22
If javac is installed then the jdk is installed, so try

```
javac -version
```

---

### Post by sanubie on 2008-12-22
That did the trick. Thanks a lot, you guys.  

PS: I want to learn more about the terminal. Where can I learn how to install stuff, and other cool tricks from the terminal?

---

### Post by ken22 on 2008-12-22
Generally to install a program

```
sudo apt-get install name_of_program
```

A guide to using the terminal is located here 

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

