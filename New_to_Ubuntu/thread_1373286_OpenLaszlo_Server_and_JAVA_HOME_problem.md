---
title: "OpenLaszlo Server and JAVA_HOME problem"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by BioVirtual on 2010-01-05
Well it's a bit confusing, I downloaded Java from [www.java.com]("http://www.java.com") and installed it successfully. But when I go to java.com and click on verify Java, it's telling me:

**>  Oops! You don't have the recommended Java installed.**> 

                                     **Your Java version is 1.6.0_0.** Please click the button below to get the recommended Java for your computer. and what is the recommended java? **Version 6 Update 17 ! **the one that i just installed.

Anyhow, I tried to configure JAVA_HOME and the result of 
```
 echo $JAVA_HOME 
``` is :
```
 /usr/lib/jvm/java-6-openjdk 
```

when I try to install OpenLaszlo I get:

> 
The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program


---

### Post by cariboo on 2010-01-05
You may have a much easier time of it if you install java from the repositories. I usually install the ubuntu-restricted-extras meta package from the repositories. Go to System-->Administration-->Synaptic Package Manager and search for **ubuntu-restricted-extras** and install the meta package. This will also install flash, java  and most of the codecs you need to play most audio/video media.

---

### Post by BioVirtual on 2010-01-07
My problem is with JAVA_HOME configuration.

---

### Post by smokinblues on 2010-02-18
I think we covered this in another post. Try:

sudo update-java-alternatives -s java-6-sun

---

