---
title: "Judy"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by judyoos on 2009-01-09
I am new to JAVA and downloaded the JDK1.6.0_07 version.
I need to download the J2SE API DOCUMENTATION but not sure wich one as my Search on the Internet gives me too may and I am not sure what to download.

Can anybody assist me.

Thanks
Judy):P

---

### Post by ThePinkPoo on 2009-01-09
[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

This is your best friend.

---

### Post by taurus on 2009-01-09
If you want to install java, try the one in the repos. Easier to install.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
When you get to the java license screen, press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by judyoos on 2009-01-09
No man, I have everything in place now and running windows xp.
All I need is the stupid API Documentation then i can continue...

---

### Post by ThePinkPoo on 2009-01-09
> **judyoos said:**
> No man, I have everything in place now and running windows xp.
All I need is the stupid API Documentation then i can continue...

Look at my first post:

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

---

### Post by 73ckn797 on 2009-01-09
Nevermind

---

### Post by ThePinkPoo on 2009-01-09
Here's the one for Java 6 which you downloaded, contains the new objects and methods to use.

[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

---

### Post by The Cog on 2009-01-09
As far as I can tell, the documentation comes with the software. I installed the JDK downloaded from Sun and installed it in /opt. The docs are in /opt/jdk1.6.0_10/docs/api/index.html but I don't know where the Ubuntu packagers would choose to hide it in their packaging. Perhaps somewhere in /usr/share. Try the command **locate index.html**.

---

### Post by Captain_tux on 2009-01-09
> **73ckn797 said:**
> nevermind

+1

Some things are just beyond explanation...

---

