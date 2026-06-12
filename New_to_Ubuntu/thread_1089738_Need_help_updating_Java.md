---
title: "Need help updating Java"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Artelus on 2009-03-07
Hey guys, I've recently installed Ubuntu (first linux distro) and so far it's good :)
I want to know how I can update my Java to the latest version, everything is confusing right now.
First of all, I don't know where Java is. In windows the stuff are usually located in C:/Program Files/Program/Program.exe, but I have no idea how Linux works. >_>...

When I vertify my Java version on Java.com, here's what I get:
> Verifying Java Version
Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.
Download Free Java for Linux

Version 6 Update 12 

Then when I search "Java" on Synaptic, I have alot of Java applications installed. This is confusing me too. Here's what I have:
java-common
openjdk-6-jre
sin-java6-jre
ca-certificates-java
britty

So yeah, what are they, and which one am I supposed to update?

When I downloaded Java from the Java.com and installed it with it's instructions, it seemed to work, but I installed it on my desktop, and my browser doesn't seem to reconize it, so I had to force-delete the folder through the terminal.

Can someone please give me some percise instructions on how to update Java on my machine? Help will be appreciated. Thank you :)

---

### Post by rhcm123 on 2009-03-07
> **Artelus said:**
> Hey guys, I've recently installed Ubuntu (first linux distro) and so far it's good :)
I want to know how I can update my Java to the latest version, everything is confusing right now.
First of all, I don't know where Java is. In windows the stuff are usually located in C:/Program Files/Program/Program.exe, but I have no idea how Linux works. >_>...



Most linux packages (thats the preferred term, but programs are ok too) are located usually in /bin, /sbin, or /usr, or a combanation of the three. Configuration files (they tell the program how to function) are usually located in /etc, /var, or /usr, along with many subdirectories of those. 

> **Artelus said:**
> Then when I search "Java" on Synaptic, I have alot of Java applications installed. This is confusing me too. Here's what I have:
java-common
openjdk-6-jre
sin-java6-jre
ca-certificates-java
britty

So yeah, what are they, and which one am I supposed to update?


You are fairly resourceful for somebody who "dosen't know how linux works" :)
-Java common is the main Java package
-Open JDK is a Debugging platform
-Sin Java is associated with Open JDK
-ca-certificates is a java applications certificate verifyer
-i have no clue what britty is

java common is the one you need to update
Run the following command to update it & associated pacakges
```
sudo apt-get upgrade java-common

```

---

### Post by Artelus on 2009-03-07
It didn't do anything. Here's what I got:
```

sudo apt-get upgrade java-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by rhcm123 on 2009-03-07
> **Artelus said:**
> It didn't do anything. Here's what I got:
```

sudo apt-get upgrade java-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Is it installed? Run this instead then:
```
sudo apt-get install java-common
```

---

### Post by Artelus on 2009-03-07
Yeah, it's installed.

---

### Post by rhcm123 on 2009-03-07
> **Artelus said:**
> Yeah, it's installed.

Open jdk also does a bit of java work (it's more of the main package than i thought..) but it can also be installed/updated.

Alrighty, try this command:
```
sudo apt-get install sun-java6-bin openjdk-6-jre
```

If it says those packages are installed, then update them!
```
sudo apt-get update sun-java6-bin openjdk-6-jre
```

---

### Post by Artelus on 2009-03-07
It's already installed:
```
sun-java6-bin is already the newest version.
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
```

And here's what I got when I tried to update:
```
sudo apt-get update sun-java6-bin openjdk-6-jre
E: The update command takes no arguments

```
????? =/

---

### Post by rhcm123 on 2009-03-07
> **Artelus said:**
> It's already installed:
```
sun-java6-bin is already the newest version.
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
```

And here's what I got when I tried to update:
```
sudo apt-get update sun-java6-bin openjdk-6-jre
E: The update command takes no arguments

```
????? =/

Ooops, i gave you update. Type upgrade instead... update is a different command entirely, and it checks repositories. But wait a tic, it says that you already have the latest versions on the computer. openjdk is set to manually installed because of you trying to manually install the latest version...

This esentially means that you have the latest fully supported ubuntu-java packages on your computer, it's just that the ultra-new one from Sun has yet to be put into the repositories

---

### Post by presence1960 on 2009-03-07
> **Artelus said:**
> Hey guys, I've recently installed Ubuntu (first linux distro) and so far it's good :)
I want to know how I can update my Java to the latest version, everything is confusing right now.
First of all, I don't know where Java is. In windows the stuff are usually located in C:/Program Files/Program/Program.exe, but I have no idea how Linux works. >_>...

When I vertify my Java version on Java.com, here's what I get:


Then when I search "Java" on Synaptic, I have alot of Java applications installed. This is confusing me too. Here's what I have:
java-common
openjdk-6-jre
sin-java6-jre
ca-certificates-java
britty

So yeah, what are they, and which one am I supposed to update?

When I downloaded Java from the Java.com and installed it with it's instructions, it seemed to work, but I installed it on my desktop, and my browser doesn't seem to reconize it, so I had to force-delete the folder through the terminal.

Can someone please give me some percise instructions on how to update Java on my machine? Help will be appreciated. Thank you :)

are you running 32bit or 64 bit? 

If 64 bit try these links, either one works : 

[http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1)

[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

### Post by rhcm123 on 2009-03-21
has this thread run it's course and i can delete it from my subsciptions folder, or do you still need help?

---

