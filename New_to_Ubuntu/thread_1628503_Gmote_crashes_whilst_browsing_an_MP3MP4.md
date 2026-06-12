---
title: "Gmote crashes whilst browsing an MP3/MP4"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by LinuxN3wbi3 on 2010-11-22
Hi,

Can anyone offer any help with the following error message please? basically trying to get Gmote to work under Lbuntu OS. Web-browsing and Pointer working okay however whilst browsing music and video Gmote is crashing:-

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x009b63c0, pid=2373, tid=66268016
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (17.0-b16 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.1
# Distribution: Ubuntu 10.10, package 6b20-1.9.1-1ubuntu3
# Problematic frame:
# C  [libc.so.6+0xcd3c0]  tfind+0x20
#
# An error report file with more information is saved as:
# /home/linuxnewbie/Desktop/Gmote/GmoteServerLinux2.0.0/hs_err_pid2373.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#


Thank you for any suggestions.

Am using pre-installed VLC and Java/JRE.

---

### Post by Fistorian on 2010-12-12
I have the same problem. I'm using Kubuntu 10.10 64 bit

I got this message:

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007faa53db7e20, pid=3738, tid=140368444163856
#
# JRE version: 6.0_22-b04
# Java VM: Java HotSpot(TM) 64-Bit Server VM (17.1-b03 mixed mode linux-amd64 )
# Problematic frame:
# C  [libvlccore.so.4+0x9ee20]
#
# An error report file with more information is saved as:
# /home/jacob/GmoteServerLinux2.0.0/hs_err_pid3738.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

Hope someone can help. Maby it's because I'm using 64 bit.

---

### Post by andresql on 2010-12-28
same here:

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb772f3c0, pid=32007, tid=3017960304
#
# JRE version: 6.0_22-b04
# Java VM: Java HotSpot(TM) Client VM (17.1-b03 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libc.so.6+0xcd3c0]  tfind+0x20
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#


any idea how to solve this?

---

### Post by Akavashi on 2011-01-20
Hey guys,
Was getting that exact same error (except the mem registers of course) as the OP, but fixed it by installing the Sun Java 6 JRE (sun-java6-jre) from the Canonical Partners repository. That fixed that problem. But then as I soon found out, I couldn't run VLC nor any music/video files because of this one little problem pointed out in this post [[COLOR="DarkOrange"]here[/COLOR]]("http://groups.google.com/group/gmote-users/browse_thread/thread/3fa2a7ac5f9442bc") in which a deprecated function in the new VLC 1.1.4 is still being used with Gmote Server.

So it looks like installing VLC 1.0.6 is the solution at the moment until we get new forks of Gmote Server with some new code. Going to attempt to build from source and see if the developers have added anything new, since the Google Code pre-compiled Server that everybody downloads is from June 2009 haha.

---

### Post by partofthething on 2012-03-10
So, any luck? The pre-compiled one is still from 2009... and I'm getting the same error. Such a great functionality! Why doesn't it work? Wahh.

---

