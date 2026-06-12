---
title: "need some help following installation instructions"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by patchido on 2010-02-21
well, actually i dont know into which thread this should go but i guessed it sounds kind of noobish i am not able to install some thing, :( so here it goes


i am trying to install a thing called lejos into my ubuntu and also to my nxt brick (LEGO ROBOT) and i cannot manage to do it.. this are the installation instructions i found in the readme file.



```
On Microsoft Windows you can you the .exe installer to install leJOS NXJ. This is a GUI installer that leads you through all the steps detailed below. On other systems, or if you use the .zip distribution on Microsoft Windows, you need to do the following:

   1. Extract the files from the distribution. A lejos_nxj subdirectory will be created.
   2. Set the environment variable NXJ_HOME to the full path of the lejos_nxj directory.
   3. Add the lejos_nxj/bin directory to your PATH.
   4. On Linux and Unix Systems, you may need to set LD_LIBRARY_PATH to your lejos_nxj/bin directory in order for the leJOS NXJ Java Native Interface (JNI) libraries to be dynamically loaded, when required. On many systems this is best set in /etc/profile. On MAC OSX systems, you should set DYLD_LIBRARY_PATH instead. As the nxj commands and the example ant build scripts that come with leJOS NXJ set the java.library.path system property, it is not always necessary to set LD_LIBRARY_PATH or DYLD_LIBRARY_PATH. It is currently necessary if you use the Eclipse plugin.
   5. On Linux and Unix systems, depending on your privilege settings you might need to adjust the execution permissions in the bin directory.

On Linux and Unix systems other than MAC OS X, you will have to build the distribution first. To do so, switch to the build folder and run ant. You will need to ensure that the packages that leJOS NXJ is dependent on are on your system. To build the jlibnxt JNI library, which is used for USB access, you need the Development files for libusb (libusb-devel). Note that leJOS NXJ uses libusb, not libusb1. To build the jbluez library, you need the Development Libraries for Bluetooth applications (bluez-libs-devel). jbluez is only needed if you use the NXTCommBluez comms driver instead of the default NXTCommBluecove. If you do not need jbluez, you can remove the build of it from the build/build.xml file. Note that package names and descriptions may differ with different Linux distributions.
```


this i found it on this forums

> You certainly don't need windows to use nxj mindstorms. Just download the correct package: [http://lejos.sourceforge.net/nxj-downloads.php](http://lejos.sourceforge.net/nxj-downloads.php) and extract it to, let's say /opt/lejos_nxj for example. There's no need to 'install' anything, extracting will do. Afterwards you'll need to set up the necessary environment variables. These are the ones I have:
Code:

export NXJ_HOME=/opt/lejos_nxj
export PATH=$PATH:$NXJ_HOME/bin
export JAVA_HOME=/path/to/java

You can add them to .bashrc so they are set every time you login (you will need to relogin the first time to have them working). Note that you will also need the variable JAVA_HOME pointing to your java directory, but you might already have that one (remember to replace /path/to/java to the actual path). You can see if a variable (for example NXJ_HOME) has been set with:
Code:

echo $NXJ_HOME



---

### Post by quixote on 2010-02-23
The second set of instructions are more complete for a linux system, although the first one does list dependencies on that linux line.  I think I've seen most of the dependencies in synaptic, so you could install those the easy way first.  Then follow the second set of instructions for the program itself.  If you put it in /opt you will have to use sudo to extract, make directories, or anything else.

I don't know if this helps.  Come back with a more specific description of the problem, starting with the first one you bump into: which step are you at?  which command did you run?  what happened or didn't happen?

---

### Post by patchido on 2010-02-23
the problem is that i dont know what the ant command makes or export, or even what to fill the export commands with

---

### Post by patchido on 2010-02-23
i dont know what i did, but know i have gnu java instead of sun java

---

### Post by oldfred on 2010-02-23
this is part of my standard update to a new install:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by quixote on 2010-02-23
yeah, replace gnu-java with sun-java.  They're not equivalent, unfortunately, and lots of things work way smoother with the sun version.  Who knows?  That by itself might help solve of the problems. :)

---

### Post by patchido on 2010-02-24
i had sun java, but i dont know what happened and with all the recent movements it changed, and the command in the above post didnt work


```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts 
[sudo] password for pato: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
The following packages were automatically installed and are no longer required:
  libusb-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
pato@pato-laptop:~$ 

```

---

### Post by oldfred on 2010-02-25
No the command worked like it is supposed to, just that it saw that you already have the latest version installed. So 0 updates.

---

### Post by patchido on 2010-02-25
have a look at this


```
pato@pato-laptop:~$ which java
/usr/bin/java
pato@pato-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
pato@pato-laptop:~$ 

```

---

### Post by oldfred on 2010-02-25
i am running 64bit so that may make a difference.

fred@fred-laptop:~$ which java
/usr/bin/java
fred@fred-laptop:~$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)
fred@fred-laptop:~$

---

### Post by patchido on 2010-02-25
the problem is that i do have java 1.6 but it seems to not be active or something like that

---

### Post by patchido on 2010-02-25
this is the weird part



```
pato@pato-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
pato@pato-laptop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  libusb-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
pato@pato-laptop:~$ 

```

---

### Post by quixote on 2010-03-02
I still don't have any ideas for your original question, but I remembered that when I had trouble with my java install I followed the instructions here: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) . I had the same problem where it was reporting it installed, but it wouldn't run.

Or maybe you have it all sorted out by now? :D

---

