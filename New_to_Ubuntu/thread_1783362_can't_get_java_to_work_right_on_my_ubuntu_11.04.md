---
title: "can't get java to work right on my ubuntu 11.04"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by winston_legthigh on 2011-06-15
this is the message i get. Java.net.Socket Exception: Socket closed

---

### Post by kroq-gar78 on 2011-06-15
Does Java work right at all or is it just networking?

---

### Post by jtarin on 2011-06-15
Run the command ```
java -version
```post the results.

---

### Post by winston_legthigh on 2011-06-15
I think it's just the networking. My brower
 doesn't let a lot of java programs run.

---

### Post by winston_legthigh on 2011-06-15
These are the results of putting in the code:

java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

---

### Post by jtarin on 2011-06-15
You should configure your system to use Sun Java."1.6.0_22" only and uninstall OpenJDK. That's my two cents worth of experience.

---

### Post by Anuovis on 2011-06-15
I grabbed this recipe somewhere that worked for me. Basically, it replaces OpenJDK with the Sun Java version.

1. Enable partner repository (this is where you have Sun Java packages)
System > Administration > Software Sources
Select Other Software tab
Make sure partner repository is ticked
Click close

2. Remove OpenJDK and IcedTea plugin
System > Administration > Synaptic Package Manager
Enter "openjdk" in the quick search field
Mark package openjdk-6-jre for complete removal
(icedtea6-plugin will be selected as well)
Click apply

3. Install Sun Java JRE and plugin
While still in Synaptic
Enter "jre" in the quick search field
Mark packages sun-java6-jre and sun-java6-plugin for installation
Click apply

---

### Post by winston_legthigh on 2011-06-18
for some reason, I can't access any of those. I'm blaming Natty Narwhal on this one. It wont let me get into my Admin. And even tho i have software sources downloaded and installed it wont let me access it. **** this. How do I go back to 10.10?

---

### Post by TheDoctorX on 2011-06-18
> **winston_legthigh said:**
> for some reason, I can't access any of those. I'm blaming Natty Narwhal on this one. It wont let me get into my Admin. And even tho i have software sources downloaded and installed it wont let me access it. **** this. How do I go back to 10.10?

maybe u must use sudo from the terminal to get full acess to your apps ... i think it's just a problem of permissions ... but i don't knowreally , i'm not so old:)

---

### Post by dFlyer on 2011-06-18
Open java still has many issues yet. My wife uses a lot of java games on the internet so I just install sun-java for her which solves the issues with open java.

---

### Post by winston_legthigh on 2011-06-18
I guess "If it ain't broke don't fix it" doesn't apply to 11.04. Not everyone wants a Mac.

---

### Post by winston_legthigh on 2011-06-18
I've tried pretty much what I can to get sun java to work on this dumb box. for some reason it just wont do it.

---

### Post by kagov on 2011-06-18
Don't be so quick to blame the OS, this problem may lie with the actual Java code, where it is possible that the OS could be causing this, is what you're trying to run open-source? This could just be a mistake in the code causing the socket to close unexpectedly! Although it probably is the fault of OpenJDK.

As for you not being able to access these things perhaps you should use 'gksudo' and run from there?

---

### Post by jtarin on 2011-06-18
> **winston_legthigh said:**
> I've tried pretty much what I can to get sun java to work on this dumb box. for some reason it just wont do it.Could you outline what you have done? It might help us guide you in the best way to aid you in installing Sun Java.

---

