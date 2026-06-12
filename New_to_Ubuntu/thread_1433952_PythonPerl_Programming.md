---
title: "Python/Perl Programming"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-03-19
Hi, I've been working on learning some programming languages, my goal being to be able to help with the programming of some of Ubuntu. One thing I am having problems figuring out, is that a lot of things that say they are programmed in Python or Perl have Unix executables. One example of this is a game called Dopewars. Everything I've read says that you don't need to create executables, so, why is this done, and how is this done?

Note: Not sure if this is really the right place to put this or not... but...

---

### Post by Flimm on 2010-03-19
You're looking for the [Programming talk subforum](http://ubuntuforums.org/forumdisplay.php?f=39).

Dopewars is programmed in C.

Python programs are usually distributed as source code, you don't need to compile them. However, they don't necessarily have a .py extension. All you need to do is include #!/usr/bin/python in the first line of the file to let UNIX know it's a Python program (see [this article](http://en.wikipedia.org/wiki/Shebang_(Unix))).

---

### Post by Ozymandias_117 on 2010-03-19
Oh... Oops =D I was looking at a special version of Dopewars... that helps a bit =D

edit: Yeah, that forum already has what I'm looking for :) *Feels like a dumbass now :P*

---

