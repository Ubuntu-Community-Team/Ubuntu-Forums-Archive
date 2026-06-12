---
title: "Installing jDownloader via .sh file"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by adobrakic on 2009-02-04
I'm guessing the folks at jDownlaoder finally got the message that their default installation is screwed up. They recently added a .sh file that apparently downloads and installs JDL for you. However, when I tried it, I took my eyes off of the terminal, and my computer simply turned off and restarted by itself -- and I'm assuming it's due to the .sh file.

The instructions for using the .sh file are as follows:

> Try out our new Install/Start-Script for Linux!
1.) Download jd.sh
2.) chmod +x jd.sh
3.) start jd.sh
Note: Open jd.sh to read Manual or change Settings! 

I did the chmod, and I cd to my desktop, where the sh file was. From there I ran something like 

```

sh ~/jd.sh

```

---

### Post by epswinde on 2009-02-04
post the contents of the .sh file (as long as its not a binary).

you can either cat it and post that, or use gedit or the like to look inside it.

---

### Post by adobrakic on 2009-02-04
> #!/bin/bash
#JD Installer/Starter Version 0.1
#by Jiaz(JD-Team), [email]jiaz@jdownloader.org[/email]
#You need at least:
#1.) bash (its a bash script ;) )
#2.) wget 
#3.) Java Version >= 1.5 (OpenJDK works also in latest Version)

#How to use this?
#1.) chmod +x jd.sh
#2.) Place it anywhere you want
#3.) Running jd.sh for the first time will install and setup JD into JDDIR folder
#4.) Running jd.sh after the first time will start JDownloader directly

#Parameters
# update (will perform an update)

#JD Installation folder (adjust to your needs)
JDDIR=~/.jd
#default path to our install/update tool (DO NOT Change this)
JDINSTALLER=http://212.117.163.148/update/jd/restore.jar

if [ -e $JDDIR ]
then
if [ "$1" = "update" ]
then
if [ -e $JDDIR/restore.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar restore.jar
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
mv restore.jar install.jar
java -Xmx512m -jar install.jar
rm install.jar
fi
exit
fi
if [ -e $JDDIR/JDownloader.jar ]
then
echo "JD Installation found: Starting JD now"
cd $JDDIR
java -Xmx512m -jar JDownloader.jar $1
fi
echo "JD Installation found: No valid JDownloader.jar exist!"
if [ -e $JDDIR/restore.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar restore.jar
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
mv restore.jar install.jar
java -Xmx512m -jar install.jar
rm install.jar
fi
else
echo "Download/Start JD-Installer"
mkdir $JDDIR
cd $JDDIR
wget $JDINSTALLER
mv restore.jar install.jar
java -Xmx512m -jar install.jar
rm install.jar
fi

justfillingupspace

---

### Post by epswinde on 2009-02-05
It doesn't look like the shell script had anything to do with your mystery reboot. as long as it doesn't keep happening, I'd just consider it an abberation.

---

### Post by adobrakic on 2009-02-05
anyone mind walking me through how to do it correctly, so I don't mess up in any way?

---

### Post by epswinde on 2009-02-05
i just tried installing jdownloader -- as long as you chmod correctly, run
```
./jd.sh
```

and it should install fine.  to start the executeable, look in the directory ~/.jd

seems like you did it fine, i don't know why it rebooted still.  sorry i'm not of more help!

---

### Post by adobrakic on 2009-02-05
Nah, any kind of help is appreciated.
I tried it again, and this time it worked! :D No more Download Them All (yay).

thanks!

---

