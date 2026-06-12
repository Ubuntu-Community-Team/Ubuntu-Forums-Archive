---
title: "GUI Hardware Information"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2008-10-03
I have created a GUI version of lshw to try out.  It doesn't do anything fancy but it does print out the lshw information in a window instead of having to go into the Terminal.

The program will allow you to be able to see all the information from lshw or you can select a particular class to view.

The reason I created this application is because most people tend to not like going into the Terminal and typing in commands.  This will now help those who are trying to figure out their wireless card.

In the future, the application will include lspci and lsusb so that those who are starting out in Linux will be able to find their wirless card, copy the information and paste into the thread without having to go into the Terminal.

This lshw version does include an option to switch to admin mode so that you can get more information from the system.

You should be able to download this file and extract it through Nautilus.  It will create a glshw folder where you will be able to find glshw.py.  This is the application to run.

For those who want to extract it in the Terminal:
```
tar -xvvf glshw*.tar.gz
```
To run it from the Terminal:
```
python glshw.py
```

Of course, this is an early release so there may be bugs.  However, the bugs will not harm anything because it does not update any files.

[NOTE:]This application uses python-gtk2 so it will work in Ubuntu, but those in Kubuntu will need to install python-gtk2.  I do plan to make a Qt version of this if I cannot find an application that matches it in KDE.

I also did not post the source code to this in the thread because it is written in Python so the source code is in the .tar.gz file.

---

