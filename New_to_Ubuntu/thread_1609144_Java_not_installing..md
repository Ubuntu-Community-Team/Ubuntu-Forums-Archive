---
title: "Java not installing."
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Omnomnom on 2010-10-30
I tried to install the java runtime and browser packages from the Ubuntu software centre, and they seem to have installed properly, but when I open minecraft, or any other java web program, it doesn't think I have java installed. And when I type into the address bar in firefox, about : plugins, it isn't listed. Do I need to execute java every time I want to play minecraft or... What?

---

### Post by bioterror on 2010-10-30
> **Omnomnom said:**
> I tried to install the java runtime and browser packages from the Ubuntu software centre, and they seem to have installed properly, but when I open minecraft, or any other java web program, it doesn't think I have java installed. And when I type into the address bar in firefox, about : plugins, it isn't listed. Do I need to execute java every time I want to play minecraft or... What?

These commands in terminal

```

sudo apt-get purge openjdk-6-jdk openjdk-6-jre icedtea6-plugin
sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-fonts sun-java6-bin

```

And then head your browser to [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

---

### Post by GabrielYYZ on 2010-10-30
maybe try to delete the JRE you installed from the software center and reinstall it? i'm not 100% sure but i kinda remember the icedtea plugin for firefox installing itself with the restricted extras. 

maybe someone else, with better memory/knowledge of that particular plugin, can point you in a better direction.

---

### Post by Omnomnom on 2010-10-30
First command installed properly, second one spat out this

```
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
E: Unable to locate package sun-java6-bin
```

---

### Post by bioterror on 2010-10-30
> **Omnomnom said:**
> First command installed properly, second one spat out this

```
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
E: Unable to locate package sun-java6-bin
```

From software sources you should enable Canonical partners repository.

---

### Post by amateur_mav on 2010-10-30
First of all, java is installed with the Open Office suite. All you need to do, and I just did this because I didn't have Java enabled in Firefox, go to this URL  [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)  and when you try to see what version you have, Firefox will alert you that you are missing a plugin and that is the IceTea plugin that should get things working.  It installs perfectly.

---

### Post by Omnomnom on 2010-10-30
> **amateur_mav said:**
> First of all, java is installed with the Open Office suite. All you need to do, and I just did this because I didn't have Java enabled in Firefox, go to this URL  [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)  and when you try to see what version you have, Firefox will alert you that you are missing a plugin and that is the IceTea plugin that should get things working.  It installs perfectly.
Thanks!!!

---

### Post by Omnomnom on 2010-10-30
Wait no, when I try and play minecraft, it's just a blank screen. At least it detects I have java, small step forward.

Oh look at that, minecraft just popped up in a seperate window. Weird...

---

### Post by Omnomnom on 2010-10-30
Never mind, after it did the whole downloading thing, there was just a blank screen. Damnit! I want my minecraft Jeeves!

---

### Post by amateur_mav on 2010-10-30
Have you closed and restarted Firefox after installing the plugin? OK, go back to the Java website at this URL  [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)  and do an update install from there.  I haven't tried that yet 'cause I don't want to close my browser while I'm waiting for someone to answer my question.  Hope that works for you.

---

### Post by Omnomnom on 2010-10-30
How do you do an update install again? And yes I even restarted my computer, when it didn't work.

---

### Post by amateur_mav on 2010-10-30
I need to do a java update so I'm going to logoff here and see how it goes.  BRB

---

### Post by bioterror on 2010-10-30
> **amateur_mav said:**
> Have you closed and restarted Firefox after installing the plugin? OK, go back to the Java website at this URL  [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)  and do an update install from there.  I haven't tried that yet 'cause I don't want to close my browser while I'm waiting for someone to answer my question.  Hope that works for you.

You guys really make me frustrated.
I gave in the first place you correct instructions how to install sun-java6 -packages and you completely ignored that. Even tho people are suggesting to install random packages from Oracle's webpage and mess all the dependencies and automatic upgrades for java.

If you really want to play this: [http://www.minecraft.net/play.jsp]("http://www.minecraft.net/play.jsp") game, you really should read once again what I said about installing sun-java6-jre,bin,plugin and fonts. restart your browser and start playing, becouse that works on my Lubuntu 10.10 with Chromium 7.0.517.41 (62167) Ubuntu 10.10 running 
ii  sun-java6-bin                        6.22-0ubuntu1~10.10                               Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
ii  sun-java6-fonts                      6.22-0ubuntu1~10.10                               Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jre                        6.22-0ubuntu1~10.10                               Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
ii  sun-java6-plugin                     6.22-0ubuntu1~10.10                               The Java(TM) Plug-in, Java SE 6

So really, open synaptic or what ever you use, check software sources and tap check mark for the Canonical Partners repository, then sudo apt-get update, sudo apt-get install all the needed packages.

OpenJDK/icedtea has never worked for anything what I've needed or used.

---

### Post by Omnomnom on 2010-10-30
Sorry dude, everyone was eager to help or get posts or something.. 

Could you PM me the details again?

---

### Post by amateur_mav on 2010-10-30
Bioterror is kinda right. I downloaded the .bin file from the Java website, unpacked it easily but registering it eludes me.

In the Ubuntu Software Center from the Edit menu, select Software Sources and make sure all sources are selected.
With IcedTea installed, going to the Get Software from Canonical Partners and installing Java from there won't upgrade the version either. IcedTea needs to be purged first.
Bioterror's command "sudo apt-get purge openjdk-6-jdk openjdk-6-jre icedtea6-plugin" I found was written wrong - shoulda been just
```
sudo apt-get purge icedtea6-plugin icedtea-6-jre-cacao
```(but all the .deb packages will still remain along with a few files)

Now go to the Get Software from the Canonical Partners and install:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

This should take care of all your java problems, at least it worked for me after struggling all night trying to register my initial install.

---

### Post by gandaran on 2010-10-30
> **Omnomnom said:**
> Never mind, after it did the whole downloading thing, there was just a blank screen. Damnit! I want my minecraft Jeeves!
you need to remove the icedtea plugin and install only the sun-java plugin from the archive.canonical partner repository to properly run java applets!
enable the archive.canonical partner repo in software sources and update the software package list then you can find the sun-java packages in ubuntu software center or synaptic.

---

### Post by Omnomnom on 2010-10-30
So far it's working, this time the software agreement came up, thing is, I don't know how to get to the next page XD

---

### Post by Omnomnom on 2010-10-31
Alright, now it's working, but minecraft is just a black screen. Please explain. :(

---

### Post by Omnomnom on 2010-10-31
Ok, it loads the terrain, well apparently, but then, a grey screen. In minecraft I mean.

---

### Post by Omnomnom on 2010-10-31
Alright, now whenever I attempt to open a java app, firefox crashes. Gotta love how developers consider people using linux.

---

### Post by Omnomnom on 2010-10-31
Bumpy Bump

---

### Post by amateur_mav on 2010-10-31
I don't know what you did O but my install went flawless and minecraft works for me, 'cept I dont know how to navigate it. Even the java test install page at [Test  Java is working]("http://www.java.com/en/download/help/testvm.xml") shows I have the upgraded version working.

Have you tried using any part of Open Office? If you're having any problems with that then you will need to do a full uninstall of java and Open Office from the Ubuntu Software Center because that would mean that you corrupted the java installation somehow - and then re-install the Open Office Suite first and then the java updates - if they are needed. You will need the plugin for FireFox re-installed.

My last suggestion is to go to the Java Help Center at [http://www.java.com/en/download/help/index.xml](http://www.java.com/en/download/help/index.xml)

---

### Post by amateur_mav on 2010-10-31
..,

---

### Post by Omnomnom on 2010-10-31
Yes, that's working.

I can tell that it's minecraft then.

---

### Post by penanya on 2010-10-31
hi.. I'm having similar problem.. i want to install java compiler and i got this error

sudo apt-get install javac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package javac

how can i install java compiler then?

---

### Post by gandaran on 2010-10-31
> **penanya said:**
> hi.. I'm having similar problem.. i want to install java compiler and i got this error

sudo apt-get install javac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package javac

how can i install java compiler then?
'javac' doesn't exist in package manager, however there is one 'javacc' package but I don't know if thats what you want.
open synaptic package manager and type java in search box, go through the java packages, read the javacc description and if it is what you are looking for mark it for install.

---

### Post by Omnomnom on 2010-11-01
Now minecraft half loads, I can just see the landscape render, but then yet another white screen.

---

### Post by gandaran on 2010-11-01
> **Omnomnom said:**
> Now minecraft half loads, I can just see the landscape render, but then yet another white screen.
if that applet isn't working correctly then you must be using openjdk-java to run it.
sun-java works works very well in linux just as it does in windows so ensure thats what you have installed only.

---

### Post by beew on 2010-11-01
To check you have the right version of java enabled
type in the terminal
```
java-version
```
and check the output.

If you are using Open-java  you need to change the default to sun-java. Make sure you have installed the packages sun-java-bin, sun-java-jdk, sun-java-plugin and sun-java-jre from Synaptic like others have said before.

Then type in the terminal to make sun-java the default (alternatively you can also purge all the open-java packages)

```
sudo update-java-alternatives -s java-6-sun
```

---

