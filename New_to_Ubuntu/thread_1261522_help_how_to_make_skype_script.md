---
title: "help: how to make skype script"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by aljoriz on 2009-09-08
I found out that skype only works on xubuntu with this command run from the terminal:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skypethe only problem is that I can't make a script of it using the command gksu edit /usr/bin

any suggestions?

---

### Post by j.bell730 on 2009-09-08
What's wrong with making a shortcut from the desktop?
Right click desktop > Create Launcher...
Fill in all needed info and use the command you posted in the command field.

---

### Post by aljoriz on 2009-09-08
different version of ubuntu really requires knowing how to do things differently

---

### Post by aljoriz on 2009-09-08
pfft that command only works in the terminal

---

### Post by aljoriz on 2009-09-08
pfft that command only works in the terminal.. 

type
 	Code:
 	$ sudo mousepad /usr/local/bin/skype 
and paste the following 2 line
 	Code:
 	#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
then make it executable
 	Code:
 	$ sudo chmod a+x /usr/local/bin/skype 
the gedit = in xubuntu is MOUSEPAD... :lolflag:

---

