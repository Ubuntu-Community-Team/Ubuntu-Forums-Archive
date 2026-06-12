---
title: "Installing JRE"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by swissnife on 2010-11-30
Can somebody help me please. I am so lost with this. I just installed Ubuntu 10.04 LTS, and am completely new to Linux.

All  I want to do is be able to use websites that use Java applets on their  pages, but nothing seems so simple with Linux. The applets do not start.

The  IceTea plugin thing is enabled in FF, although I also disabled it. I  also logged in as su and tried the commands given below:

sudo apt-get install openjdk-6-jre-headless sun-java6-plugin sun-java6-fonts

and 

sudo apt-get install icedtea6-plugin

They  either come back and say that the latest version of whatever is  installed, or stuff like "Package sun-java6-plugin has no installation  candidate"

Any help appreciated, but please explain in beginner's language; I really have little clue about Linux yet.

Thanks!

---

### Post by adwhitenc on 2010-11-30
The easiest way to do this would be to go into synaptic (System -> Admisistration -> Synaptic). Then you can browse to the package you want and install it.

---

### Post by lobralleo on 2010-11-30
Hi and welcome to the forums!
You started in the right direction: the key package to use Java-based applet is indeed sun-java6-plugin .

If you have IcedTea installed, you can try and uninstall it: I noticed that sometimes the two packages conflict with each other.
So, just open a terminal and type in:

sudo apt-get remove icedtea*

After that, go to System > Administration > Synaptic Package Manager and, when Synaptic is open, click on Settings > Repositories ; chose the "Other software" tab and select the entry called "Canonical Partners" (Synaptic is the graphical package manager that provides a frontend to apt-get commands and can make things easier: you just search for a package, select it and install it). This whole procedure enables the repository where the Sun Java packages are kept.

Now just install sun-java6-plugin from Synaptic or command line and you should be set to go: just restart Firefox and you should be able to enjoy Java-based content.

You can check if the plugin is operational by opening Firefox and typing about: plugins in the address bar: Firefox will open a page with a breakdown of all active plugins.

Good luck and enjoy Ubuntu! :)

---

### Post by stoogiebuncho on 2010-11-30
There's a couple of steps involved in switching to Sun's Java instead of Ubuntu's default open-source version, but it's pretty easy if you copy-paste these commands.

You can't install sun java right now because it's not in the Ubuntu repository.  So the first thing you need to do is add the Medibuntu repository.  Enter this command in a terminal (in a terminal window, use Ctrl+Shift+V for "paste")
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
**edit: I see from lobralleo's post that you may not need the Medibuntu repository if you enable the "Canonical Partners" sources.  It might be worth it to skip this command and try that first.

Next, install sun java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Finally, set sun java as the default:
```
sudo update-java-alternatives -s java-6-sun
```

That last command will likely return a number of errors.  That's normal.  You can ignore them.

You should be using sun java now.

---

### Post by lobralleo on 2010-11-30
Actually the Sun Java packages are not in Medibuntu:

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)

I believe it's in the Partner repositories in Maverick, or in the Universe repository in Lucid and earlier releases (not sure about this, though).

---

### Post by swissnife on 2010-11-30
Thanks for all the comments and suggestions guys. Much appreciated. I will be giving them a whirl later on! 

Thanks again.

---

### Post by swissnife on 2010-12-04
Hi,

Tried the suggestions but not getting very far.

Tried installing sun-java-bin and sun-jave-jre from the Synaptic thingy but was getting messages "could not mark all packages for installation or upgrade"

Tried the other commands, but also got errors:

sudo apt-get install sun-java6-jre sun-java6-plugin

gave "Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

and 

sudo update-java-alternatives -s java-6-sun

gave "update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun"

Suffice to say that Java is still not working in the browser. Any suggestions. Can't believe that it's this difficult to do something that should be so easy.

---

### Post by lykeion on 2010-12-04
It's easy if you do things in the right order.
[LIST=1]
[*]Close all package managers (synaptic, ubuntu software center)
[*]Start a terminal (Applications > Accessories > Terminal)
[*]Uninstall icedtea6-plugin, enter this command in terminal:
(if it says it's not installed it's ok, go to next step)```
sudo apt-get remove icedtea6-plugin
```
[*]Enable partner repository, enter this command in terminal:
(if you use 10.10 just change lucid to maverick)```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
[*]Install sun-java6-plugin, enter this command in terminal:
```
sudo apt-get install sun-java6-plugin
```
[*](Re)start browser and go to java plugin check page:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
[/LIST]

Note:
Thread title is "Installing JRE" but in first post you say you want "to use websites that use Java applets on their pages". 
Just for clarification:
JRE = Java Runtime Environment, i.e. the Java Virtual Machine (JVM), core classes, and supporting files
Java Browser Plugin = establishes a connection between popular browsers and the Java platform. This connection enables applets on Web sites to be run within a browser on the desktop.

---

### Post by swissnife on 2010-12-04
Hi

Thanks for the response, but just tried all of that and still not working. The first two commands work okay, but the third one does the following:

~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

... and then, just checking the Java test page which you provided, it comes back with "Something is wrong. Java is not working."

Any ideas?

---

### Post by lykeion on 2010-12-04
"Package sun-java6-plugin is not available"
That means apt-get can't find this package in the repositories.
Either you didn't succeed in enabling the Partner repository, or you need to update the repositories, like this: ```
sudo apt-get update
```Then try to install sun-java6-plugin again.

If that doesn't help I'd like you to paste output of some commands for troubleshooting.
And _please wrap output in CODE tags when posting it here for readability_, using the # button.

1. Paste the output of this command:```
cat /etc/lsb-release
```
2. Paste the output of this command:```
cat /etc/apt/sources.list
```

---

### Post by swissnife on 2010-12-04
Ah, that's much better ... I've done what you suggested and it installed okay, and is now working fine!

Thank you very much for your help, I appreciate it!

---

