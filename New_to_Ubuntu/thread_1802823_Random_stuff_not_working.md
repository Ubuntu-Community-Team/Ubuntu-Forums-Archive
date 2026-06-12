---
title: "Random stuff not working"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-07-12
My webcam, and minecraft have stopped working.  They open, then the window disappears.  Ive recently been fighting with CCSM not sure if that would have any effect.

---

### Post by DarrenMR415 on 2011-07-12
There has been several updates to minecraft since its stopped working, which makes me very sad, since I cant play.

---

### Post by CatKiller on 2011-07-12
> **DarrenMR415 said:**
> Ive recently been fighting with CCSM not sure if that would have any effect.

Maybe.

Try running them in a Terminal so that you get to see any error messages. It might shed some light on the matter.

---

### Post by DarrenMR415 on 2011-07-12
How do I do that?

---

### Post by DarrenMR415 on 2011-07-12
I did alt-F2 and grabbed the minecraft Jar.  Terminal opened for a second, then closed.

---

### Post by CatKiller on 2011-07-12
> **DarrenMR415 said:**
> How do I do that?

Applications -> Accessories -> Terminal.

Type in the command to launch the program you're trying to run.

Error messages then have a place to go.

---

### Post by DarrenMR415 on 2011-07-12
My issue is not knowing the command.

---

### Post by CatKiller on 2011-07-12
> **DarrenMR415 said:**
> My issue is not knowing the command.

How were you running them before?

---

### Post by DarrenMR415 on 2011-07-12
Icon on the desktop.

---

### Post by CatKiller on 2011-07-12
> **DarrenMR415 said:**
> Icon on the desktop.

I'm assuming that means that you've got a file on your Desktop. I take it from your earlier post that it's some kind of .jar file.

```
java -jar ~/Desktop/NameOfTheJARFile.jar
``` (case-sensitive) might be what you want. I've not used such a thing myself.

---

### Post by DarrenMR415 on 2011-07-12
> **CatKiller said:**
> I'm assuming that means that you've got a file on your Desktop. I take it from your earlier post that it's some kind of .jar file.

```
java -jar ~/Desktop/NameOfTheJARFile.jar
``` (case-sensitive) might be what you want. I've not used such a thing myself.

Unable to access jarfile /home/darren/desktop/minecraft.jar

---

### Post by wildmanne39 on 2011-07-12
Hi, you might want to run a disk check just to be on the safe side by opening disk utility.

---

### Post by Zombie_Z on 2011-07-12
HI I'm fairly new to UBUNTU, Love it so far, Using 11.04 on a high end  AMD machine, anyways to my point, I was trying to enable desktop cube,  and after attempting to do that, I no longer have a border around  several windows.... PLEASE HELP, Very frustrating. Also, possibly key  info, I have Unity disabled, and it was all fine right before i tried  using the cube.  Flustered.

Kind of a bummer. Im pretty new to Ubuntu, and advanced computing.

---

### Post by Zombie_Z on 2011-07-12
!!!DISREGARD MY LAST POST, FOUND MY SOLUTION!!!     Thank god for genius' with signatures ;) u know who you are!!


Didnt't look hard enough for the solution.

---

### Post by wildmanne39 on 2011-07-12
> **Zombie_Z said:**
> !!!DISREGARD MY LAST POST, FOUND MY SOLUTION!!!     Thank god for genius' with signatures ;) u know who you are!!


Didnt't look hard enough for the solution.Hi, here is a guide to setup the cube in natty.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by DarrenMR415 on 2011-07-12
> **wildmanne39 said:**
> Hi, you might want to run a disk check just to be on the safe side by opening disk utility.

Im still not very good with all this.  I opened disk utility, but I dont see an option for disk check.  I do see "check filesystem" but it wont let me run that because it says the device is busy.

---

### Post by wildmanne39 on 2011-07-12
> **DarrenMR415 said:**
> Im still not very good with all this.  I opened disk utility, but I dont see an option for disk check.  I do see "check filesystem" but it wont let me run that because it says the device is busy.Hi, on the right of the window it says smart status and right underneath that is says smart data click on that and see what it says, choose the disk partition that ubuntu is on first, you might only have one.

---

### Post by DarrenMR415 on 2011-07-12
Self test complete ok
bad sectors none
overall assessment disk is healthy.

---

### Post by wildmanne39 on 2011-07-12
> **DarrenMR415 said:**
> Self test complete ok
bad sectors none
overall assessment disk is healthy.
Hi, thats is good, a lot of times when someone starts having a lot of programs not working properly it is due to file corruption because of bad sectors in a hard drive. 

I am not sure what is causing your problem I have never used the programs you are talking about. 

A lot of the time to open a program in a terminal you just type the name of the program you want to run, but I do not know if that will work with your program but you can try that, if it will open it that will give error messages that can help to fix the problem.

---

### Post by alquery on 2011-07-12
> **DarrenMR415 said:**
> Unable to access jarfile /home/darren/desktop/minecraft.jar

There might be two issues with the command you entered: first, you might have to capitalize Desktop, since folder and filenames are case sensitive. So
```
java -jar ~/**D**esktop/minecraft.jar
```

Also, your file might not be a .jar file at all, but maybe a .desktop file? If the file on your desktop has no visible extension, then that is probably the case.

---

### Post by CatKiller on 2011-07-13
> **DarrenMR415 said:**
> Unable to access jarfile /home/darren/desktop/minecraft.jar

It's case-sensitive. desktop and Desktop are not the same. minecraft and MineCraft are not the same.

---

### Post by DarrenMR415 on 2011-07-13
darren@darren-laptop:~$ java -jar ~/Destop/minecraft.jar
Unable to access jarfile /home/darren/Destop/minecraft.jar



The minecraft.jar is "minecraft.jar".

---

### Post by alquery on 2011-07-13
> **DarrenMR415 said:**
> darren@darren-laptop:~$ java -jar ~/Destop/minecraft.jar
Unable to access jarfile /home/darren/Destop/minecraft.jar



The minecraft.jar is "minecraft.jar".

Because "Desktop" is misspelled "Destop" in both cases, it leads me to believe that the command was typed in wrong (as you probably did not manually type out the error you got from your console.)

Try copying (Ctrl-c) and then pasting (Ctrl-Shift-V) into terminal the command:

```
java -jar ~/Desktop/minecraft.jar
```

---

### Post by DarrenMR415 on 2011-07-14
> **alquery said:**
> Because "Desktop" is misspelled "Destop" in both cases, 

:(

> darren@darren-laptop:~$ java -jar ~/Desktop/minecraft.jar
16 achievements
151 recipes
Setting user: slipmagt, -1411550721681694701
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x81066ef6, pid=9692, tid=2185231216
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/darren/hs_err_pid9692.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted
darren@darren-laptop:~$ 

I opened the pid9692, its quite long, should I still post it here?

---

### Post by CatKiller on 2011-07-14
> **DarrenMR415 said:**
> 
```
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x81066ef6, pid=9692, tid=2185231216
```

Yay! We've got to the point where we can start diagnosing the problem.

Doesn't look like it's Compiz-related, it's that Java is segfaulting.

> I opened the pid9692, its quite long, should I still post it here?

Possibly in a new thread. I doubt anyone that knows about this is going to get to this point in this thread. Something like "Java Segfaults on Minecraft" would be a better title. If you put the error log in Code tags, it will make your message easier to read.

I don't use Java, so I can't help with your particular problem. Someone else might have more of a clue. You could see if you have more luck using OpenJRE rather than Sun's JRE in the meantime.

---

