---
title: "Skillsoft not working"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Apoorvbarwa on 2011-01-17
I am taking an e-learning course..... But i am not able to run the applet... It says that java is not installed whereas i have java installed ... i get different results for Mozilla and Chrome ... Chrome results are good but skillsoft does not support chrome ... plzz help ... i have attached the two results..

---

### Post by kaldor on 2011-01-17
You may be using OpenJDK/IcedTea instead of Oracle/Sun Java. 

What version of Ubuntu are you running? If you're in Lucid Lynx (Ubuntu 10.04) paste these commands in the terminal (Applications > Terminal)

```

sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"

sudo apt-get install sun-java6-jre

sudo apt-get install sun-java6-plugin


```

Hopefully that will help.

---

### Post by Apoorvbarwa on 2011-01-17
yes ... when i do about:plugins in mozilla it says Openjdk/Icedtea .... but when i run these commands in terminal it says it already exists .... below is the output


sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
apoorv@apoorv-desktop:~$ sudo aptitude install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by lykeion on 2011-01-17
You can list your installed java versions with following command
```
java-update-alternatives --list
```
If you've installed Sun Java you'll see an entry starting with "java-6-sun"
To switch to installed Sun Java enter:
```
sudo java-update-alternatives --set java-6-sun
```
Then you can restart firefox and try the skillsoft check again.

---

### Post by kaldor on 2011-01-17
If I were you, I'd just remove the Icedtea plugin.

---

### Post by Zzl1xndd on 2011-01-17
removing the IcedTea Plug in should work as well as it can conflict with the Oracle Java Plug in.

---

### Post by Apoorvbarwa on 2011-01-21
Hii ... i got the skillsoft material to work ... all i did was change JRE that i was using .... 

Before

apoorv@apoorv-desktop:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

To change .... 


apoorv@apoorv-desktop:~$ sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/bin/cacao                             10        manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 3


After


apoorv@apoorv-desktop:~$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Client VM (build 17.1-b03, mixed mode, sharing)


Now only one more thing .. to remove IcedtEA I did

sudo apt-get remove icedtea6-plugin icedtea-6-jre-cacao

but still as you can see it is showing in the options ...

how do i remove this plugin???

---

### Post by lykeion on 2011-01-22
> Now only one more thing .. to remove IcedtEA I did
sudo apt-get remove icedtea6-plugin icedtea-6-jre-cacao
but still as you can see it is showing in the options ...
how do i remove this plugin???
You remove the IcedTea plugin just the way you did. 

Is it the OpenJDK JRE that you see from your *update-alternatives --config java* output you want to remove as well?
If so you should remove the *openjdk-6-jre* package.

@tweakedenigma
I've never experienced any conflicts between IcedTea and Sun Java plugin. Can you confirm this/give any examples?

---

### Post by ronnielsen1 on 2011-01-22
> Hii ... i got the skillsoft material to work ... all i did was change JRE that i was using .... 

Does it work right then? You might want to consider upgrading the page at winehq to help other people out. Someone else rated it as garbage

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8944](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8944)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15095](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15095)

---

### Post by masoud77 on 2012-12-05
Works well for me as i have now opted for the Oracle jre rather than IcedTea. IcedTea was causing a lot of issues which hopefully might be resolved in later versions.

Apoorv, thanks for post as it has helped me to take skillsoft at home as well. i have installed jre 6u37.

Thanks,
Masoud A R

---

### Post by lisati on 2012-12-05
From the [CoC]("http://ubuntuforums.org/index.php?page=policy"):
[quote=Code of Conduct]
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/quote]

---

