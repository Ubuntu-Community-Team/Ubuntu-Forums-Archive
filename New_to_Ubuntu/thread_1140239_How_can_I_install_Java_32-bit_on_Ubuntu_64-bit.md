---
title: "How can I install Java 32-bit on Ubuntu 64-bit?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by looi76 on 2009-04-27
Hi, I couldn't find a How-to tutorial that explains how to install 32-bit Java on Ubuntu 64-bit. I have a fresh copy of Ubuntu Jaunty installed and I want to install Java on Firefox. Can someone please explain that to me?

---

### Post by NESFreak on 2009-04-27
> **looi76 said:**
> Hi, I couldn't find a How-to tutorial that explains how to install 32-bit Java on Ubuntu 64-bit. I have a fresh copy of Ubuntu Jaunty installed and I want to install Java on Firefox. Can someone please explain that to me?

sudo apt-get install ia32-sun-java6-bin

but the normal java runs perfectly fine on firefox. U see, jar files are architecture independent.

normal java flash and many others can easily be installed using

sudo apt-get install ubuntu-restricted-extras

---

### Post by SuperSonic4 on 2009-04-27
What's wrong with the 64 bith plugin?

---

### Post by looi76 on 2009-04-27
I have installed ubuntu-restricted-extras but Java didn't get installed with it. Is there a way to force 32bit to get installed because I don't think 64bit Java will run web applets properly.

---

### Post by SuperSonic4 on 2009-04-27
The 64bit version of java is running perfectly within firefox on my box.

[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/) explains it all

---

### Post by NESFreak on 2009-04-27
> **SuperSonic4 said:**
> The 64bit version of java is running perfectly within firefox on my box.

[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/) explains it all

you could switch to the sun version by running
```
sudo update-alternatives --config java
```

---

### Post by stchman on 2009-04-27
> **looi76 said:**
> Hi, I couldn't find a How-to tutorial that explains how to install 32-bit Java on Ubuntu 64-bit. I have a fresh copy of Ubuntu Jaunty installed and I want to install Java on Firefox. Can someone please explain that to me?

SUN Java (except browser plugin) is 64 bit compatible.

I use icedtea as my plugin and openjdk for Java.

```
sudo apt-get install icedtea6-plugin openjdk-6-jdk
```

---

### Post by bkieser on 2009-09-16
> **SuperSonic4 said:**
> What's wrong with the 64 bith plugin?

There are many problems with 64 bit Java on Ubuntu. For example, Webex, won't run. Here is a quote from the Webex support desk that I received:
[INDENT][I]
WebEx will support any Linux distribution as long as it meets the following requirements: 

Kernel: 2.6 or above 
X Lib: X11R6 or above compatible 
C++ Lib: libstdc++ 6 
Desktop Environment: XFce 4.0 or above, KDE, Ximian, Gnome 
GDK/GTK+ version: 2.0 or above 
Glib: 2.0 or above 
Sun Java 1.5 or above 

But 64-bit Ubuntu Linux currently does not work with WebEx and hence you are having difficulties to start the Event. However it supports 64-bit Fedora 10/11 Linux OS[/I][/INDENT].

Other software items that won't run: JBuilder, 3rdRail, many browser applets.

Sure you can get a lot of them to sort-of start up. On the face of it, without properly using them, you could even think that many of the problem items are actually working. But when you start to use them, there are very serious problems.

Even Sun's own Netbeans has problems with 64bit Java on Ubuntu (well, I run Kubuntu).

SWT seems to be a major problem area. There are numerous screen-related issues with 64bit Java on Ubuntu right now (Jaunty) in my experience. These range from race conditions to sometimes the keyboard will just stop getting input or screen items will simply not allow themselves to be clicked.

In Web-ex, the info panel will appear but no more tabs will be able to be opened.

And forget 64bit Java being able to interface with the sound system! Just doesnt happen. It can't detect the devices or when it does, they simply don't work together.

However, having said that the sound system is still in a shocking state with 64bit. My Skype is very hit and miss, Adobe AIR is a nightmare.

And on top of all that, we frequently lose working systems because upgrades tend to install non-working configs. For example, we need to keep a resident copy of the firefox flash and Java libs because upgrades so frequently blat them. Especially flash. We never know if it will be working or not. Constantly having to recopy the libs over.


IMHO 64 bit Ubuntu is very much pre-Alpha.

---

### Post by QIII on 2009-09-16
> **bkieser said:**
> 
 Even Sun's own Netbeans has problems with 64bit Java on Ubuntu (well, I run Kubuntu).
 
 IMHO 64 bit Ubuntu is very much pre-Alpha.
 
 64 bit Ubuntu "pre-Alpha"?  Not IMHO.  I've had virtually no problems with 64 bit Jaunty and had very few with 64 bit Intrepid.

Your genuine issues with WebEx may be with WebEx.  Maybe they aren't ready.  If you take a look at what you posted, you have to understand what "it" means in the following sentence.

"*However it supports 64-bit Fedora 10/11 Linux OS"  "It" *is WebEx.  Thus, read "*However WebEx supports 64-bit Fedora 10/11 Linux OS"*.  Indicates to me that the other condition is that WebEx does not support Ubuntu.  But then one of my degrees is in the area of Modern Languages, so I could be reading it wrong.

Skype on Linux is a Beta.  

From Adobe: "64-bit binaries of AIR are not currently available. Running 32-bit AIR on 64-bit systems has not been fully tested"

I develop with Netbeans 6.7 in a 64 bit Ubuntu environment with 64 bit Java.  Unless I'm missing something, I'm not having problems.

Haven't had any problems with audio and 64 bit Java.

But then I do have a gray beard and bifocals, so it's entirely possible I'm just not seeing things right.

---

### Post by realgt on 2009-12-08
I'm running Karmic 64bit but i got webex working with IE 6 via crossover
(edit: this works for entering meetings and seeing others' shared screens but it crashes IE6 when trying to share desktop)

---

### Post by lbthrice on 2010-02-11
I need the 32 bit java on the 64 bit machine because Juniper Network Connect cannot work with the 64-bit java.  Everything else seems to run fine.  Did we decide the best way to install these javas side-by-side?

---

### Post by bedge on 2010-09-07
> **QIII said:**
> 64 bit Ubuntu "pre-Alpha"?  Not IMHO.  I've had virtually no problems with 64 bit Jaunty and had very few with 64 bit Intrepid.



I take issue with the above statement. 64 bit java support sucks. Nothing works. 
While I dislike blatant exaggerations like that, with 64 bit java, it's pretty close.

webstart is what a large number of apps use to kick off java execution, and it completely fails to work with 64 bit Sun and openjdk. You can't even just install a 32 bit java on a 64 bit machine because the problem is with the 32 bit library support. 

For just about all apps I use I have to resort to running a 32 bit chroot to get web based java apps to work.

The typical error is something like:

```

Exception in thread "thread applet-com.hp.ilo2.virtdevs.virtdevs.class-1" java.lang.UnsatisfiedLinkError: /tmp/cpqma-675ee9e3: /tmp/cpqma-675ee9e3: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1699)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1003)
	at com.hp.ilo2.virtdevs.DirectIO.<clinit>(DirectIO.java:87)
	at com.hp.ilo2.virtdevs.MediaAccess.devices(MediaAccess.java:183)
	at com.hp.ilo2.virtdevs.virtdevs.ui_init(virtdevs.java:363)
	at com.hp.ilo2.virtdevs.virtdevs.start(virtdevs.java:142)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1639)
	at java.lang.Thread.run(Thread.java:619)

```

Note the **"Possible cause: architecture word width mismatch"**

This may be the application's fault, but the one common element is the 64 bit java platform that can't run any of these apps.

Any "report your java version" site will work fine, but try run an embedded webstart based app, and you get the above.

And for all those people that claim "64 bit java is perfect, I don't know what you're complaining about" try using it for actual work and not just verifying that some web site can accurately report your java version.


Here's a list of apps that do not work with 64 bit java, period. Nor do they work with a 32 bit JRE on a 64 bit OS.

HP's iLO virtual media, netmeeting, webex, and just about any on-line net-session, net-meeting, web-conference you try to join.

---

### Post by Cavsfan on 2010-09-07
Check out the links in my sig. The one that says How to install Java has 32 bit instructions on the left 
and 64 bit instructions on the right. It has never failed me yet and works perfectly.

---

### Post by Cavsfan on 2010-09-07
Although I have never had any problem running 64 bit Java on my 64 bit machine. =;

---

### Post by bedge on 2010-09-07
> **Cavsfan said:**
> Although I have never had any problem running 64 bit Java on my 64 bit machine. =;

Why, does one have to discard all packaged java versions and go with an unmaintainable raw version?

Can someone not simply package a JRE/JDK version that works?

---

### Post by Cavsfan on 2010-09-07
> **bedge said:**
> Why, does one have to discard all packaged java versions and go with an unmaintainable raw version?

Can someone not simply package a JRE/JDK version that works?

I have no idea what you are talking about and my interest is also waining...
However, I hope the OP of this thread has benefited.

---

### Post by bedge on 2010-09-07
> **Cavsfan said:**
> I have no idea what you are talking about and my interest is also waining...
However, I hope the OP of this thread has benefited.

It's this lack of interest that has left this problem to fester for so long.

The link you refer to in your sig points to: 

[http://sites.google.com/site/easylinuxtipsproject/java"](http://sites.google.com/site/easylinuxtipsproject/java")

which says to remove all installed java packages, and then download a jre from:

[http://www.java.com](http://www.java.com)

This leaves you with a java installation that does not track upstream Ubuntu bug fixes or releases. It's completely detached from the packaging system. Essentially, it's not a maintainable solution.

Why should a user have to replace the distro supplied java at all? That is the source of the problem. 

It's fine to suggest a band-aid to fix an immediate need, but not to declare that said band-aid should be the accepted fix for a mainstream distro.

---

### Post by Cavsfan on 2010-09-07
> **bedge said:**
> It's this lack of interest that has left this problem to fester for so long.

The link you refer to in your sig points to: 

[http://sites.google.com/site/easylinuxtipsproject/java"]("http://sites.google.com/site/easylinuxtipsproject/java%22")

which says to remove all installed java packages, and then download a jre from:

[http://www.java.com](http://www.java.com)

This leaves you with a java installation that does not track upstream Ubuntu bug fixes or releases. It's completely detached from the packaging system. Essentially, it's not a maintainable solution.

Why should a user have to replace the distro supplied java at all? That is the source of the problem. 

It's fine to suggest a band-aid to fix an immediate need, but not to declare that said band-aid should be the accepted fix for a mainstream distro.


Take that **"** mark off of the end of the link and you have it. With the **"** at the end, it fails...

The OP stated this simple question [B]"Hi, I couldn't find a How-to tutorial that explains how to install  32-bit 
Java on Ubuntu 64-bit. I have a fresh copy of Ubuntu [COLOR="Red"]Jaunty[/COLOR]  installed and I want to install Java on Firefox. 
Can someone please  explain that to me?"[/B]

First you must make sure the multiverse repository is enabled.
[[color=blue]_How to enable the multiverse repository for [COLOR="Red"]Jaunty[/COLOR]._[/COLOR]](http://www.psychocats.net/ubuntu/sources)
The link in my sig. is for **Karmic**, but this link will [[color=blue]_install java for [COLOR="Red"]Jaunty[/COLOR]_[/COLOR]](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)

**bedge**, perhaps you should start your own thread with your own problem.

---

