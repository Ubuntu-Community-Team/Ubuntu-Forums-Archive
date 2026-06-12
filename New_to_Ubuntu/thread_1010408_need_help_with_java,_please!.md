---
title: "need help with java, please!"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by thehereaway on 2008-12-13
Okay, im trying to install java for like the hundredth time already. I've no idea what i'm doing, i'm just following these instructions...

[http://www.java.com/en/download/help/5000010500.xml#rpm](http://www.java.com/en/download/help/5000010500.xml#rpm)

I'm on step 7 (I *think* everything has worked so far, but i've no idea really) and i get this message in the terminal...

> root@Darren:/home/darren# rpm -iv jre-6u11-linux-i586.rpm
error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0_11-fcs.i586
        /bin/cat is needed by jre-1.6.0_11-fcs.i586
        /bin/cp is needed by jre-1.6.0_11-fcs.i586
        /bin/gawk is needed by jre-1.6.0_11-fcs.i586
        /bin/grep is needed by jre-1.6.0_11-fcs.i586
        /bin/ln is needed by jre-1.6.0_11-fcs.i586
        /bin/ls is needed by jre-1.6.0_11-fcs.i586
        /bin/mkdir is needed by jre-1.6.0_11-fcs.i586
        /bin/mv is needed by jre-1.6.0_11-fcs.i586
        /bin/pwd is needed by jre-1.6.0_11-fcs.i586
        /bin/rm is needed by jre-1.6.0_11-fcs.i586
        /bin/sed is needed by jre-1.6.0_11-fcs.i586
        /bin/sort is needed by jre-1.6.0_11-fcs.i586
        /bin/touch is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/find is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0_11-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0_11-fcs.i586
        /bin/sh is needed by jre-1.6.0_11-fcs.i586
root@Darren:/home/darren# 


I've no idea what i'm doing tbh, so if anyone knows an easier way to install java (that actually works) please let me know...i'm desperate!

Cheers.

---

### Post by L Campbell on 2008-12-13
> **thehereaway said:**
> Okay, im trying to install java for like the hundredth time already. I've no idea what i'm doing, i'm just following these instructions...

[http://www.java.com/en/download/help/5000010500.xml#rpm](http://www.java.com/en/download/help/5000010500.xml#rpm)

I'm on step 7 (I *think* everything has worked so far, but i've no idea really) and i get this message in the terminal...



I've no idea what i'm doing tbh, so if anyone knows an easier way to install java (that actually works) please let me know...i'm desperate!

Cheers.

Maybe these instructions will help you:-

[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

### Post by taurus on 2008-12-13
Why not just install the one from the repos?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
And when you get to the licensing screen, hit Tab to highlight the <OK> and Return to accept it.

Otherwise, download the .bin, _not_ the .rpm.bin version.

---

### Post by thehereaway on 2008-12-13
> **taurus said:**
> Why not just install the one from the repos?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
And when you get to the licensing screen, hit Tab to highlight the <OK> and Return to accept it.

Otherwise, download the .bin, _not_ the .rpm.bin version.

> darren@Darren:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  gnustep-base-common liblzo1 gnustep-base-runtime libtorrent10 mplayer-skins
  python-pygame libwxgtk2.8-0 libkdegames1 python-pyogg gcc-3.4-base
  python-imaging libggi2 libgii1 libgnustep-base1.13 nautilus-script-manager
  gnustep-common libwxbase2.8-0 libcrypto++6 libgii1-target-x libffcall1
  amule-common libobjc1 libg2c0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
darren@Darren:~$ 

It says already the newest version, but all the java tests on the internet say i don't have the latest versions and most websites that i need java for arent working.

---

### Post by taurus on 2008-12-13
What's the output of this command from a terminal?

```
java -version
```
Which release are you running?

```
lsb_release -a
uname -a
```

---

### Post by thehereaway on 2008-12-13
> **taurus said:**
> What's the output of this command from a terminal?

```
java -version
```
Which release are you running?

```
lsb_release -a
uname -a
```


> darren@Darren:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

darren@Darren:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

darren@Darren:~$ uname -a
Linux Darren 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
darren@Darren:~$ 


[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

this says i'm using java 1.4.2

---

### Post by taurus on 2008-12-13
What's the output of this command?

```
sudo update-alternatives --config java
```

---

### Post by thehereaway on 2008-12-13
> **taurus said:**
> What's the output of this command?

```
sudo update-alternatives --config java
```

```
darren@Darren:~$ sudo update-alternatives --config java
[sudo] password for darren:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/cacao
*+        4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

---

### Post by taurus on 2008-12-13
In the address field of firefox, enter this line and see which version of java plugin you use.

```
about:plugins
```

---

### Post by thehereaway on 2008-12-13
> **taurus said:**
> In the address field of firefox, enter this line and see which version of java plugin you use.

```
about:plugins
```

It says...

Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

Then a load of things underneath it which are all enabled

---

### Post by taurus on 2008-12-13
Not sure why that test page says you are running version 1.4 since it says I am running 1.6.  Go into synaptic and try to remove the gij-4.2.  Then restart firefox.

---

### Post by thehereaway on 2008-12-13
> **taurus said:**
> Not sure why that test page says you are running version 1.4 since it says I am running 1.6.  Go into synaptic and try to remove the gij-4.2.  Then restart firefox.

I did that, and it still says 1.4.2 (by restart you do just mean like close down and start back up again yeh?) 

Is it possible it's not installed properly or something?

---

### Post by albinootje on 2008-12-13
Can you show the output of :

locate libjavaplugin.so

---

### Post by thehereaway on 2008-12-13
> **albinootje said:**
> Can you show the output of :

locate libjavaplugin.so

```
darren@Darren:~$ locate libjavaplugin.so
/usr/lib/iceape/plugins/libjavaplugin.so
/usr/lib/xulrunner/plugins/libjavaplugin.so
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/midbrowser/plugins/libjavaplugin.so
/usr/lib/iceweasel/plugins/libjavaplugin.so
/usr/lib/firefox/plugins/libjavaplugin.so
darren@Darren:~$ 


```

---

### Post by albinootje on 2008-12-13
Hmm :( that's actually the same as i have.
I actually hoped to see a java plugin in your ~/.mozilla/ plugins directory which was causing the conflict in version numbers.

---

### Post by thehereaway on 2008-12-13
> **albinootje said:**
> Hmm :( that's actually the same as i have.
I actually hoped to see a java plugin in your ~/.mozilla/ plugins directory which was causing the conflict in version numbers.

Dam, any other ideas?

---

### Post by albinootje on 2008-12-14
Which browser did you use ? Firefox ?
Can you try with other browsers like Galeon, Konqueror, and Epiphany-browser, and check the java-test page ?
With the idea to find out where the problem is located.

---

### Post by mitso on 2008-12-14
Try this :

System - Administration -Synaptic Package Manager
Click on search -put in "sun java"
Go down to "sun-java5-plugin
Click on box
Click on -Apply - which should be highlighted
Answer all questions as they come up.
This worked for my application when other  java's didn't.

Good luck

---

### Post by thehereaway on 2008-12-20
> **mitso said:**
> Try this :

System - Administration -Synaptic Package Manager
Click on search -put in "sun java"
Go down to "sun-java5-plugin
Click on box
Click on -Apply - which should be highlighted
Answer all questions as they come up.
This worked for my application when other  java's didn't.

Good luck

Hmm, didn't work for me unfortunately.


> **albinootje said:**
> Which browser did you use ? Firefox ?
Can you try with other browsers like Galeon, Konqueror, and Epiphany-browser, and check the java-test page ?
With the idea to find out where the problem is located.

I am using Firefox. Didn't have any of those other browers installed so tried Galeon and it still didn't work. :(

---

### Post by albinootje on 2008-12-20
> **thehereaway said:**
> Hmm, didn't work for me unfortunately.


So, the situation is that you want the latest java, but test pages say that you don't have the latest java, but an older version, right ?

I suggest that you remove all of the java packages in Ubuntu first.

Then follow the instructions here :
[http://ubuntuforums.org/showthread.php?p=6389802](http://ubuntuforums.org/showthread.php?p=6389802)
posting #3

---

### Post by thehereaway on 2008-12-20
> **albinootje said:**
> So, the situation is that you want the latest java, but test pages say that you don't have the latest java, but an older version, right ?

I suggest that you remove all of the java packages in Ubuntu first.

Then follow the instructions here :
[http://ubuntuforums.org/showthread.php?p=6389802](http://ubuntuforums.org/showthread.php?p=6389802)
posting #3

Ok, how do i properly remove all the java packages in Ubuntu? Do i use the synaptic?

---

### Post by albinootje on 2008-12-20
Removing it from Synaptic package manager is possible, but easiest is probably opening a terminal and typing :
```
sudo apt-get remove --purge sun-java5-* sun-java6-*
```

---

### Post by kansasnoob on 2008-12-20
After admittedly very limited experience I still suggest Untuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

More:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

