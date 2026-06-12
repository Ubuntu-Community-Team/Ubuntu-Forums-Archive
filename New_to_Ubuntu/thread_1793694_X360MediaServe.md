---
title: "X360MediaServe"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by flyingboy on 2011-06-29
I have tried to install X360MediaServe, but cannot get it to work. I downloaded it from [http://sourceforge.net/projects/x360mediaserve/](http://sourceforge.net/projects/x360mediaserve/), and tried to follow the directions from [http://ubuntuforums.org/showthread.php?t=794489](http://ubuntuforums.org/showthread.php?t=794489). The directions are outdated, and cannot be followed exactly.

So far I moved the folder to my home folder, and made it hidden with a "." prefix. I created an x360MediaServe.sh, as well as a startup command. I followed the restart command and have also tried to restart my computer to no avail; the 360 still does not see my computer. 

Any ideas? If I try to go to [http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure), I get a page not found. Any help is greatly appreciated!

---

### Post by Ozymandias_117 on 2011-06-29
Open up a terminal and try to run this and see what output you get:

```
cd ~/.x360MediaServe
./start
```

If it doesn't do ANYTHING, try:
```
ls -lA ~/.x360MediaServe
```


Edit: Another option instead of trying to make this work, is to use uShare. (Which is in the Ubuntu repositories)

---

### Post by flyingboy on 2011-06-30
from ./start, I got a bash with permission denied. I sudo'ed it and got command not found.

Here's the list of files from the second command:


-rw-r--r-- 1 sam  sam    131 2011-06-27 18:29 config.xml
drwxr-xr-x 2 sam  sam   4096 2007-08-29 23:50 files
drwxr-xr-x 6 sam  sam   4096 2007-08-29 23:50 lib
-rw-r--r-- 1 sam  sam  18351 2006-02-25 12:39 License
-rw-r--r-- 1 sam  sam    435 2006-02-25 12:39 Licenses
-rw-r--r-- 1 sam  sam   1093 2006-07-07 23:45 README.txt
drwxr-xr-x 2 sam  sam   4096 2007-08-29 23:50 ScriptDir
-rw-r--r-- 1 sam  sam    351 2007-08-29 23:11 start
-rw-r--r-- 1 sam  sam    347 2007-08-16 16:39 start.bat
-rw-r--r-- 1 sam  sam    417 2007-08-29 23:19 startmac
-rw-r--r-- 1 sam  sam  90402 2007-08-29 23:30 x360mediaserve.jar
-rwxr-xr-x 1 root root    44 2011-06-27 18:20 x360MediaServe.sh


Thanks

---

### Post by Ozymandias_117 on 2011-06-30
Alright. Go ahead and do ```
sudo chown sam:sam ./x360MediaServe.sh
```
Looking at the instructions, there's no reason for that to be owned by root.

Then post the output of ```
cat ./start
``` I'm assuming it's a shell script and that might give us some idea as to what commands it's wanting that you're missing.

---

### Post by flyingboy on 2011-06-30
sam@sam-64bit:~/.x360MediaServe$ cat ./start
#!/bin/bash
java -cp x360mediaserve.jar:lib/cyberlink/clink170.jar:lib/cyberlink/cmgatejava120.jar:lib/jetty/commons-logging.jar:lib/entagged/entagged-audioformats-0.15.jar:lib/jetty/servlet-api-2.5-6.0.1.jar:lib/jetty/jetty-6.0.1.jar:lib/jetty/jetty-util-6.0.1.jar:lib/xerces/xercesImpl.jar:lib/xerces/xml-apis.jar:lib/cyberlink/clinkwrap.jar Run $1

---

### Post by Ozymandias_117 on 2011-06-30
Do you have Java installed on your machine?

---

### Post by flyingboy on 2011-06-30
Yeah. I installed sun-java6-jre via synaptic.

---

### Post by s1mple_M4N on 2011-08-08
Hi

Don't know if you're still looking for help on this...

I downloaded this also and found the instructions a little vague. But I remembered another java application (FileBot) I use and had to change the properties of the executable.

I opened the properties of the "start" shell script file and changed the permissions to executable. Double-clicked and chose "Run in Terminal". Then opened 127.0.0.1:7000 in my browser to access the config options.

It works, but I'm still working on a way of making it start when Ubuntu does.

Hope that helps,

RoyJ

---

