---
title: "How to filter pidgin contact notifications in indicator-applet?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by MrPok on 2009-07-13
Hello (and welcome to my first post! ;))

I have used Ubuntu 9.04 for some time now and I have figured most things out by googling or searching the various Linux forums. There is plenty of help/advice/tutorials/etc. available. However, I can't seem to find how to fix his "inconvenience".  

This is the case:
Every time any of my contacts comes online, the indicator applet shows the black toaster box notification in the upper-right part of the screen.
I would like to restrict this to ***only*** show the the contacts that are either 

[LIST]
[*]in some **group** of my Pidgin contact list, OR
[*]belong to a **pre-defined list of contacts** (say for example, some of my friends and my father)
[/LIST]
The point is that the notifier is useful and quite "stylish", but since I use this setup for work, I don't want to be bothered by notification pop-ups showing people coming on-line that I hardly ever speak. (So, you could say I'd just like to polish my desktop experience with as few distractions as possible haha)

I have experience in programming Java and (very) limited in scripting. But hey, I don't mind learning how to do program/script this in C/Python/whatever myself ...as long as *somebody can point me in the right direction*.

[LEFT][COLOR=DarkSlateGray][On a more general note: it would be nice to be able to filter notifications on a higher level, for example only allowing notification that contain some keywords to be actually displayed.][/COLOR]
[/LEFT]

Any help is much appreciated!
*Cheers*

[COLOR=DarkSlateGray]P.S.: I hope that I've placed this thread in the right forum section, but since this is my first post, feel free to move it to the appropriate section.[/COLOR];)

---

### Post by NESFreak on 2009-07-13
sounds like at least a partial rewrite of pidgins libnotify plug-in. Which is written in C.*

However, pidgin has a pretty neat D-BUS interface, which means you could basically disable the internal libnotify plugin, and instead use any other language that supports D-BUS and libnotify. For for instance the python programming language i came across some nice examples of interacting with both dbus and libnotify. (I'm sorry i can't remember where i found them**) The downside of this is that it requires you to run your 'notifier' as a separate application.

*download the pidgin-libnotify source using
```
apt-get source pidgin-libnotify
```

**some quick links google came up with:
[http://developer.pidgin.im/wiki/DbusHowto](http://developer.pidgin.im/wiki/DbusHowto)
[http://roscidus.com/desktop/node/336](http://roscidus.com/desktop/node/336)

---

