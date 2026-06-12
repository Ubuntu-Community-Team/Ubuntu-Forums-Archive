---
title: "Installing Java for the first time"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by NeiloII on 2011-02-20
Hi everyone. So i am new to the whole Ubuntu os and was trying to play Minecraft on it. However, its in a .jar file and I have no idea how to run it and install it, or how to even install a JRE or JDK or anything else I need to run it. Thanks in advance for any help!

---

### Post by davidmohammed on 2011-02-20
Welcome to the forums

normally you just run jar files like this

assuming you've download the file to "Downloads"

open a terminal and type


```

cd ~/Downloads
java -jar name_of_file.jar
```

you'll need to add execute rights to the file first though

```
chmod +x name_of_file.jar
```

---

### Post by cavh on 2011-02-20
Go to Applications, Accessories, Terminal: type this into the terminal and hit the enter key: ```
java -version
```. If it displays a Java version, then carry on typing this into the terminal:

```
cd <enter the directory where the Minecraft jar file is located, without the angle brackets>
``` eg. ```
cd /home/username/games
``` and hit the enter key. Then type ```
java -jar <name of the jar file>, eg. java -jar minecraft.jar &
``` and hit the enter key. The '&' tells the terminal to run the program in the background so you can use the terminal for other things whilst carrying on with Minecraft.

If there is no Java installed on your system, go to System, Administration, Synaptic and do a search for sun-java. Install the jre (Java runtime environment) and the plugin options.

---

### Post by NeiloII on 2011-02-20
Hey thanks a lot guys! that did the trick. now am I gonna have to do this every time I want to run Miecraft or can I create a desktop shortcut somehow?

---

### Post by cavh on 2011-02-21
Make yourself a little script like this:

In the terminal, type this command:

```
gedit ~/minecraftscript &
```

This will create a text file in your home directory called minecraftscript (the '~' means the home directory of the user logged in to the terminal).

And when the Gedit text editor opens, type this in and save the file:

```
#! /bin/bash

cd <enter the full file path to the directory containing the Minecraft jar file>
java -jar <enter the name of the Minecraft jar file>
```

Then you can close Gedit. Now you need to make the script executable so it will run. In the terminal, type

```
chmod +x ~/minecraftscript
```

Then right-click a blank area on your desktop and select 'Create Launcher'. Then enter a name (any value will do), and then in the command box, enter the full path to the executable, for example */home/<your username>/minecraftscript*. Hit the Okay button, and click the launcher to test it.

---

### Post by NeiloII on 2011-02-21
That works perfect. Thanks a lot! much appreciated :D

---

### Post by dibal on 2011-02-21
hi everyone sorry for this digression. i'm trying to install matlab 2010b in ubuntu 10.10 as a super user but this is the error message i get:

./install: line 562: /tmp/mathworks_14711/java/jre/glnx86/jre/bin/java: Permission denied

kindly help.
Peter

---

### Post by maqtanim on 2011-02-21
> **dibal said:**
> hi everyone sorry for this digression. i'm trying to install matlab 2010b in ubuntu 10.10 as a super user but this is the error message i get:

./install: line 562: /tmp/mathworks_14711/java/jre/glnx86/jre/bin/java: Permission denied

kindly help.
Peter
Please create separate topic for different subject.

BTW... how did you go to Super User mode? Try the following link to install matlab
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by shortrun on 2011-02-21
This is great, my son and I have been trying to get minecraft going on ubuntu for a while.
 
I works now but it's quite slow.  Is that just because the computer is too slow.  It is an old PC about 6 years old.

---

### Post by sandyd on 2011-02-21
> **shortrun said:**
> This is great, my son and I have been trying to get minecraft going on ubuntu for a while.
 
I works now but it's quite slow.  Is that just because the computer is too slow.  It is an old PC about 6 years old.
minecraft requires a lot of resources.

---

### Post by shortrun on 2011-02-21
Thanks Sandyd
I have an Asus A7NBX-vm mother board.  Close to 2 GHz processor and only 512 MB of memory.
I could add more memory, up to 2 GB.
To make minecraft work possibley a video card will be required.
 
NeiloII - thanks for starting this thread, I hope you and others don't mind me expanding on the topic, I really hope I have not strayed too far off.

---

### Post by sandyd on 2011-02-21
> **shortrun said:**
> Thanks Sandyd
I have an Asus A7NBX-vm mother board.  Close to 2 GHz processor and only 512 MB of memory.
I could add more memory, up to 2 GB.
To make minecraft work possibley a video card will be required.
 
NeiloII - thanks for starting this thread, I hope you and others don't mind me expanding on the topic, I really hope I have not strayed too far off.
upgrade to 1 GB

---

### Post by wog on 2011-02-22
cavh, I have questions about that script file.
Is it best not to point the launcher directly at the script file?

I tried putting the script file in the directory with minecraft.jar and having the script simply start minecraft, and then pointed the launcher at the script, but that didn't work. Now I want to try and figure out why it didn't work.

Advice?

---

### Post by Paqman on 2011-02-24
> **NeiloII said:**
> Hey thanks a lot guys! that did the trick. now am I gonna have to do this every time I want to run Miecraft or can I create a desktop shortcut somehow?

If you have Java installed, just right click on the minecraft.jar and go to properties > open with and make sure it is set to open it with whatever Java you have installed. When you click on minecraft.jar it will launch.

---

