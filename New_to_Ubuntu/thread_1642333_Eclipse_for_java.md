---
title: "Eclipse for java"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2010-12-10
Hi,

Is their any thread for setting up latest eclipse (3.6) and sun-6-jdk in Lucid Lynx?
Will be grateful if someone could direct me to it.
Thanx in advance.

---

### Post by lykeion on 2010-12-11
1. Install Sun Java 6 JDK from partner repositories.
2. Install Eclipse 3.5 Galileo from multiverse repositories.

If you don't specifically need to use Helios I'd suggest you to stick with Galileo.

To install Eclipse 3.6 Helios you'll have to download it from the Eclipse site. You can extract the downloaded archive to your home directory run it from there. You might have to manually set the path to the JDK inside Eclipse.

Get back here if you have any further questions, and I'll try to answer them as soon as I'm on the forums.

Good luck!

---

### Post by gupta_sumesh63 on 2010-12-12
Thanks for the response.
I'll stick with Galileo for now.
It does what I want.
Thanks again.:P

---

### Post by Numer0bis on 2010-12-24
Installing Helios 3.6 on Ubuntu 10.10 is rather simple. Download eclipse package from eclipse.org and extract it to a folder in your home directory. 

The tricky part is setting up java6-jdk from the sun partner repository but there is a easy to follow guide on [http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

basically you have to enable the partner repository

than install java6 jdk with

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

and then if necessary update your java alternatives with:

shows a list with available java alternatives
```

sudo update-java-alternatives -l
```

sets the alternative
```
sudo update-java-alternatives -s java-6-sun
sudo update-alternatives --config java
```

---

