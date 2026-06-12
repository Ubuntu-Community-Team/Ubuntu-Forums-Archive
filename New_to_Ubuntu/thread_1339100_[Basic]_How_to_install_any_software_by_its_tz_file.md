---
title: "[Basic] How to install any software by its tz file"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by coka on 2009-11-27
Hi all 
How to install a software bt its tz file. I have extracted it now which file should i run..
Till now i was installing sw by apt-get ....

---

### Post by Virtual Liberty on 2009-11-27
[This guide]("https://help.ubuntu.com/community/CompilingEasyHowTo") might help you.

---

### Post by pi4r0n on 2009-11-27
The installation procedure for software that comes in tar.gz and tar.bz2 packages isn't always the same, but usually it's like this:
>  tar xvzf package.tar.gz (or tar xvjf package.tar.bz2
 cd package
 ./configure
 make
 make install


If you're lucky, by issuing these simple commands you unpack, configure, compile, and install the software package and you don't even have to know what you're doing.

---

### Post by iponeverything on 2009-11-27
More often than not, there is file like "Readme" or "Install" at the root of archive tree that will give instructions on how to install as well as known dependency issues.

---

### Post by coka on 2009-11-27
Thanks all

@ pi4r0n 

If u dont mind..suggest me a tutorial to understand wats going on...

Regards

---

### Post by coka on 2009-11-27
The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GTK not installed
XYZ@XYZ-laptop:~/Downloads/gipmsg-0.4.0beta1$ 



--after ./configure i m getting this ...

now make is not working

---

### Post by bwang on 2009-11-28
You are missing the GTK+ header files.
In Terminal, run
```
sudo apt-get install libgtk2.0-dev
```
What program are you trying to install. Chances are you need to install more packages.
If you've never compiled programs before, you probably need to get build-essential:
```
sudo apt-get install build-essential
```

---

### Post by pi4r0n on 2009-11-28
> **coka said:**
> @ pi4r0n 

If u dont mind..suggest me a tutorial to understand what going on...

 
[Here you go.]("http://www.tuxfiles.org/linuxhelp/softinstall.html")

---

