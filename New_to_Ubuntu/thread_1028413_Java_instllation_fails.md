---
title: "Java instllation fails"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by sp_key on 2009-01-02
Hi all,

First, happy new year to all of you!

I have just installed Ubuntu on my old laptop for the first time. I am a complete beginner with linux. 

I have tried unsuccessfully to install Java in order to play online chess at yahoo. 

At my first attempt, I managed to unpack a bin file downloaded from Sun Java at my Desktop. I Run the executable from my Terminal and it all looked like it was installed properly. (Agreed to Licence and so on) but still Yahoo games fail to load due to lack of Java. Now I cannot delete the folder I unpacked as I have no right permissions.

At my second attempt I tried to install Java by running following command: **sudo apt-get install sun-java6-plugin sun-java6-jre** at my Terminal. Again, all looked ok until I try to load games from yahoo.

Third attempt was by adding Java through the Add/Remove option. This time I get this error: [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Obviously this means nothing to me :)

Any ideas?

Many thanks in advance.

---

### Post by taurus on 2009-01-02
Just run

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Moop on 2009-01-02
Run the command it suggests with a sudo in front of it. 
```
sudo dpkg --configure -a
```Have you installed the ubuntu restricted extras package? I believe it includes java.

---

### Post by sp_key on 2009-01-02
Hi,

thanks for your quick response. I've tried both suggestion codes and even though they run fine on Terminal, Java is still not installed properly as Yahoo games still refuse to work on my Firefox.

Furthermore, the unpacked folder on my Desktop (from first attempt) still cannot be deleted due to permissions restrictions.

Any ideas how to undue all this mess and install Java properly?

Thanks.

---

### Post by bump_ on 2009-01-02
To get rid of the folder on your desktop, open the Terminal and type

```

cd ~/Desktop
gksu nautilus .

```

This will open a root nautilus window at the Desktop. Just delete the folders there.

As for you java problem, what does 

```
echo $JAVA_HOME 
```

output?

---

### Post by sp_key on 2009-01-03
> **bump_ said:**
> To get rid of the folder on your desktop, open the Terminal and type

```

cd ~/Desktop
gksu nautilus .

```

This will open a root nautilus window at the Desktop. Just delete the folders there.

It does indeed open a root nautilus windows (what is nautilus?) but once I double click on the Desktop icon from the root folder, it appears blank (i.e there is no such folder in there).

> **bump_ said:**
> As for you java problem, what does 

```
echo $JAVA_HOME 
```

output?

It outputs nothing. Just a blank line.

BTW, it's only my second day with Ubuntu and I have already managed to resurrect an old laptop (did not work with XP) however, I get the impression that commands don't make any "logical" (i.e. human) sense.


Thanks for your time

---

### Post by linux_tech on 2009-01-03
to complete the java install, you need to press tab key to select text and then enter key to enter that selection and move to next selection where you repeat the same again. 

Try to run install again so it completes, then you should have java installed.

---

### Post by linux_tech on 2009-01-03
In terminal type the following:
```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-bin
```

---

### Post by Tom--d on 2009-01-03
You need to install the Java Web plugin in Add/Remove to have Java in Firefox.

---

### Post by sp_key on 2009-01-03
> **linux_tech said:**
> to complete the java install, you need to press tab key to select text and then enter key to enter that selection and move to next selection where you repeat the same again. 

Try to run install again so it completes, then you should have java installed.

Sorry, could you please elaborate? Press Tab key where? What text to select and what selection you're talking about?

Once I enter ```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-bin
``` I watch the Terminal doing it's own stuff. Installation ends with the below:

[I]Setting up sun-java6-plugin (6-10-0ubuntu2) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
[/I]

Then ```
echo $JAVA_HOME
```
and I get a blank line.

So to summarize: 

I need to delete a folder of my Dekstop that "I don't have the right permissions" and install Java. Is this possible?

btw Tom--d, the answer to this is at my original post.

Thanks!

---

