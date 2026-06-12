---
title: "File Installation"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Diametric on 2010-08-30
Hello,
 
I have an Ubuntu box at home with no internet connection.  The emulators I installed before I moved do not work with the USB logitech controller I have.  So, I have DL'ed ZNES (file format .tar.bz2) and FakeNES (file format .tar) onto my thumbdrive to bring home.  How do I install these apps once I get home?  Up till now, I have used the package manager to get my apps and have never installed a "raw" file.
 
Thanks in advance!
 
-Dylan
 
PS: I love and have used ZNES before - does anyone have feedabck on FakeNES?

---

### Post by kwacka on 2010-08-30
As is usual, instructions are part of the archive.

There will also be lists of files that the application depends upon to run - you will need these to install & run; they may or may not be part of your installation already.

---

### Post by Diametric on 2010-08-30
Fair enough on the archives point, but why would I need other files to install regular .tar and .bz2 files?  Is this the "dependancy" issue I've come across.

---

### Post by Jazzy_Jeff on 2010-08-30
For every program you install there are dependencies. When you install using the software center or using a .deb file the dependencies are already included for you. When you compile your own software then you need to install the dependencies that are needed yourself.

---

### Post by Diametric on 2010-08-30
Ok, so I've read through the process of manually installing software and what I'm still not 100% on is how to determine what dependencies are needed for the software I'm installing.  Anyone?

---

### Post by Jazzy_Jeff on 2010-08-30
There should be some instructions that come with the file. It will tell what you need to make the program run.

---

### Post by kwacka on 2010-08-30
There is an Ubuntu package to install ZNES, when you can find an internet connection go to [http://packages.ubuntu.com/lucid/otherosfs/zsnes](http://packages.ubuntu.com/lucid/otherosfs/zsnes) to download it, then install using ```
sudo dpkg -i zsnes_1.510-2.2ubuntu3_i386.deb
``` (Note, there is only a 32-bit package)

There is a list of require files at the site above, you can check whether they are already installed using (for example) ```
dpkg -s libao2
``` which, when I ran it told me that version 0.8.8-5ubuntu2 of the program 'libao2' was installed.

Using any operating system there are programs that other programs depend upon - obviously you can't run a java application if you don't have java installed.

---

### Post by Diametric on 2010-08-31
Thanks, but I don't have an internt connection on the Ubuntu box.  So, I'm attempting to install manually.  
 
The ZNES .bz2 file has a "makefile" and a "cbuild.c" - I just could seem to run it.  I tried "source makefile" - "sudo makefile" - and a few other combos, but couldn't get it to run.  Any ideas?
 
Thanks.

---

### Post by oldos2er on 2010-08-31
If you want to compile source code on Ubuntu, you first need to install the package build-essential; for some reason this is not installed by default. See [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) and [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

For help installing packages on an offline machine, see [http://keryxproject.org/](http://keryxproject.org/)

---

