---
title: "How do I start a program automatically when Ubuntu starts?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Green_Mac on 2009-01-14
I want to know how to start a program every time I start up the computer.  The equivalent of the Windoze startup group, basically.  In this case, it's Skype, but I'd like to know the principle so that I can do it for other programs too.  I know about the System, Preferences, Sessions route, but I don't know what to put in as the command, given that Linux doesn't use .exe files (which is what I'm used to).

---

### Post by priegog on 2009-01-14
well, for skype, the command is actually "skype"
it's the same thing for 98% of programs...

---

### Post by taurus on 2009-01-14
You just use the name of the program.  For instance, if you want gedit text editing to start when you log in, just put **gedit** in the command field.

---

### Post by Green_Mac on 2009-01-14
Fantastic! Did it, restarted the PC, auto logged in to Skype.  Again and again I'm finding that the answers to my Linux questions are the most straightforward and obvious ones.  This is so much easier than Windoze, why are people still paying for that sh*te?

---

### Post by jemate18 on 2009-01-14
Just to add a little bit,

sometimes you need the full path of the program..

for example, for Firefox you need to check its full path to ensure.

Applications->Accessories->Terminal
```
which firefox
```

the terminal will display
```
/usr/bin/firefox
```

then 

same process,

System - > Preferences - > Session

add the

/usr/bin/firefox


thanks.....

---

### Post by Green_Mac on 2009-01-15
Marvellous!  I'll make a note of that.

---

### Post by taurus on 2009-01-15
> **jemate18 said:**
> Just to add a little bit,

sometimes you need the full path of the program..

for example, for Firefox you need to check its full path to ensure.

Applications->Accessories->Terminal
```
which firefox
```

the terminal will display
```
/usr/bin/firefox
```

then 

same process,

System - > Preferences - > Session

add the

/usr/bin/firefox


thanks.....

You don' really need a full path if /usr/bin is in your path!

---

### Post by 3rdalbum on 2009-01-15
I thought I'd mention this too. If you need a terminal program to run before you reach the login screen, you can add its name to the "/etc/rc.local" file. Put it before the "exit 0" line. Be aware that it will run as root, so use whatever precautions are necessary, and you don't need to put sudo before any commands in that file.

---

### Post by Lod on 2009-01-15
> **Green_Mac said:**
> Fantastic! Did it, restarted the PC, auto logged in to Skype.  Again and again I'm finding that the answers to my Linux questions are the most straightforward and obvious ones.  This is so much easier than Windoze, why are people still paying for that sh*te?To add a little bit more. In case of skype you didn't need to restart, just to log out and in again. :)

---

