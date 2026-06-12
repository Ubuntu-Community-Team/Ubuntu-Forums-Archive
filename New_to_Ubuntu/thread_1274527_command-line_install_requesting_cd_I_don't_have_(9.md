---
title: "command-line install requesting cd I don't have (9.04)"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by SydneyGB on 2009-09-24
I'm trying to do a command line install of Xubuntu 9.04.  The installer is at the point where it wants to install GRUB and is requesting "Xubuntu 9.04 Jaunty Jackalope - (Release 20090420.1)".  I have both the alternate cd and the regular live cd and it doesn't accept either one.  Now what do I do? :confused:

Edited to add: I calmed down a bit and found a workaround here: [http://ubuntuforums.org/showthread.php?p=7098797&highlight=AlternateCD%3A+Failure#post7098797](http://ubuntuforums.org/showthread.php?p=7098797&highlight=AlternateCD%3A+Failure#post7098797)

It looks like this is a (known?) bug in the alternate CDs (both i386 and 64-bit), but this workaround worked for me.

---

### Post by bodhi.zazen on 2009-09-24
How are you installing if not from the CD ?

If you are installing packages post-install, edit /etc/apt/sources.list and comment out (add a # to the front of the line) the line(s) referring to the CD.

---

