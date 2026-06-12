---
title: "linux mint-can't get jdownloader to run"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by irish66 on 2009-10-17
Hi, downloaded JDownloader%200.8.9.zip to desktop , extracted jar, to desktop,rightclicked, chose to open with java runtime, but nothing happennedJDownloader%200.8.9.zip

---

### Post by beastrace91 on 2009-10-18
Did you read the install notes for Linux listed [here](http://jdownloader.org/download/index)? ```


   1.
      wget must be installed on system!
   2.
      Download jd.sh
   3.
      chmod +x jd.sh
   4.
      start jd.sh

Note: Open jd.sh to read Manual or change Settings!

```

Give this a try.

~Jeff

---

### Post by irish66 on 2009-10-18
No, i didn't jeff. But Thank you for pointing it out to me.
I'll probably have problems with that now :)
...okay i do have java and wget installed.
I am confused over  this jd.sh thing.
Is the jdownloader program for Linux.
Is the zip program with the jar file inside no good to me
What is the actual command I need to get this jd.sh file
Thanks again,  
M

---

### Post by nikhilbhardwaj on 2009-10-18
try 
java -jar jDownloader.jar
from the command line 
that way you'll be able to find out the error message that doesn't let java start

---

### Post by irish66 on 2009-10-18
thank you
"Unable to access jarfile jDownloader.jar"

---

### Post by beastrace91 on 2009-10-18
Open terminal and change directory to where you exacted the files to, for example if they are on your desktop do ```
cd ~/JDownloader\ 0.8.9
java -jar JDownloader.jar
```

Note that capital J in JDownloader.jar - Linux is case sensitive. I just tested this on my 32bit Ubuntu system and it went off without a hitch.

Regards,
~Jeff

---

### Post by irish66 on 2009-10-18
Thank's Jeff.
i tried a number of different ways, but to no avail.
here is output from terminal to shoow what i tried
  
martin@martin-desktop ~ $ cd/home/martin/Desktop/JDownloader%200.8.9.zip
bash: cd/home/martin/Desktop/JDownloader%200.8.9.zip: No such file or directory
martin@martin-desktop ~ $ java -jar JDownloader.jar
Unable to access jarfile JDownloader.jar
martin@martin-desktop ~ $ cd ~/JDownloader\ 0.8.9
bash: cd: /home/martin/JDownloader 0.8.9: No such file or directory
martin@martin-desktop ~ $ java -jar JDownloader.jar
Unable to access jarfile JDownloader.jar
martin@martin-desktop ~ $ cd/home/martin/Desktop/JDownloader%200.8.9
bash: cd/home/martin/Desktop/JDownloader%200.8.9: No such file or directory
martin@martin-desktop ~ $ java -jar JDownloader.jar
Unable to access jarfile JDownloader.jar
martin@martin-desktop ~ $ cd~/home/martin/Desktop/JDownloader 200.8.9.zip
bash: cd~/home/martin/Desktop/JDownloader: No such file or directory

---

### Post by beastrace91 on 2009-10-18
Where did you save the file to?... Like my above post said was "for example" if it was saved to your desktop. Look at the out put you are getting from terminal - it is not seeing the directory you are trying to change into AKA it does not exist ;)

Use ```
ls
``` in terminal to list all folders/files for the directory you are currently in. And then use ```
cd myfolder
``` to change into "myfolder" for example.

~Jeff

---

### Post by irish66 on 2009-10-21
thanks for your patience, Jeff.
here is terminal output after using your suggestions
martin@martin-desktop ~ $ ls
Bliss.bmp  Documents  dwhelper  Pictures  Public         Templates     Videos
Desktop    Downloads  Music     Projects  restarter.log  The KMPlayer
martin@martin-desktop ~ $ cd desktop
bash: cd: desktop: No such file or directory
martin@martin-desktop ~ $

---

### Post by Mighty_Joe on 2009-10-22
```

martin@martin-desktop ~ $ ls
Bliss.bmp  Documents  dwhelper  Pictures  Public         Templates     Videos
Desktop    Downloads  Music     Projects  restarter.log  The KMPlayer
martin@martin-desktop ~ $ cd desktop
bash: cd: desktop: No such file or directory
martin@martin-desktop ~ $
```

As has been pointed out before, Linux is case-sensitive.  Note that ls reports a directory named "Desktop" and you attempt to cd to "desktop".

---

### Post by irish66 on 2009-10-23
apologies.yes cd Desktop worked. Now to go back to the start of the thread

---

### Post by irish66 on 2009-10-23
okay, it;s getting to the stage now where I'm saying to hell with it.
anyway here is latest output from terminal
martin@martin-desktop ~ $ cd Desktop
martin@martin-desktop ~/Desktop $ ls
JDownloader 0.8.9
JDownloader.jar
martin@martin-desktop ~/Desktop $ Downloader 0.8.9
bash: Downloader: command not found
martin@martin-desktop ~/Desktop $ JDownloader.jar

---

### Post by Mighty_Joe on 2009-10-24
JDownloader 0.8.9 is a directory.  It is not executable.
Is JDownloader.jar really on the desktop or is it the JDownloader.zip that you downloaded?
As many people have posted, the correct command for running the JDownloader JAR file is:
```
java -jar JDownloader.jar
```
It should be in the JDownloader 0.8.9 directory off the desktop.

---

### Post by irish66 on 2009-10-24
Hi, thanks for responding
i unzipped the jdownloader zip file.
that now appears on the desktop
as jDownloader. 0.8.9
i also copied the jdownloader.jar file from within that directory
and put it on desktop
so the two jdownloader items on desktop are
jdownloader 0.8.9=unzipped directory
and jdownloader.jar=copy of file from above directory

i tried your suggestion with following result


 martin@martin-desktop ~/Desktop $ java -jar JDownloader.jar
Exception in thread "main" java.lang.NoClassDefFoundError: it/sauronsoftware/junique/AlreadyLockedException
Caused by: java.lang.ClassNotFoundException: it.sauronsoftware.junique.AlreadyLockedException
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: jd.Main. Program will exit.

---

### Post by Mighty_Joe on 2009-10-26
> **irish66 said:**
> 
i also copied the jdownloader.jar file from within that directory
and put it on desktop


Did you try running JDownloader from it's own directory?  It's a bad idea to go tinkering with a program if you don't understand what that program does.  
FWIW, I just tried moving the JDownloader.jar file and it failed for me too.  I know JDownloader constantly downloads updates to keep ahead of various sites' countermeasures.  My wild-assed guess is that JDownloader has a custom classloader which loads those updates from somewhere in the JDownloader directory.  Moving the JAR probably breaks this classloader, giving you the error you observed.

---

### Post by octavio822 on 2011-12-26
try using unix installer i have ubuntu 11.04 and work perfectly

1.- Download from oficial webpage.
2.- Double click in the file (is an Binary not a bash).
3.- enjoy

For Hard problems Easy Solutions.

---

### Post by oldos2er on 2011-12-26
Closed, necromancy.

---

