---
title: "Compiling packages froms source"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by thisxcantxexist on 2008-12-12
Hello, new to ubunutu

I'm trying to install a software called OOF2 for some research. [http://www.ctcms.nist.gov/oof/oof2/source/README](http://www.ctcms.nist.gov/oof/oof2/source/README)

In order to install it I need to have:
python
magick++
gtk+-2.0    (which needs atk, glib, pango, cairo)
libgnomecanvas2
pygtk2

the readme says i need to have the header files for all these

1) after compiling and installing glib i tried to compile atk, atk claims that i don't have glib installed properly, how can i check to see what is installed and what is not.

2) is there some way i can install all these packages without downloading all the source code and compiling it all separately?

---

### Post by capn_hector on 2008-12-12
for most of the dependencies (required programs) you can get the .deb with sudo apt-get install <nameofpackage> then compile your program after using apt-get for the dependencies

---

### Post by mc4man on 2008-12-12
you can't always take those readme lists 'literally'

For instance 
"gtk+-2.0 (2.6 or later" actually means you need libgtk2.0 (which is installed already) and in most cases is referring to the -dev package (libgtk2.0-dev

Glib is a source that installs several libs, the above included, hopefully you didn't bork things up there. (there isusually no need to compile and 'install' glib.

Edit: add. packages needed
liblapack-dev
libmagick++9-dev 
libmagick++10 
python-gtk2-dev

packages maybe needed
libffi4-dev
python-gobject-dev 
python-cairo-dev

---

### Post by Claus7 on 2008-12-17
> **thisxcantxexist said:**
> Hello, new to ubunutu

I'm trying to install a software called OOF2 for some research. [http://www.ctcms.nist.gov/oof/oof2/source/README](http://www.ctcms.nist.gov/oof/oof2/source/README)

In order to install it I need to have:
python
magick++
gtk+-2.0    (which needs atk, glib, pango, cairo)
libgnomecanvas2
pygtk2

the readme says i need to have the header files for all these

1) after compiling and installing glib i tried to compile atk, atk claims that i don't have glib installed properly, how can i check to see what is installed and what is not.

2) is there some way i can install all these packages without downloading all the source code and compiling it all separately?

Hello,

as far as glib is concerned I faced a lot of problems installing it myself in my system. I'm still looking on how to be able to solve different dependency issues, yet every problem has a different solution. For glib in particular, if you are still facing problems, you have to be careful with the installation you did. The configure command takes some arguments. One of these, is the location that the new library and/or program will be installed. The default location from program to program (or from library to library) is different. If it is not in your path, the installation will be ok, yet it won't be visible from your other programs. This is what I did in order to install glib and use it in other programs:
[http://ubuntuforums.org/showthread.php?p=5823494#post5823494](http://ubuntuforums.org/showthread.php?p=5823494#post5823494)

Unfortunately you do not give information about the problems you are facing exactly. For example about the error you get. That way you could have targeted help.


> **capn_hector said:**
> for most of the dependencies (required programs) you can get the .deb with sudo apt-get install <nameofpackage> then compile your program after using apt-get for the dependencies

It depends, as you say so. If you have an older version of ubuntu (at least this is my case) the deb file is not solving always one's issue. 

Regards!

---

### Post by Captain_tux on 2008-12-17
Here's a good compiling tutorial from Linux Format:

[http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy](http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy)

Good luck!

---

