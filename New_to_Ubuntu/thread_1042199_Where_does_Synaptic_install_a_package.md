---
title: "Where does Synaptic install a package"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by buzzbob on 2009-01-17
I have requested that Synaptic install MySQL.  It downloads, appears to install but nothing on the desktop and the only thing I find on the disk is a conf file. Any help would be appreciated.

---

### Post by earthpigg on 2009-01-17
find the package in synaptic... right click -> properties -> installed files

google searching 'man mysql' showed me the man page... typing 'man mysql' from either the terminal or in google will get you started on that.

(sorry if that sounds like a RTFM comment, thats the best i can do since i have _not_ RTFM and have no idea how mysql works :) )

---

### Post by igknighted on 2009-01-17
There is nothing graphical for MySQL.  If you want a GUI, there is a web-based one called Phpmyadmin.  What do you want to use mysql for?

---

### Post by m_duck on 2009-01-17
Try typing```
mysql -u root -p
```into a terminal window (Applications -> Accessories -> Terminal). It will ask for the password you created during installation, enter it and press enter, then it is ready to use. I think that is how to do it but I've not used it for a long time and when I did, it wasn't that often.

---

### Post by fuser312 on 2009-01-17
usually the softwares goes in /usr/bin

> regarding sql
what you need that for, you should install a server to use it.
go for apache. follow the link
[http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06)

then you could easily utilize sql

---

### Post by mcduck on 2009-01-17
The packages are not installed into single directory like in Windows. Instead all the files are put into different places based on what the files are for.

For example, the executable files usually go to /usr/bin, so almost every time you need to find the executable for some program you'll find it there.

All documentation goes into /usr/share/doc, icons into /usr/share/icons or /usr/share/pixmaps, configuration files into /etc and so on.. Rest of the files go to /usr/share/*nameoftheprogram*.

It's quite different from the Windows way of putting everything into C:\Program Files\*someCompanyName*\*nameOfTheProgram*, but once you learn the system you'll definitely see the benefits: No matter what the program is, or who made it, you'll always know where to find it's documentation without even looking for it, you'll *know* it's in /usr/share/doc..

There are also a couple of useful commands that help you finding out where the packages are installed:
"whereis *nameOfTheProgram*" will list all the directories where that program's components are.
"which *nameOfTheProgram*" will give you the path to the executable file of that program. (in most cases /usr/bin/*nameOfTheProgram*).

Also, it's worth remembering that not all packages available are actual programs, many of them are libraries and other stuff. And even from the ones that actually are programs, only a small part is graphical programs. It wouldn't make any sense to create desktop or menu shortcuts for a command-line program or some random library., you couldn't run them from a shortcut anyway.

---

### Post by buzzbob on 2009-01-18
I need to lear SQL, so I decided to put mySQL on my linuz laptop. Thanks for the info

---

### Post by mcduck on 2009-01-18
In that case I suggest installing Apache, PHP and PhpMyAdmin as well, so you'll get a graphical user interface for MySQL.

---

