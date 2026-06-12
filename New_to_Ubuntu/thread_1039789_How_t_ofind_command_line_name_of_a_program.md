---
title: "How t ofind command line name of a program?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Jengajam2 on 2009-01-14
Whenever you open the terminal and enter in a program, like for Firefox, you type "firefox". I've installed several applications via source code, but I don't know what their names are. Just for an example, one of them is an alien-converted(rpm to deb) resolution changing program named sax2, but that isn't the terminal name.

---

### Post by caljohnsmith on 2009-01-14
If the program name you are looking for is for a GUI app, one trick you can do is run the GUI app from the menus, and then in a terminal do:
```
xprop | grep WM_CLASS
```
Then click on the GUI app Window, and most of the time the "WM_CLASS" field of xprop will tell you the GUI app name that can be run in the terminal. Is that maybe what you are looking for?

---

### Post by lswb on 2009-01-14
In this particular case since you installed from a deb, you can use synaptic, search for the package, then click on the tab that says "installed files" Look for one that is in one of the bin directories. From the command line you can do the same thing with something like 
  dpkg -L packagename|grep bin

Another way, if you know at least part of the command name, is to use the "locate" command. For example, say you know that there is a command for tweaking linux filesystems that has the word "tune" in it, but can't remember the exact name.

locate bin/tune
on my system returns:
/sbin/tune2fs
/usr/sbin/tunelp

One more thing I frequently use is the "man -k", used like "man -k keyword" This will search all man pages for "keyword" and return a list of commands and short descriptions.

---

### Post by thomasr on 2009-01-14
And remember - Linux is case sensitive. firefox is not the same as Firefox.

---

### Post by dannybuntu on 2009-01-15
Wow, thank you all. I am gonna put this in my list of how tos. Thanks :)

---

### Post by Vantrax on 2009-01-15
Its also helpful to remember that applications are named whatever is in the bin and sbin folders.

To find a program to do something specific I highly recommend Google.

---

### Post by nothingspecial on 2009-01-15
A trick I use to launch gui apps remotely on my server is to click

system > preferences > main menu

Navigate through that until you find the app you want, click on properties and it will show you the launch command.

---

### Post by sdennie on 2009-01-15
Another option is:

```

dpkg -L name_of_package | grep bin/

```

Conversely to figure out package a binary (or any file) came from:

```

dpkg -S /path/to/file

```

---

