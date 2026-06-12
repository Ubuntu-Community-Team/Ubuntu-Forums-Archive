---
title: "Install TAR files"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by fdhealy4 on 2008-12-13
I am using Ubuntu 8.1 and I'm having trouble installing a TAR downloaded file. I have read, and tried, to follow instructions on the web to do this without success. The file name is "hearts-1.98.tar.bz2". It is currently on my desktop. I would like to install it in the games directory. If someone would please list the exact steps here It would be greatly appreciated. Also, after being installed how will I get an icon displayed in the applications - games drop down list?

---

### Post by Michael.Godawski on 2008-12-13
Usually the process of installation a tar file is described in the readme of the tar.
Does it state something special?

If you see a make file in the tar file, do as follows.
Extract the file to your Desktop.
Navigate in terminal to the extracted folder. 
```

cd /path/to/file
```
then run 
```
./configure
make 
sudo make install
```

perhaps there is an install script or an executable bin file.

Please give us the link to the page where you have downloaded the tar package, so we get a picture.

---

### Post by The Cog on 2008-12-13
The first step is to right-click it and choose "Extract here" which will extract the contents into a directory on your desktop. Look in there for a readme file or other instructions.

---

### Post by fdhealy4 on 2008-12-13
I tried to cd to the desktop, "cd home/fdhealy4/desktop/hearts-1.98" but it says no such directory exists.

---

### Post by fdhealy4 on 2008-12-13
Yes I put the / before Home in above. I just got typing too quick

---

### Post by fdhealy4 on 2008-12-13
Yes I already extracted the files on the desktop

---

### Post by fdhealy4 on 2008-12-13
Here is the link to the program I downloaded - [http://rbytes.net/linux/hearts-review/](http://rbytes.net/linux/hearts-review/)

---

### Post by Michael.Godawski on 2008-12-13
As I said. Reading the readme would help.
> To compile you should only have to do:

```
./configure
make
make install
```

RUNNING THE PROGRAM
-------------------

1. Basics

Type "hearts" at the command prompt or select Hearts from the KDE menu.

So navigate into the extracted folder and run the commands mentioned above and you should be fine.

---

### Post by fdhealy4 on 2008-12-13
Michael,

I read the read me file but I can't get to the desktop directory where the file is to execute the commands in the readme file you listed. I tried: "cd /home/fdhealy4/desktop/hearts-1.98"  That is the folder that has the extracted files in it.

---

### Post by fdhealy4 on 2008-12-13
I can't get past the cd /home/fdhealy4 point. 
Ex fdhealy4@Office:/home$ cd /home/desktop
bash: cd: /home/desktop: No such file or directory

---

### Post by Michael.Godawski on 2008-12-13
ok, 
Lesson for today 
Linux is case-sensitve. So desktop is not the same as Desktop.
from the very beginning
open a clean terminal
run ```
ls
```this will show you what files and folders are in the directory you are currently in.
Should be something like this:
```
michael@michael-laptop:~$ ls
Desktop    Examples  Photos    Public     Videos
Documents  Music     Pictures  Templates
michael@michael-laptop:~$ 

```Then type ```
cd Destkop
```This should bring you to the Desktop
Now again run ```
ls
```Do you see your extracted folder?
Great if yes. 
Now again cd and start to type the name of the folder; after some letters push the Tab-button to auto complete the long file name.

---

### Post by Ender41 on 2008-12-13
> **fdhealy4 said:**
> I can't get past the cd /home/fdhealy4 point. 
Ex fdhealy4@Office:/home$ cd /home/desktop
bash: cd: /home/desktop: No such file or directory

 Ok the desktop is Desktop for a start.
You are going to need a lot of dev tools installed to get this working.
build-essential xorg-dev most of the qt tools and kde-dev for a start there might be others that I have installed that you don't. I have got as far as getting the configure to run with no errors after lots of installing new bits as it threw errors at me. However I am getting errors on the make and haven't got to the bottom of those yet.
I have gnome-hearts installed, is this on essentially different that it requires all the work that seems to be needed.

This is what I have done so far. Downloaded the file, then opened a terminal sudo mv thefile /opt/
cd /opt
ls to make sure it is there
then sudo tar jvxf hea(hit tab it will autocomplete) enter
cd hearts-1.98
sudo ./configure

Watch for the errors and then figure out what needs to be installed.

To me this program seems like a heck of a lot of work to get running but of course it is up to you

Ender

---

### Post by fdhealy4 on 2008-12-13
Did what you said. Thans for the CAP lesson. I did the ./configure and got the following at the end of the configure list.

configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


So maybe the file is not installable????

I tried the make command anyway and it said

fdhealy4@Office:~/Desktop/hearts-1.98$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by Michael.Godawski on 2008-12-13
ok tried to install it by myself and got this:

```
michael@michael-laptop:~/Desktop/hearts-1.98$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
[B]checking for kde-config... not found
configure: error: The important program kde-config was not found![/B]
Please check whether you installed KDE correctly.
michael@michael-laptop:~/Desktop/hearts-1.98$ sudo apt-get install kde-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package kde-config**
michael@michael-laptop:~/Desktop/hearts-1.98$ 
```

It seems you need the KDE desktop, (Kubuntu) to run this application.

---

### Post by fdhealy4 on 2008-12-13
OK,

Thanks all for the Ubuntu lessons. I know about gnome hearts, guess it will have to do. The wife is used to the MS layout and this copies that. Trying to get the family to move over to Ubuntu but it's a struggle.

Again Thanks for your patience and help

---

### Post by Ender41 on 2008-12-13
[QUOTE=fdhealy4;6363017]Did what you said. Thans for the CAP lesson. I did the ./configure and got the following at the end of the configure list.

configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


So maybe the file is not installable????

It is but like I said it needs lots of dev files
try sudo apt-get install build-essential and try again,
it will throw more errors and you will need to figure out what these mean.
If you go to [www.google.com/linux](www.google.com/linux) and type in the error it will probably tell you what needs to be installed.

Ender

---

### Post by fdhealy4 on 2008-12-13
Michael,

I'm not running the KDE desktop. Is that the problem? I thought any program would run in any of the desktop versions.

---

### Post by fdhealy4 on 2008-12-13
Going to close this out. Just not worth it. How do I close the thread?

---

### Post by Michael.Godawski on 2008-12-13
> Michael,

I'm not running the KDE desktop. Is that the problem? I thought any program would run in any of the desktop versions. 	

Thought that either. But since this particular game is not in the repositories, it is difficult to download all the dependencies.

Of course you can download the kubuntu desktop, and log into it during the login via select session. 
```

sudo apt-get install kubuntu-desktop
```

---

### Post by Ender41 on 2008-12-13
> **fdhealy4 said:**
> Michael,

I'm not running the KDE desktop. Is that the problem? I thought any program would run in any of the desktop versions.


 Not necessarily true esp one like this that you are compiling, sudo apt-get install kubuntu-desktop kde-dev build-essential will install a lot of the files you need for this, but if you are not running kubuntu the number of files you need will be megs worth. Basically this one is built on the kde desktop and not built into a deb file, so there can be a lot of work getting it running.

Ender

---

### Post by Michael.Godawski on 2008-12-13
You cannot close it; only moderators can. You can leave it open.

---

