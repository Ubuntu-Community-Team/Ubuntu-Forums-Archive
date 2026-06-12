---
title: "dynamice window manager"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by crowhill on 2008-12-31
Hi there

Since this forum is awesome, I dare asking some questions about dwm (dynamic window manager) here.

First of all, I'm a beginner with C and dwm (have it on my Ubuntu (gnome) desktop). So far, I managed to accomplish only a few things (date and time in upper right-hand corner, background picture, keyboard shortcut for starting the terminal, maximization of all windows and firefox, in particular). I think, I like dwm and I would like to tweak it a little bit more. Therefore, I have a few questions. I hope, someone here has some answers. I couldn'd find any solutions by googling.

1. How to change the colors of the statusbar? E.g. make it black with white font.

2. How to create keyboard shortcuts to launch applications? E.g. I tried {MODKEY|ShiftMask, XK_Return, spawn, "exec firefox"} but it doesn't work.

3. How can I automatically get the wireless started when my machine fires up? At the moment, I type in nm-applet in a terminal and wait for a moment. Things work after that. I would like to have something like a script that takes care of it. Or are there alternatives to the nm-applet that could be integrated in dwm?

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by blueridgedog on 2009-01-02
This site:

[http://bbs.archlinux.org/viewtopic.php?id=49121](http://bbs.archlinux.org/viewtopic.php?id=49121)

Talks of gettign the source for dwm and editing it priot to compile.  For example this quote is on the site:

> 
The alternative to manually fetching the source, unpacking etc. is ABS which will automate some tasks for you, and you'll be able to make dwm available globally.

*I* chose to keep it somewhere in my home directory because:

#1. I'm still toying with the configuration file; it's easier to just go to the source directory and edit config.h and then run `make` than it would be to use the ABS.
#2. Sometimes, when using the ABS, I saw that config.h could not be stat`ed and the default configuration got used instead [I haven't looked too much into this, so it might be an error on my side.]
#3. The PKGBUILD contains `config.h` in its source option AND an md5 sum for it; so if you configure config.h as you're supposed to and then try to build the package you'll get md5 checksum errors. [which can be solved either by removing config.h from the sources option and the relevand md5 sum from the md5sums option *OR* by generating an md5 sum for your custom config.h file and updaing the PKGBUILD accordingly.]

---

