---
title: "Install puzzle pirates"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Obeide on 2009-05-29
Hello, I have recently upgraded to the latest ubuntu and I want to install puzzle pirates.  On the puzzle pirates site it tells you to download the file, open a terminal window and run the installer program. % sh yohoho-install.bin  Then follow the instructions in the installer.

I tried this and it wouldn't work.  how can i get the add/remove programme to install the file I downloaded?

thanks.

---

### Post by Bodsda on 2009-05-29
I think you may be in the wrong directory, when you open a terminal, you will be in ~/ meaning your home directory, but by default firefox downloads get saved in the desktop folder, so we need to change directory, in a terminal run the following commands, the first change directory ```
cd ~/Desktop
```
and the second runs the installer ```
sh yohoho-install.bin
```

Hope this helps,

Bodsda

EDIT: Notice that ~/Desktop is case sensitive, capital 'D'

---

### Post by Obeide on 2009-05-29
woohoo, game installed, thank you so much :D

---

### Post by ashvinmanoj on 2009-09-19
I'm also suffering from same problem. but i installed java and puzzle pirates but at last its asking that it needs jvm 1.5 or more as follows
[SIZE=4][B]

Which Java Virtual Machine would you like to use?
Note: the JVM must be version 1.5 or newer.
[] jvm 1.6                                                             
[: 59: 1.6/bin/java: unexpected operator[/B][/SIZE]
  
i gave jvm 1.6 it shows as above.   also it asked about the location to store the yoclient as follows
[SIZE=4][B]
Where would you like to install yoclient?
[/home/ubuntu/yohoho]   [/B][/SIZE] 

    [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]   now  i dono what    to do here. i am new to ubuntu so please help me to play game..


i installed java using the comand
[B][SIZE=4]
sh jre-6u16-linux-i586.bin[/SIZE][/B]
which was in my home folder.. h

help me please............

---

