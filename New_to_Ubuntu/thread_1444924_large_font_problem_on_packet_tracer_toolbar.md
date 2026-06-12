---
title: "large font problem on packet tracer toolbar"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by netnovice on 2010-04-01
i got a display problem on my packet tracer toolbar font size. the font size is extra large. the font size on toolbar option is set to the smallest size possible. does anyone know how to fix that. 

using ubuntu 9.10 with packet tracer 5.2.1.8


[IMG]file:///home/student/Desktop/Screenshot-Cisco%20Packet%20Tracer.png[/IMG][IMG]file:///home/student/Desktop/Screenshot-Cisco%20Packet%20Tracer.png[/IMG]

---

### Post by Anbrew on 2010-05-07
I'm having the same issue. The editing line 6 of the packettracer file does not work. Any ideas anyone?

---

### Post by GigiKent on 2010-05-08
Hy,
I'm running Ubuntu 10.04 (32-bit) and i've fixed the ugly font problem in Packet-Tracer5.3 (linux-notutorials) by following the workaround from: [http://sonniesedge.co.uk/?p=116]("http://sonniesedge.co.uk/?p=116") and for me, it worked like a charm. First you have to install "libqtwebkit2.2-cil" "libqt4-script" "libqt4-qt3support" "libqt4-sql" with all their dependencies:
```
sudo apt-get install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
```
Then you have to edit the file "/usr/local/PacketTracer5/packettracer". Just add a comment in front of the "EXPORT" line:
```
sudo gedit /usr/local/PacketTracer5/packettracer
```  
It should look like this:
```

#!/bin/bash

echo Starting Packet Tracer 5.3

PTDIR=/usr/local/PacketTracer5
#export LD_LIBRARY_PATH=$PTDIR/lib
pushd $PTDIR/bin > /dev/null
./PacketTracer5 $@ > /dev/null 2>&1
popd > /dev/null

```
Save the file and exit.

Start the PacketTracer and enjoy!

I hope this will help you... Cheers!

---

### Post by gemblungcc on 2010-05-14
how about 64bit. 
My machine is Ubuntu 64bit 
I can install Packet Tracer with --force-architecture, but the font is very ugly. How to fix it
I have installed this packets and comment the script
 
libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql

---

### Post by NetBeholder on 2010-05-18
Hi there! 
Sorry for my bad english.
I have installed PT5.3 on ubuntu 10.04 lucid amd64 and commented line 6 in packettracer script. After it I used utility getlibs for download and install x86-libs.
And then new lucid theme were applied! :) (except fonts).
But...

[http://imageshost.ru/links/0d58165d993e2bf8ad7b58e22ec6d809](http://imageshost.ru/links/0d58165d993e2bf8ad7b58e22ec6d809)

Does anyone know how to fix it?

---

### Post by smoothifier on 2010-09-02
I just installed Ubuntu 10.04 an hour ago and the first thing I installed was Packet Tracer.  I had trouble with the fonts and remembered something similar in the past.  I installed ttf-mscorefonts-installer from Synaptic and everything works like a charm.  You might need to enable the Universe and Multiverse repositories although I did not have to.

Hope that helps!

---

### Post by daniel1904 on 2010-09-24
I have installed the normal native way of Packet Tracer PacketTracer531_Ubuntu.tar.gz from the web of Cisco Academy but however was very easy to install. The problem is that the fonts of the program is not large however they are transparent. An that annoys me :S.

---

### Post by JosephWheatley on 2010-10-30
Thanks for this work around
This has solved the font issue for me but now Packet Tracer is running very very slowly.
Any ideas?

---

### Post by rocketsami on 2010-12-10
hey bro this is cool it also works for small font problem

---

### Post by Herazio on 2010-12-19
I've created a small script that might resolve the issue. It basically changes the old QT Framekit files with a newer one that can be installed with apt-get, also included in this script.

Use at your own risk however. It works fine on my PC, I'm not positive if it'll work on yours. A backup does get created automatically however so you can always put that one back. Just put it in a file and chmod +x ***filename***. 

Run by typing sh ***filename***.

```

#! /bin/bash
# Script by: Herazio 
# Made for Ubuntu 10.10 & Packet Tracer 5.3.1 (Works on x64)

#
# Set some variables
# 
# PTPATH = Packet Tracer Library path.
# QTLIBPATH = QT Library path.
# QTOLDVER = QT Old Version found in the Packet Tracer Library directory.
# QTVER = QT New Version installed by apt-get.
#
# Change the variables according to where your paths are located
#  
# Packet Tracer Library standard path = /usr/local/PacketTracer5/lib
# QT Library standard path = /usr/lib32
#
# In case of failure backup is located at /usr/local/PacketTracer5/lib/backup.
#
# Enjoy
#

PTPATH="/usr/local/PacketTracer5/lib"
QTLIBPATH="/usr/lib32/"
QTOLDVER="4.4.3"
QTVER="4.7.0"


#Checks if the needed packages are already installed.
packages=$(dpkg -l | grep libqt4-script | wc -l)

if [ $packages -ne 1 ]
then
 #Install the latest QT Libraries needed for PacketTracer
 echo "Needed packages not installed. Installing as superuser."
 sudo apt-get install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
else
 echo "Packages already installed, moving on."
fi

#Create a backup from the PacketTracer lib directory.
echo "Creating a backup from $PTPATH to $PTPATH/backup."
rsync -az $PTPATH $PTPATH/backup
echo "Done"

#Copying needed files from the QT lib directory.
cd $QTLIBPATH
cp libQt3Support.so.$QTVER $PTPATH
cp libQtCore.so.$QTVER $PTPATH
cp libQtGui.so.$QTVER $PTPATH
cp libQtNetwork.so.$QTVER $PTPATH

#CHMOD the files to permission 755.
cd $PTPATH
chmod 755 libQt3Support.so.$QTVER
chmod 755 libQtCore.so.$QTVER
chmod 755 libQtGui.so.$QTVER
chmod 755 libQtNetwork.so.$QTVER

#Renaming the files to the old filename installed by Packet Tracer.
mv libQt3Support.so.$QTVER libQt3Support.so.$QTOLDVER
mv libQtCore.so.$QTVER libQtCore.so.$QTOLDVER
mv libQtGui.so.$QTVER libQtGui.so.$QTOLDVER
mv libQtNetwork.so.$QTVER libQtNetwork.so.$QTOLDVER

echo "All done, fonts should be fixed now."

```

---

### Post by arseshan on 2010-12-31
> **GigiKent said:**
> Hy,
I'm running Ubuntu 10.04 (32-bit) and i've fixed the ugly font problem in Packet-Tracer5.3 (linux-notutorials) by following the workaround from: [http://sonniesedge.co.uk/?p=116]("http://sonniesedge.co.uk/?p=116") and for me, it worked like a charm. First you have to install "libqtwebkit2.2-cil" "libqt4-script" "libqt4-qt3support" "libqt4-sql" with all their dependencies:
```
sudo apt-get install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
```
Then you have to edit the file "/usr/local/PacketTracer5/packettracer". Just add a comment in front of the "EXPORT" line:
```
sudo gedit /usr/local/PacketTracer5/packettracer
```  
It should look like this:
```

#!/bin/bash

echo Starting Packet Tracer 5.3

PTDIR=/usr/local/PacketTracer5
#export LD_LIBRARY_PATH=$PTDIR/lib
pushd $PTDIR/bin > /dev/null
./PacketTracer5 $@ > /dev/null 2>&1
popd > /dev/null

```
Save the file and exit.

Start the PacketTracer and enjoy!

I hope this will help you... Cheers!


Thanx a lot man It worked like magic :) :D

---

### Post by krowa on 2011-02-13
[Herazio]("http://ubuntuforums.org/member.php?u=1103530"), Thanks for this scripts, work grat!

---

### Post by MatthewHouse on 2011-02-22
Herazio your script worked great mate... thanks

---

### Post by sulaimangd on 2011-04-17
> **Herazio said:**
> I've created a small script that might resolve the issue. It basically changes the old QT Framekit files with a newer one that can be installed with apt-get, also included in this script.

Use at your own risk however. It works fine on my PC, I'm not positive if it'll work on yours. A backup does get created automatically however so you can always put that one back. Just put it in a file and chmod +x ***filename***. 

Run by typing sh ***filename***.

```

#! /bin/bash
# Script by: Herazio 
# Made for Ubuntu 10.10 & Packet Tracer 5.3.1 (Works on x64)

#
# Set some variables
# 
# PTPATH = Packet Tracer Library path.
# QTLIBPATH = QT Library path.
# QTOLDVER = QT Old Version found in the Packet Tracer Library directory.
# QTVER = QT New Version installed by apt-get.
#
# Change the variables according to where your paths are located
#  
# Packet Tracer Library standard path = /usr/local/PacketTracer5/lib
# QT Library standard path = /usr/lib32
#
# In case of failure backup is located at /usr/local/PacketTracer5/lib/backup.
#
# Enjoy
#

PTPATH="/usr/local/PacketTracer5/lib"
QTLIBPATH="/usr/lib32/"
QTOLDVER="4.4.3"
QTVER="4.7.0"


#Checks if the needed packages are already installed.
packages=$(dpkg -l | grep libqt4-script | wc -l)

if [ $packages -ne 1 ]
then
 #Install the latest QT Libraries needed for PacketTracer
 echo "Needed packages not installed. Installing as superuser."
 sudo apt-get install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
else
 echo "Packages already installed, moving on."
fi

#Create a backup from the PacketTracer lib directory.
echo "Creating a backup from $PTPATH to $PTPATH/backup."
rsync -az $PTPATH $PTPATH/backup
echo "Done"

#Copying needed files from the QT lib directory.
cd $QTLIBPATH
cp libQt3Support.so.$QTVER $PTPATH
cp libQtCore.so.$QTVER $PTPATH
cp libQtGui.so.$QTVER $PTPATH
cp libQtNetwork.so.$QTVER $PTPATH

#CHMOD the files to permission 755.
cd $PTPATH
chmod 755 libQt3Support.so.$QTVER
chmod 755 libQtCore.so.$QTVER
chmod 755 libQtGui.so.$QTVER
chmod 755 libQtNetwork.so.$QTVER

#Renaming the files to the old filename installed by Packet Tracer.
mv libQt3Support.so.$QTVER libQt3Support.so.$QTOLDVER
mv libQtCore.so.$QTVER libQtCore.so.$QTOLDVER
mv libQtGui.so.$QTVER libQtGui.so.$QTOLDVER
mv libQtNetwork.so.$QTVER libQtNetwork.so.$QTOLDVER

echo "All done, fonts should be fixed now."

```

Hey man thanks for the script, would this script work in Packet Tracer 5.2 on ubuntu 10.04

---

### Post by tripialos on 2011-04-27
That did the trick :D

Thanks m8

---

### Post by orewacrazy on 2011-05-04
> **GigiKent said:**
> Hy,
I'm running Ubuntu 10.04 (32-bit) and i've fixed the ugly font problem in Packet-Tracer5.3 (linux-notutorials) by following the workaround from: [http://sonniesedge.co.uk/?p=116](http://sonniesedge.co.uk/?p=116) and for me, it worked like a charm. First you have to install "libqtwebkit2.2-cil" "libqt4-script" "libqt4-qt3support" "libqt4-sql" with all their dependencies:
```
sudo apt-get install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
```Then you have to edit the file "/usr/local/PacketTracer5/packettracer". Just add a comment in front of the "EXPORT" line:
```
sudo gedit /usr/local/PacketTracer5/packettracer
```It should look like this:
```

#!/bin/bash

echo Starting Packet Tracer 5.3

PTDIR=/usr/local/PacketTracer5
#export LD_LIBRARY_PATH=$PTDIR/lib
pushd $PTDIR/bin > /dev/null
./PacketTracer5 $@ > /dev/null 2>&1
popd > /dev/null

```Save the file and exit.

Start the PacketTracer and enjoy!

I hope this will help you... Cheers!

I can't create anything with my packet tracer.....
the Packet tracer window always close every I want to save it....

any other method???

---

### Post by soekarmana on 2011-10-20
> **orewacrazy said:**
> I can't create anything with my packet tracer.....
the Packet tracer window always close every I want to save it....

any other method???

this method works for me : [http://forum.kde.org/viewtopic.php?f=43&t=87983#p158833](http://forum.kde.org/viewtopic.php?f=43&t=87983#p158833) :guitar:

---

