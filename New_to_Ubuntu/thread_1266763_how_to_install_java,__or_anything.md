---
title: "how to install java,  or anything"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by copracr on 2009-09-15
I think I should preface this post by saying I have been running microsoft OS's since MS_DOS 2.?.  I'm very good with MS from a lay perspective and I'm the guy eveyone I know calls when they have pc issues.  I'm really interested in moving away from MS so I'm exploring Ubuntu on a dual boot basis.  This is my second attempt at Linux and I'm just getting started so I dont know ANYTHING.  

First program I'm trying to install is azureus,  but I've already hit the obstacle of not having JAVA.  I went to the website and d/l'ed a .bin file.  This file isn't executable like a .exe on MS.  What do I do with it?

Sorry to post such a basic question,  but I didn't understand the results I got when I searched the forum.

---

### Post by QIII on 2009-09-15
I wouldn't do it that way.

The Ubuntu repositories currently have Update 16.

Go to Applicatons | Accessories | Terminal.

You will get something just like the command line interface in Windows.  In the terminal, type

```
 sudo apt-get update
```You will be asked for your password.  That is just the password you log in with.  You won't see any characters displayed, so don't be concerned and think nothing is happening.

You will see a lot of stuff scroll by.  Eventually, you will be returned back to your command line.

Then, type 

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk 
```You will be asked to agree to the EULA, blah, blah.

After Java is installed, you need to make sure it is the preferred option over OpenJDK

```
sudo update-java-alternatives -s java-6-sun
```

Finally, this will tell you what version you have installed:

```
java -version
```

Normally, I would suggest that newcomers use the Synaptic Package Manager because it provides a nice GUI.  But in this case it would be more difficult to tell you how to get all the packages installed properly than to just have you use the terminal.

Edit:  Sorry.  A bit of explanation.  You use "sudo" to gain temporarily elevated privileges to run things as root in the terminal.  "apt-get" is a command to invoke one of the components of Ubuntu's version of the Debian Advanced Packaging Tool (Ubuntu is a derivative of Debian).  "update" makes sure you are using the latest goodies.   "install" should be obvious.

---

### Post by zeroseven0183 on 2009-09-15
First of all, welcome to Ubuntu and welcome to the Forums!

To install an application, you can either:
 1. use the **Terminal** and type the command, given that you know the package name
 2. use **Add/Remove** in **Applications** menu
 3. use **Synaptic Package Manager** in **System** > **Administration**

So to install** Azureus**, the easiest way would be to go to **Add/Remove...**, search for '**Azureus**' or '**Vuze**', click the check box and click **Apply Changes**.

Hope that helps.


By the way, it will be helpful if you download and read the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/") mentioned in [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by dmizer on 2009-09-15
Or, instead of trying to install Azureus, you can just use the default torrent client called "transmission" that's already installed.

---

### Post by 3rdalbum on 2009-09-15
Install Vuse with Synaptic Package Manager. Install *anything* with Synaptic Package Manager, as long as it's available there. It will automatically download and install Java for you too.

---

### Post by copracr on 2009-09-15
Thanks guys,  I tried the terminal since I could cut and paste and it worked great.  Then I went to "Add/Remove" and searched for both azureus and Vuze but neither came up.  Did I miss a step?

---

### Post by copracr on 2009-09-15
Sorry,  just saw the post about the Synaptics package manager and tried it successfully.   I like that,  very simple.

---

### Post by zeroseven0183 on 2009-09-15
Oh yeah.. It won't show up. Sorry.

Be sure the **All available applications** is selected in Show: ....

---

### Post by copracr on 2009-09-15
It's installed now,  but when I click on the link located in Applications->Internet nothing happens.  Is this normal?  did I miss another step?

---

### Post by juancarlospaco on 2009-09-15
run it from terminal...

---

### Post by copracr on 2009-09-15
> **juancarlospaco said:**
> run it from terminal...

I dont think i can.   I dont know the file system structure to point to it nor do i know where its located.

---

### Post by marshmallow1304 on 2009-09-15
> **copracr said:**
> I dont think i can.   I dont know the file system structure to point to it nor do i know where its located.

That should be automatic.  Just type
```
vuze
```


For future reference, if you want to find out where a program is, use "which".  For example
```
which vuze
```

---

### Post by copracr on 2009-09-15
owner@Asus:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
owner@Asus:~$ 

This is the result.  Does this mean java is installed wrong?

---

### Post by marshmallow1304 on 2009-09-15
> **copracr said:**
> owner@Asus:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
owner@Asus:~$ 

This is the result.  Does this mean java is installed wrong?

The same thing happened the last time I tried Vuze.  I don't have it installed any more (I prefer KTorrent), but I remember how to fix it.

In the terminal,
```
gksudo gedit /usr/bin/azureus
```

Find the following line
```
JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
```

and change it to
```
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
```

Then add this line directly under the previous line
```
JAVA='/etc/alternatives/java -Xmx1024M'
```

If you're interested, here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109").

---

### Post by caspertk on 2009-09-23
Hi, I did the installation of java, and I'm using ies4linux, but when I try to go to a specific chat room that doesn't work with FF (hence ies4linux) it still tells me to install java. 

Help please?

---

### Post by meazz1 on 2009-09-30
> **marshmallow1304 said:**
> The same thing happened the last time I tried Vuze.  I don't have it installed any more (I prefer KTorrent), but I remember how to fix it.

In the terminal,
```
gksudo gedit /usr/bin/azureus
```

Find the following line
```
JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
```

and change it to
```
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
```

Then add this line directly under the previous line
```
JAVA='/etc/alternatives/java -Xmx1024M'
```

If you're interested, here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109").


Thanks, this solved my problem.

---

### Post by 3rdalbum on 2009-09-30
> **caspertk said:**
> Hi, I did the installation of java, and I'm using ies4linux, but when I try to go to a specific chat room that doesn't work with FF (hence ies4linux) it still tells me to install java. 

Help please?

The Linux version of Java doesn't work with Internet Explorer; it's a Windows program! You need to install the Windows version of Java in Wine.

---

