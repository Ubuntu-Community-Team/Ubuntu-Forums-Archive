---
title: "Running a windows java program (T4) for tax..."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by saibalter on 2009-05-01
Hi, i'm having trouble running the T4 desktop application which can be found at the canadian revenue agency's website:

[http://www.cra-arc.gc.ca/esrvc-srvce/rf/t4/dsktp/dwnld-eng.html](http://www.cra-arc.gc.ca/esrvc-srvce/rf/t4/dsktp/dwnld-eng.html)

It requires java virtual machine, which i have downloaded and installed into ubuntu 8.0.4...

but i'm unable to emulate the windows .exe with wine because it says it does not detect java virtual machine. is there anyway to run this program to do taxes?

---

### Post by Volt9000 on 2009-05-01
You'll probably have to install the Java Virtual Machine in WINE as well.

---

### Post by Bölvaður on 2009-05-01
looks like a fail to me.
they made a java program that should be able to run on linux and mac, but failed by not using the standard, .jar type of file but an .exe file to install with -.-

so you'll have to install wine (find it under applications &#8594; add/remove) and then to run windows programs you just right click them and select to open them with wine.

Follow the instructions on the site, install the java environment to be able to run java programs, then install that program and then you can be happy :) But you do all this through wine, but not nativly in linux.

---

### Post by pi.boy.travis on 2009-05-01
If you install the Ubuntu-restricted-extras package you will get the Java runtime environment and Java development environment.  That should do it.

---

### Post by llamabr on 2009-05-02
> **pi.boy.travis said:**
> If you install the Ubuntu-restricted-extras package you will get the Java runtime environment and Java development environment.  That should do it.

Looks like the problem is on the server side, though.

I'm not sure it's worth it trying to fight with wine to get this running.  beyond the simplest things, wine often breaks.

---

### Post by pi.boy.travis on 2009-05-02
You could try to run Windows in a virtual machine with VirtualBox.

However, you will need a WinXP disk. . .

---

### Post by Volt9000 on 2009-05-02
> **Bölvaður said:**
> looks like a fail to me.
they made a java program that should be able to run on linux and mac, but failed by not using the standard, .jar type of file but an .exe file to install with -.-

Wow... just wow. This is beyond fail.
Developing software in a platform-independent language only to throttle its ability to be run on any machine by encasing it in a platform-specific installer.

Try this-- I installed the program in my WinXP virtual machine and just zipped the contents of the folder and attached it here. Extract it to its own directory and run it from the command-line as follows:

```

java -jar T4Internet.jar

```

This works from both Windows and Linux. I haven't tested the program fully but it seems to work anyways.

Good luck...

[Edit]
Crap, can't attach, too big, I'll try to split it up..

[Edit2]
On a sidenote/rant, I must say this is typical of the Canadian Government: favouring the Microsoft platform, since they release this program with an exe-only installer, and have parts of their website which will ONLY work in Internet Explorer (or more specifically, won't let you proceed if they detect a non-IE web browser.)

---

### Post by Volt9000 on 2009-05-02
Ok here they are...

Just download all 3 attachments to one directory and type the following in a terminal window:

```

cat T4software1.zip T4software2.zip T4software3.zip > T4software.zip

```

Then just extract T4software.zip to an empty directory and run it as per my previous post.
Hope this works for you!

---

