---
title: "loading java in wine?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by mikeprosceo on 2010-06-09
I have a program from work that is windows based.  I am running ubuntu 10.04, have the latest version of wine and linux based java.  When I try to install the program using wine I get a message that I need java.  Yet when I go to the java web page it says I have it.  It seems the windows program doesn't see it.  When I try to load a windows based java in wine I get an error stating that there might be a problem with wine.  Yet wine opens other windows based programs I use.  Do I need to load a windows based java in wine?  If not how do I get my linux based java to work or be seen by the work program I am trying to load.  It is an exe file.  Can anyone help or tell me where to go for help.  Thank You - Mike

---

### Post by dvanrensburg on 2010-06-10
What is the name of the application you are trying to run?

Is is strange that the application will be dependent on Java and be a Windows based at the same time. Even though it is a .exe file it sounds like a Java application which means it should run fine on both Windows and Linux. Some times developers make Java applications start natively on Windows by distributing a .exe which just starts the Java application in the virtual machine.

Generally you can download a Linux version of the application but it might even be possible to start the application as is if you can figure out the main .jar file of the application.

---

### Post by gandaran on 2010-06-10
> Do I need to load a windows based java in wine?
yes if you install a windows based program in wine, if it needs java then it can only work if java is installed in wine too.
just grab the windows java package and install it in wine but I recommend installing the sun java 6 update 7, it works better in wine than other versions, you can download all old versions from java.com

---

### Post by mikeprosceo on 2010-06-10
I did finally get java to load in wine.  Now however when I try to open my work specific windows program I get an error message that hh.exe in java has a problem.  I tried reinstalling java but still get the same message. The windows program I am trying to run is s400.exe. I know this seems to be a java problem but any ideas or where I can get some.  I emailed java the problem but it is important I get this solved or I will have to install windows back on my computer.  (ugh)  Thanks - Mike

---

### Post by mikeprosceo on 2010-06-11
This is the error I get when trying to load a windows based program in wine.  It seems to be a java error but it also says to see problematic frame for where to report the bug.  Anyone have any ideas, please??

The crash happened outside the Java Virtual Machine in native code.

# See problematic frame for where to report the bug.

#

A fatal error has been detected by the Java Runtime Environment:

#

#  Internal Error (0x80000101), pid=39, tid=54

#

# JRE version: 6.0_20-b02

# Java VM: Java HotSpot(TM) Client VM (16.3-b01 mixed mode windows-x86 )

# Problematic frame:

# C  0xf77e2425

#The crash happened outside the Java Virtual Machine in native code.

# See problematic frame for where to report the bug.

#

---

### Post by miji.nyan on 2010-11-03
I get a similar error when i try to run my applets in j creator. is there a way to fix this?

---

