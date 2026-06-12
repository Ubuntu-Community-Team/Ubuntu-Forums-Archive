---
title: "what is ue of key  ALt+ctrl+F1"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by katochd46 on 2011-08-12
Hi,

Please suggest on this question.

> 9.2. Switch to Console mode from Graphical User Interface

In case your Linux system is runnig under a graphical user interface (KDE, Gnome,...) and you need access to the console, use the Ctrl-Alt-F1 shortcut keys to switch to the first console. To switch back to Desktop mode, use the Ctrl-Alt-F7 shortcut keys. 
Hi when i press keys:
ALt+ctrl+F1
ALt+ctrl+F2
ALt+ctrl+F3

only change which occur at the screen is it becomes black. and word changes from ttys0, ttys1, ttys2

what is the use of this console mode & what i can do if i enter console mode ?

---

### Post by haqking on 2011-08-12
The main difference between using terminal and using console in Linux  is that in console mode the whole screen is used to  enter line-oriented commands in text mode, whereas a terminal emulates  a console within a window (under the X-window environment in most  cases).  If you're familiar with the old-fashioned Dos OS, it's like the  difference between the Dos command line and a command prompt under windows.

---

### Post by CatKiller on 2011-08-12
It lets you run things without a graphical interface. It's useful to be able to do that if you've broken your graphical interface, and some people run without a graphical interface at all.

You can do anything that you can do from any other command line, but for the most part it's not something that you need to worry about.

---

### Post by scorp123 on 2011-08-12
> **katochd46 said:**
>  only change which occur at the screen is it becomes black. and word changes from ttys0, ttys1, ttys2 Yes, you're switching between your "**t**ele **ty**pers". Read here:
[http://ubuntuforums.org/showpost.php?p=9804902&postcount=2](http://ubuntuforums.org/showpost.php?p=9804902&postcount=2)

What their purpose is? You can run stuff in text mode without having to touch a mouse. Ever. In text mode you can read mails, write mails, surf the web, edit files and do lots of other stuff without depending on any desktop environment.

---

### Post by fslezak on 2011-08-12
It just is another way to interact with your computer.

if you have ever used the Gnome Terminal or Konsole, they emulate these TTYs.

---

### Post by hakermania on 2011-08-12
using
```

DISPLAY=:0

```
you can run things on the Desktop Environment (located at Ctrl+Alt+F7), for example
```

DISPLAY=:0 gedit

```
will open gedit on the Desktop Environment

---

