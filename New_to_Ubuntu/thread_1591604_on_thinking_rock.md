---
title: "on thinking rock"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by asafzid on 2010-10-09
Hi every body
I'm an absolute new ubuntu user, and quite ignorant in computers
I'm trying to download thinkingrock to my computer
 I would really appreciate if someone can help me here
Thanks so much
Asaf

---

### Post by nlsthzn on 2010-10-09
I see that the free version is only available as source... that makes it a bit more complicated to get installed and running on your system.

Fellow the guidelines [here]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html") and you should be good to go!

---

### Post by Rubi1200 on 2010-10-09
Download link:
[http://sourceforge.net/projects/thinkingrock/files/](http://sourceforge.net/projects/thinkingrock/files/)

you need the one for Linux: tr-2.2.1-with-jre.tar.gz

Documentation:
[http://www.trgtd.com.au/index.php?option=com_content&view=article&id=87:minsetup&catid=39:gettingstartedcat&Itemid=85](http://www.trgtd.com.au/index.php?option=com_content&view=article&id=87:minsetup&catid=39:gettingstartedcat&Itemid=85)

---

### Post by AndresC on 2010-11-20
> **Rubi1200 said:**
> Download link:
[http://sourceforge.net/projects/thinkingrock/files/](http://sourceforge.net/projects/thinkingrock/files/)

you need the one for Linux: tr-2.2.1-with-jre.tar.gz

Documentation:
[http://www.trgtd.com.au/index.php?option=com_content&view=article&id=87:minsetup&catid=39:gettingstartedcat&Itemid=85](http://www.trgtd.com.au/index.php?option=com_content&view=article&id=87:minsetup&catid=39:gettingstartedcat&Itemid=85)

I think you can download the version without the jre


Just check that you have java 1.6 already installed on your maverick box, it should be...

In my case

```
$java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.1) (6b20-1.9.1-1ubuntu3)
OpenJDK Server VM (build 17.0-b16, mixed mode)

```So download the version without the JRE
[http://sourceforge.net/projects/thinkingrock/files/ThinkingRock/TR%202.2.1/tr-2.2.1.tar.gz/download](http://sourceforge.net/projects/thinkingrock/files/ThinkingRock/TR%202.2.1/tr-2.2.1.tar.gz/download)

Unpack it somewhere:
```
/opt/thinkingrock
``` is a sensible place

so you should get something like

```
/opt/thinkingrock/:
tr-2.2.1

/opt/thinkingrock/tr-2.2.1:
bin
etc
ide10
install.html
platform9
tr

/opt/thinkingrock/tr-2.2.1/bin:
tr
tr48.png
tr.exe
tr.png
tr.sh
tr_w.exe
xdg-email
xdg-open

```just type 
```
/opt/thinkingrock/tr-2.2.1/bin/tr.sh
```and you should get it up and running.

the ```
/opt/thinkingrock/tr-2.2.1/install.sh
``` file has some further information in case you need it.

---

### Post by birkopf on 2011-09-20
Hello,

I had working TR before on previous system. Now I'm on Maverick with Java 1.6.0.26. All applications based on java work like a charm but ThinkingRock doesn't start up. Gives just an error:

```

Cannot find java. Please use the --jdkhome switch.

```

Does anyone have idea how to fix it ?

---

### Post by oldos2er on 2011-09-20
Please start a new thread explaining your problem in full. Thanks!

---

