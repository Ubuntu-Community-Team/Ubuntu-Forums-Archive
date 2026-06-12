---
title: "Help with installing JDK"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-01
Hello there,

I would like some assistance as to how to install this [http://www.oracle.com/technetwork/java/javase/downloads/jdk6-jsp-136632.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk6-jsp-136632.html) on my Xubuntu 11.04 desktop.

I downloaded this file "jdk-6u21-linux-x64.bin" and I double click it. 
It says "Starting without Administrating privileges"and then I press OK. After that, it opens Synaptic Package Manager and doesn't should the file at all.

EDIT: I am also trying to download the JDK using:
```

sudo apt-get install sun-java6-jdk

```

But this is what I get when I post this on the terminal:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate
arqman@arqman-Inspiron-N5010:~$ sudo apt-get install sun-java6-jdk
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
arqman@arqman-Inspiron-N5010:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate

```

---

### Post by Toz on 2011-08-01
Make sure you enable the partner repositories. 
Open up Ubuntu Software Centre, select Edit->Software Sources, and on the "Other Software" tab, make sure Canonical Partners is selected.

---

### Post by WubiAR on 2011-08-01
Thank you.
[B]I wanted to know if "sun-java6-jdk" package is the same as downloading the .bin file from the [http://www.oracle.com/technetwork/java/javase/downloads/jdk6-jsp-136632.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk6-jsp-136632.html) website? If not, then how can I install the .bin file?
[/B]
EDIT: Solved the problem with that blue box.

---

### Post by Toz on 2011-08-01
Have you installed the sun-java6-jdk package from the repositories? If so, open a command terminal and type in:
```
java -version
```

What do you get?

---

### Post by Toz on 2011-08-01
The instructions to install the bin file are located at the Oracle site. See: [http://www.oracle.com/technetwork/java/javase/install-linux-64-self-extracting-142068.html]("http://www.oracle.com/technetwork/java/javase/install-linux-64-self-extracting-142068.html")

---

### Post by WubiAR on 2011-08-01
> **Toz said:**
> Have you installed the sun-java6-jdk package from the repositories? If so, open a command terminal and type in:
```
java -version
```What do you get?

I get this:
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

---

### Post by Toz on 2011-08-01
The version you installed is a newer version than the bin you downloaded. Also note, that Oracle has recently released Java version 7. See: [http://www.oracle.com/technetwork/java/javase/downloads/index.html]("http://www.oracle.com/technetwork/java/javase/downloads/index.html"). That same page links to update 26 of java 6, which is the same version that you've installed.

---

### Post by WubiAR on 2011-08-01
> **Toz said:**
> The version you installed is a newer version than the bin you downloaded. Also note, that Oracle has recently released Java version 7. See: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html). That same page links to update 26 of java 6, which is the same version that you've installed.

Ok if I am to install the latest version, how do I get rid of the previous ones? Should I just delete them off from my usr/lib/jvm/(version of Java folder here)

---

### Post by Clayton7510 on 2011-08-01
You should be able to install either Sun Java from Oracle or OpenJDK.

If you are going to install either of these, then you should do it through apt-get (i.e. the package manager service).  

I personally use OpenJDK.  To install it, type the following at the command line:

*sudo apt-get install openjdk-6-jre*

To install Sun Java, type the following at the command line:

*sudo apt-get install sun-java6-jdk*

If Ubuntu can't find it then open Ubuntu Software Center and Select *Edit->Software Sources... *then make sure that every software source is checked under *Downloadable from the Internet *and *Other Sources*.  Now try the terminal command *sudo apt-get update* and try to install again.  Everything should work as expected.

-Clayton
[http://www.claytonstechnobabble.com](http://www.claytonstechnobabble.com)

---

### Post by Toz on 2011-08-01
> **WubiAR said:**
> Ok if I am to install the latest version, how do I get rid of the previous ones? Should I just delete them off from my usr/lib/jvm/(version of Java folder here)

You can get rid of the other versions by uninstalling them through the Software Centre. However, you can have multiple java versions installed. Ubuntu uses the alternatives method to specify which java implementation is the active implementation.

From a command line, to list installed java vms, run:
```
sudo update-java-alternatives --list
```
To set one as the current active vm, you can run:
```
sudo update-java-alternatives --set <vm>
```
where <vm> is one of the vms from the previous command.

For more help, try:
```
sudo update-java-alternatives
```
or
```
man update-java-alternatives
```

This method allows you to more easily jump between versions and implementations.

---

### Post by YesWeCan on 2011-08-01
If you want the latest, download it from here [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
into the directory you want to extract it to. Then extract it. For example:
tar zxvf jdk-7-linux-x64.tar.gz

---

### Post by Clayton7510 on 2011-08-19
I have noticed more than a few people having questions about this topic.  If you want the Sun/Oracle JDK (which also comes bundled with the JRE) then download it from here: [http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u27-download-440405.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u27-download-440405.html).  Get the self extracting executable.

After you run and install the self extracting executable, then update your Java profile to use what you just installed by using the following commands:

s[I]udo update-alternatives --config javac
[/I]s[I]udo update-alternatives --config java

[/I]If you need a more detailed explanation, check out the post I put up about this subject: [http://www.claytonstechnobabble.com/2011/08/installing-java-jdk-on-linux.html](http://www.claytonstechnobabble.com/2011/08/installing-java-jdk-on-linux.html)

If you still have questions then you can email me directly from the 'Contact Me' link on the page in my signature.

-Clayton
[http://www.claytonstechnobabble.com](http://www.claytonstechnobabble.com)

---

