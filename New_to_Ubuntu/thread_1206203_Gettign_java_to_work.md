---
title: "Gettign java to work"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-06
What do I need to install to get Java to work correctly on NOAA weather?

---

### Post by nhasian on 2009-07-07
to install Sun's Java from a terminal type:

```
sudo apt-get install sun-java6-jre
```

then choose sun's java 6 from the list of javas with:

```
sudo update-alternatives --config java
```

---

### Post by servicetech on 2009-07-07
bob@bob-desktop:~$ sudo apt-get install sun-java6-jre
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
bob@bob-desktop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
bob@bob-desktop:~$

---

### Post by kpkeerthi on 2009-07-07
Your Java is setup properly. Not sure what NOAA is, though.

---

### Post by servicetech on 2009-07-09
[http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes](http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes)

---

### Post by credobyte on 2009-07-09
```
sudo apt-get install sun-java6-plugin

```

Restart your browser and it should work ;)

---

