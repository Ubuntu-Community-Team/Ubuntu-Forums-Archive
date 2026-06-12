---
title: "Java"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by llmunro on 2010-04-27
Hi all,

I am trying to install Java Runtime Environment following these instructions:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)


First, it says to check if the multiverse repository enabled or not.  I think this is in Software Sources, and from what I can tell, this is enabled.

Then I try to install it in the terminal.
Here's what I get:

lisa@lisa-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6fonts
[sudo] password for lisa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Where am I going wrong?

Thanks.

Best,
Lisa

---

### Post by ttshivers on 2010-04-27
If you are running Ubuntu 9.10, then there is an easier way to install Java, and it will fix your problem.  Here are the steps:


[LIST=1]
[*]Click on applications
[*]click on Ubuntu Software Center
[*]Type Java in the search box
[*]Click on the arrow next to Sun Java 6 Runtime
[*]Click the button that says install
[*]That should fix your problem
[/LIST]

---

### Post by 2hot6ft2 on 2010-04-27
Are you running 9.04? That's what that guide is for.
Did you run
```
sudo apt-get update
```
before running
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6fonts
```?
If not then that's the problem.

---

### Post by llmunro on 2010-04-27
Aha...the fact that I am running the 10.04 RC might be the problem.  How would the instructions for 10.04 differ?  I assumed it would be a similar process, but you know what happens when we assume....! :P

Thanks for the help.
Best,
Lisa

---

### Post by QIII on 2010-04-27
In Lucid, simply enable the partner repo (System | Administration | Software Sources in the "Other Software" tab) and install it from Synaptic.  Install the sun-java6-xxx packages.  (Pay attention to 32 and 64 bit choices.)

---

### Post by StephenDavison on 2010-04-27
llmunro, are you wanting the Sun JRE specifically?  I'm pretty sure the OpenJDK JRE runtime was among the default packages installed when I put 10.04 on my machine, but that was pre-beta.  At any rate, you can find out by looking at the Installed Software in the Ubuntu Software Center app.  

sudo apt-get openjdk-6-jdk

should get you the jdk too.

---

### Post by QIII on 2010-04-27
OpenJDK should work well for most people.  And it is open source, in keeping with Canonical's philosophy of what should be available in its repos.

But, as said, it is a work in progress.  It's really close to being a perfect fit and the developers are working madly.

Unfortunately, some websites fail to recognize it -- primarily Windows-centric ones.

I have issues when clients specify Java.

---

### Post by _0R10N on 2010-04-28
If you want to install it through the repositories, I won't try to change your mind. But I must say that I'm a Senior Java Developer and when installing Java, I always prefer to download it from the Java site and running the installer myself. It's simple and never failed, until now...

Kind regards!

_0R10N >>

---

### Post by llmunro on 2010-04-28
Well, being quite new to Linux, I often times don't know precisely what I need, but here's what I'm trying to do:

[http://forums.zotero.org/discussion/10355/firefox-could-not-load-the-component-required-to-communicate-with-your-word-processor-/#Item_0](http://forums.zotero.org/discussion/10355/firefox-could-not-load-the-component-required-to-communicate-with-your-word-processor-/#Item_0)

I'll mess with it tomorrow and report back.

Thanks for all the help and comments!

Best,
Lisa

---

### Post by llmunro on 2010-04-29
Hi,

It appears that I am not doing something right, as I thought I had installed Sun Java, but still see in the terminal:

isa@lisa-desktop:~$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)


Would someone be able to walk me through this very slowly?

Thanks much.
Best,
Lisa

---

### Post by _0R10N on 2010-04-29
> **llmunro said:**
> Hi,

It appears that I am not doing something right, as I thought I had installed Sun Java, but still see in the terminal:

isa@lisa-desktop:~$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)


Would someone be able to walk me through this very slowly?

Thanks much.
Best,
Lisa

What this says is that  your $JAVA_HOME Environment Variable is pointing to a OpenJDK 1.6.0_18 installation. It doesn't mean that you haven't installed the packages that you've been trying to install. So, you must determine whether your java has been installed or not. A simply way to accomplish this is opening Synaptic and check if the package is marked as installed.

If the package appears as installed, you'll have to find where the java files were installed. To do so:
```
find / -name java-6*
```
When you get a valid location (a location of a directory containg /lib, /bin and the whole java stuff), you need to manually set the $JAVA_HOME Environment Variable, pointing to the directory you found. To do so:
```

sudo gedit /etc/profile

```
When the gedit opens, append this to the end of the file:
```

export JAVA_HOME=your_java_directory

```

Restart your system.

As I mentioned in a previous post in this thread, I always download the installer from the java site, move into the directory where I want the java installation to be, and execute the installer. After a minute I have it installed, then set environment variable, and ready to go!.

Kind regards!

_0R10N >>

---

### Post by r-senior on 2010-04-29
If you installed Sun's Java from the repositories, this should switch you to it:

$ sudo update-java-alternatives -s java-6-sun

---

### Post by llmunro on 2010-04-29
Thanks to everyone who made suggestions on this thread! I've learned a lot, that's for sure!

I did end up installing the Sun Java stuff through Synaptic and found that this

$ sudo update-java-alternatives -s java-6-sun 	

did the trick!  

I normally wouldn't have been so persistent about figuring this out, but this was necessary to get my Zotero OpenOffice plugin to work, which is what I'm using to cite my dissertation research.  I've just tested it and it works perfectly!

I have made notes about this for future reference!

Thanks to everyone for all of the help and patience! :)

Best,
Lisa

---

