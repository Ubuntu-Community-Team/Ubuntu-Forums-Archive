---
title: "Installing JDK"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Existance0 on 2010-04-30
```
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jdk-6u20-linux-i586.rpm  
  inflating: sun-javadb-common-10.5.3-0.2.i386.rpm  
  inflating: sun-javadb-core-10.5.3-0.2.i386.rpm  
  inflating: sun-javadb-client-10.5.3-0.2.i386.rpm  
  inflating: sun-javadb-demo-10.5.3-0.2.i386.rpm  
  inflating: sun-javadb-docs-10.5.3-0.2.i386.rpm  
  inflating: sun-javadb-javadoc-10.5.3-0.2.i386.rpm  
./jdk-6u20-linux-i586-rpm.bin: 619: rpm: not found
./jdk-6u20-linux-i586-rpm.bin: 619: rpm: not found
Installing JavaDB
./jdk-6u20-linux-i586-rpm.bin: 619: rpm: not found
 
Done.


```
Is it supposed to do that!? That file is on my desktop though its the one I had to run to get to the installer.

---

### Post by Paqman on 2010-04-30
Couple of tips:
[LIST=1]
[*]Rpms won't install on Debian-based Linux systems like Ubuntu. We use .debs
[*]Normally on Ubuntu you don't download software from websites, you get it through your package manager
[/LIST]

Go to System > Admin > Synaptic and install the JDK packages you want from there.

---

### Post by r-senior on 2010-04-30
You may also need to switch your preferences to use the Sun JDK/JRE when you've installed it:

See what this produces:

$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

If it's not similar to that, it's not the Sun (or should I say Oracle) Java, and you need to do this:

$ sudo update-java-alternatives -s java-6-sun

---

### Post by Existance0 on 2010-04-30
> **Paqman said:**
> Couple of tips:
[LIST=1]
[*]Rpms won't install on Debian-based Linux systems like Ubuntu. We use .debs
[*]Normally on Ubuntu you don't download software from websites, you get it through your package manager
[/LIST]

Go to System > Admin > Synaptic and install the JDK packages you want from there.

Thanks :p

---

