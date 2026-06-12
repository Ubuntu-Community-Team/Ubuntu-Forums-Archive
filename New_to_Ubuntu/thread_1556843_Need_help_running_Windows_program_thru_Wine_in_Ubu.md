---
title: "Need help running Windows program thru Wine in Ubuntu - java error?"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Asteria on 2010-08-20
Recently, my HP laptop decided to crash (WindowsXP). After hours and hours of hitting my head against a(n internet) wall full of unhelpful advice, and restraining myself from throwing the poor machine against the wall, I managed to find my way in to the files I needed and put them on an external hard drive. I then decided to give up on Windows completely and try something new, which led me to Ubuntu. So, obviously I am a definite n00b when it comes to this OS, and I need some help. The reason I spent so long trying to get files off my old hard drive was because I have literally hundreds of hours of research on there. I got the files, but my writing program (WriteItNow4) is a Windows executable. I installed and got Wine running, and marked the file as executable. The program starts to load, and then hits me with this error: 

"No JVM could be found on your system. Please define EXE4J_JAVA_HOME to point to an installed 32-bit JDK or JRE or download a JRE from Java.com"

So, what do I do now? Is there a way I can change something through Terminal? I have (according to java - version in Terminal) "Java version 1.6.0_18 OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-Oubuntu1) OpenJDK Server VM (build 16.0-b13, mixed mode)"

It is IMPERATIVE I can gain access and continue to work on these files!!! Remember, I am new to Ubuntu, so please use layman's terms (and step-by-step instructions, if possible) for this poor soul. I really appreciate any help I can get for this issue.

If more information is needed, I can provide!


(A side question, not really relevant, is there a way to change the appearance of the hibernate login screen? I'm not really digging the plain black.)

---

### Post by retrovirus-007@juno.com on 2010-08-20
Asteria, the WineHQ is designed to execute Windows applications so it will attempt to follow to the application's instructions.

Your terminal belongs to the Ubuntu OS kernel, so it may read on the Java language on Ubuntu by default. Your Windows applications will certainly not accept the Java standard from Ubuntu. My best bet is to install a Java Runtime Environment for Windows (I guess the Java language was not as versatile as I thought it would be).

In the link below, you can find a list of Java Runtime Environments for a Windows operating system (and JRE required Windows applications):
[http://www.oldapps.com/java.php]("http://www.oldapps.com/java.php")

---

### Post by JBAlaska on 2010-08-20
Just install Java under WINE. According to [WINEhq](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6626) ver 6 is your best bet.

---

### Post by Asteria on 2010-08-20
Great! Thanks for helping so quickly. I can't believe I didn't think of doing that in the first place, since it makes perfect sense!

I'm not getting an error anymore, but now when I click on the .exe file (there's a .jar one as well that I have tried) the stupid program acts like it is loading and then nothing happens. This is a total shot in the dark since I can't narrow it down to a specific problem area, but, any ideas? Both the exe and jar are marked as executables as well as to open with Wine/Java.

---

### Post by retrovirus-007@juno.com on 2010-08-20
Sometimes, the program takes a while to load. WineHQ (in theory) suppose to make Windows applications work. I must say that my first letdown about Ubuntu is that WineHQ cannot cover Microsoft's Office products. I tried installing the MSWord2002 from the CD, and then there was just this blank. I do not know if I actually succeeded or not, but I can tell that there are going to be some (copyright/copyleft/trademark/patent) problems between the fabled monopoly and let us go with consumers.

I heard that VirtualBox is like another solution, but you should see the screenshots for yourself ("[http://www.virtualbox.org/wiki/Screenshots]("http://www.virtualbox.org/wiki/Screenshots"). Virtualbox could make the machine go a bit slower.

My logic boils down to using a program (regardless of its nature) that is easily distributable and could do the same as WriteItNow4. The saved file format would be the most essential component. 

I read from [http://www.winehq.org/pipermail/wine-users/2008-March/030309.html]("http://www.winehq.org/pipermail/wine-users/2008-March/030309.html") that yWriter might be a good enough substitute. [http://www.spacejock.com/yWriter.html]("http://www.spacejock.com/yWriter.html")

~update (08/20/2010):
It looks like this was not the first time WineHQ had a tangle with the WriteItNow program.
[http://www.winehq.org/pipermail/wine-users/2008-March/030296.html]("http://www.winehq.org/pipermail/wine-users/2008-March/030296.html")

~update (08/20/2010):
I have found a possible workaround here. [http://ubuntuforums.org/showthread.php?t=610721]("http://ubuntuforums.org/showthread.php?t=610721")

---

### Post by hankaaron88 on 2010-08-20
Wine does serve it's purpose, but I have found that VirtualBox runs programs much better. You will need to install an os in the virtual machine. Here is a link to a good copy of xp. I use it and it passes wga.
[http://thepiratebay.org/torrent/5199210/WINDOWS_XP_PRO_32-BIT_SP3_ISO_ACTIVATED_GENUINE](http://thepiratebay.org/torrent/5199210/WINDOWS_XP_PRO_32-BIT_SP3_ISO_ACTIVATED_GENUINE)

---

