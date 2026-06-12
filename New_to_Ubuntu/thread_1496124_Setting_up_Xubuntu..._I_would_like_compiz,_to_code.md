---
title: "Setting up Xubuntu... I would like compiz, to code in C, and to access my flash drive"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by blue cobra on 2010-05-28
I'm brand new to Linux, and just recently took an interest in computers, and so I would really appreciate some help setting up Xubuntu. My computer is very old- I got it for free several years ago- and it has a 400 MHz Pentium II processor, 512 MB of RAM, and, using ```
lspci | grep VGA
``` I got back ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c). I installed Xubuntu 10.04- the version with the filename xubuntu-10.04-desktop-i386.iso.This computer is not connected to the internet, and its main use will (hopefully) be programming, which I plan to learn more of in the next few months.

First of all, I'd like to be able to code in C. I have been using Dev-C++ on this Windows machine, and preferably I'd like to have something similar for Xubuntu, where I can write, compile, and run code in one program. Is there something that will help me to do this?

It may be impossible with my hardware, but if not I'd also like to use compiz to get the nice visual effects Ubuntu is known for. I tried typing ```
sudo apt-get install compiz compizconfig-settings-manager
``` into the terminal, but that didn't work. Specifically, I get back "E: Couldn't find package compiz". Again, any assistance would be appreciated.

Lastly, I need to be able to access my USB flash drive. Since the Xubuntu computer is not connected to the internet, any files that I want to download will have to be downloaded on this computer and then transferred to the other through a flash drive. However, when I plug in my flash drive and try to click it under Places, I get a box that says ```
Failed to Mount "2G Removable Volume".
     /usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine
     configuration option "gradients" is no longer supported and
     will be ignored.
     Method "Mount" with signature "ssas" on interface
     "org.freedesktop.Hal.Device.Volume" doesn't exist
     .
```And for the icing on the cake, now it won't open most applications. Earlier I ran GIMP, Abiword, Gnumeric, and many more, and now whenever I try to open almost any program, it shows up in the task bar and the cursor turns to the loading one, but then the thing in the task bar goes away and it just doesn't load. I've changed the theme to NOX, I believe (can't check, since that won't open now) and this thing that displays CPU, RAM, and swap usage on the task bar. Help will be welcomed with the greatest appreciation.

Thank you for reading this, and thanks again if you can help. Assistance will be awarded with a baker's dozen of victory cookies :) (in jpeg format)

---

### Post by -humanaut- on 2010-05-29
Theres literally thousands of ways to code in C on Linux I like Geany quite a bit because of its syntax highlighting You'll have to connect the machine to the internet though to realisticly  get the type of software you want.

---

### Post by lisati on 2010-05-29
For the programming side of things there are some good links here:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by quinnten83 on 2010-05-29
Using Linux without internet connection is very difficult.
You need to connect in order to update your computer and install software from the repositories. 
the command sudo apt-get install connects to the internet (usually) and downloads the software from a database. So that is why you got the error.

to see what's happening with the programs,open a terminal and launch them from there, you can then copy the output to the forum and we can have a look see....

you can also run dpkg --reconfigure

---

