---
title: "Deleting entries from Applications menu"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by Linux_will_prevail on 2011-06-18
I uninstalled a programs from my computer. The files are gone I guess because I cant run them any more but I can still see their names in the applications menu. Please help me remove these entries. I am totally new to Linux so please be patient too.

---

### Post by mikewhatever on 2011-06-18
What version of Ubuntu do you use?

---

### Post by Linux_will_prevail on 2011-06-18
I am using Ubuntu 10.04 LTS.

---

### Post by kryos on 2011-06-18
Right click applications/edit menus and take it from there.

---

### Post by Linux_will_prevail on 2011-06-19
Thanks Kryos. I have one more question. I have this application I installed which shows up in the applications menu but it doesn't run. I guess there's some problem with the application. Now that I want to uninstall it, it doesn't show up at all in either Ubuntu software center or Synaptic package manager. This is a program I never uninstalled and is just stuck in my system, hidden in some "undisclosed location". lol.

---

### Post by mikewhatever on 2011-06-19
What's the application and how was it installed. For example, if you compiled something from source, it will not show in Synaptic, and you'll need to run something like **make clean** from the source folder.

---

### Post by Linux_will_prevail on 2011-06-19
The application is TickInvest. I downloaded a file from the internet with file extension .sh and followed the instructions. Does that mean I compiled it from source and installed it? If that's the case how do I remove it?

---

### Post by mikewhatever on 2011-06-19
It's really hard to tell, as the .sh must have been the installation script, and one would have to see it to know what it did. It could have compiled from source, or coped binaries and config files all over.

---

### Post by Linux_will_prevail on 2011-06-19
After I entered the command sudo bash '/home/name/Downloads/TickInvest_1_0_5.sh' in the terminal I saw the following two lines come up as the application got installed:

Unpacking JRE ...
Preparing JRE ...
Starting Installer ...

I also noticed a new folder was created in the within the same folder where the .sh file was located. Does that help in any way. Also I want to try to run "make clean" from the source folder. How do I do that? Please let me know.

---

### Post by mikewhatever on 2011-06-19
JRE could be Java Runtime Environment, which suggests that it may have been a Java application, but I still don't know how to uninstall it. As said, you have to see the script to know what it did.
To run 'make clean' you need the source folder. Do you have it? If so, change to it and run 'make clean'.

---

