---
title: "Understanding the Linux Filesystem"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by #include on 2010-11-12
Hello all.

I apologize if this seems extremely newb, but I'm making another run at making the conversion from windows to linux, and I'm trying to understand how the file system works.

In windows, programs install to C:\Program Files\* 

What is the equivalent for Ubuntu? 

I've been able to understand concepts such as sudo, apt-get, and get a few of the programs I know I will want. But I need to put the libflashplayer.so file into my Google Chrome plugins folder... just can't find it !

---

### Post by AngusH on 2010-11-12
Most programs that are not preinstalled on the system will install their executables to /usr/bin and store their data in various places, grouped based on it's intended use not the program it came with.
Angus

---

### Post by #include on 2010-11-12
Interesting. 

So in order to install Flash from the Adobe website, they have you download a tar.gz (zip file equivalent), filled with a .so file which I assume is the flash plugin.

I'll continue looking to see if I am just going about this wrong.

---

### Post by AngusH on 2010-11-12
Unfortunately there are so many different "standards" for installing on linux (although the variety is a good thing) that no company can reasonably produce a file for every one. Instead they give you a compressed archive of source or binary files which contains an install script (usually in the form of a makefile). This is not a very easy way of installing software. To make your life easier canonical have created a massive archive of files in the .deb format that are dead easy to install and uninstall on ubuntu. We call it the repositories :)
Angus

---

### Post by Whiteice on 2010-11-12
I'm by far not a linux ubuntu expert but I have found some interesting things. like in windows linux has the ability to sort information in on your hard drive. The best way of describing this is as follows

(/) / is your top folder kind like C:

in / you have system files

/etc
/home
/var
etc...

The /home is kinda like your C:/users folders. It houses you users and the documents

Hope that sheds some light for you

---

### Post by oldos2er on 2010-11-12
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

To install flash manually, copy libflashplayer.so to ~/.mozilla/plugins

---

### Post by freesitebuilder on 2010-11-12
I found this helpful:
[http://www.thebuzzmedia.com/linux-filesystem-layout/](http://www.thebuzzmedia.com/linux-filesystem-layout/)
(click the image to enlarge it to a readable size!)

---

### Post by ibizatunes on 2010-11-12
If your a newbie, try installing thing from the GUI and software center, ubuntu is a debian release so look where it would say .exe for a .debs and that will install really easily

if you want to install from the commandline ie flash etc
```
sudo apt-get install ubuntu-restricted-extras
```
ubuntu has thousand of application, you dont really need to download them from the website like you do in window, just use the package manager!

---

### Post by A_M_S on 2010-11-12
To begin to understand the Linux file system try [this]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

---

### Post by corncob on 2010-11-12
I found this enlightening:
[www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf](www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf)

---

### Post by sandyd on 2010-11-12
```

sudo mkdir /opt/google/chrome/plugins
gksudo nautilus /opt/google/chrome/plugins

```
drag-n-drop

---

### Post by tahitiwibble on 2010-11-12
Just a couple of links to help with your delving into linux :)

[http://www.debianadmin.com/linux-directory-structure-overview.html](http://www.debianadmin.com/linux-directory-structure-overview.html)

[http://www.secguru.com/files/cheatsheet/linux-file-structure.jpg](http://www.secguru.com/files/cheatsheet/linux-file-structure.jpg)

---

### Post by Jetso on 2010-11-12
To find where a program puts it's files, in terminal: ```
wheris google-chrome
``` Just replace Google-Chrome with what program your finding. For examply ```
whereis gimp
``` and it says where Gimp's files are.

---

