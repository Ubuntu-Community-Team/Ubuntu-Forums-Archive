---
title: "Minecraft keeps crashing"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by numb500 on 2011-06-03
Hey guys,

I'm having a problem with running Minecraft on Ubuntu 11.04 32 bit version. Everytime I want to enter a world or create a new one it keeps crashing. I already installed Sun Java but it still keeps crashing. Maybe it is a driver issue? I'm using the amd driver for my 5770.

---

### Post by Davaross on 2011-06-03
Try installing wine and the windows version of java as well as the windows executable. IMO it is much more stable via this method than running natively.

---

### Post by numb500 on 2011-06-03
> **Davaross said:**
> Try installing wine and the windows version of java as well as the windows executable. IMO it is much more stable via this method than running natively.

Thank you, now it's working

---

### Post by robbiemacg on 2011-06-03
Could there be a server-side issue? Are you trying to get into a multi-player game or build a world on your own server?
Also, are you doing anything to help with memory problems? Per the suggestion on minecraft.net, I launch the launcher (I know the sounds redundant) with the following command:

java -Xmx1024M -Xms512M -cp **/path/to/Minecraft.jar** net.minecraft.LauncherFrame

I've had no issue running the beta on 10.10 and 11.04. I think it runs better when launched with the above command, but it's run regardless... and I use the standard open java.
I'd like to help you figure out what the problem is. This game's mighty fun.

edit - LOL. I'm too slow. [Solved] now?

---

### Post by numb500 on 2011-06-03
> **robbiemacg said:**
> Could there be a server-side issue? Are you trying to get into a multi-player game or build a world on your own server?
Also, are you doing anything to help with memory problems? Per the suggestion on minecraft.net, I launch the launcher (I know the sounds redundant) with the following command:

java -Xmx1024M -Xms512M -cp **/path/to/Minecraft.jar** net.minecraft.LauncherFrame

I've had no issue running the beta on 10.10 and 11.04. I think it runs better when launched with the above command, but it's run regardless... and I use the standard open java.
I'd like to help you figure out what the problem is. This game's mighty fun.

edit - LOL. I'm too slow. [Solved] now?

Hey,

thanks for helping. If i want to launch it with the command you posted i get this error when loading a world.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb77ab416, pid=27477, tid=2925636464
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Client VM (19.1-b02 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# An error report file with more information is saved as:
# /home/yannick/hs_err_pid27477.log
[thread -1275200656 also had an error]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)



Running it through WINE works good though

---

### Post by robbiemacg on 2011-06-03
If you have it up and running in a way that suits you, you've scored a win in my book.
As for that error message, I think you're encountering a driver issue when attempting to run the game natively. By what method did you install java? Are you sure all of your dependencies are met?
In your first post, you mention that you're running a 32 bit OS and also that you've installed an AMD driver. Though I'm no expert when it comes to java, this seems like the sort of thing that might present a problem.

---

