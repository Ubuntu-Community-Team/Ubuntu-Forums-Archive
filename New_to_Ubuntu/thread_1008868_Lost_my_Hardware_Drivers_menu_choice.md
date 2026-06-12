---
title: "Lost my Hardware Drivers menu choice"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Docaltmed on 2008-12-12
Somewhere along the line, I seem to have lost the menu selection for "Hardware Drivers" in the System > Administration submenu?

How do I get it back?

---

### Post by adult swim on 2008-12-12
right click the ubuntu icon up by applications and places.  choose edit menus and then go down to administration.  see if hardware drivers is checked on the right side.

---

### Post by Docaltmed on 2008-12-12
I just looked. Hardware drivers isn't on the list.

---

### Post by adult swim on 2008-12-12
you can add it by going to the system>administration bar in edit menus and then on the right select new item.
it will be as follows

type: application
name: Hardware Drivers
command: jockey-gtk
comment: anything you want

---

### Post by jakwriter on 2009-04-18
Had the exact same problem.  Stumbled around for hours.  A pot of coffee, a bag of chips, and a chocolate bunny later I found this thread.  

These may be new thread questions, but . . . 

What could have made the button disappear?  And how does one figure out what goes in the command slot (eg jockey-gtk)?

Alright, legitimate question now - Followed the directions provided by adult swim, got this

*Failed to execute child process "jockey-gtk" (No such file or directory)*  I did however do a search for "jockey-gtk" in the Synaptic Package Manager, find and install it.  So the button does work now.

So, uh, how does one figure out what command to attach to a particular launcher button?

---

### Post by nandemonai on 2009-04-18
> **jakwriter said:**
> Had the exact same problem.  Stumbled around for hours.  A pot of coffee, a bag of chips, and a chocolate bunny later I found this thread.  

These may be new thread questions, but . . . 

What could have made the button disappear?  And how does one figure out what goes in the command slot (eg jockey-gtk)?

Alright, legitimate question now - Followed the directions provided by adult swim, got this

*Failed to execute child process "jockey-gtk" (No such file or directory)*  I did however do a search for "jockey-gtk" in the Synaptic Package Manager, find and install it.  So the button does work now.

So, uh, how does one figure out what command to attach to a particular launcher button?

All depends on the application / command you're trying to invoke. If it were Firefox it would be (surprise surprise) firefox or firefox-3.0.

You need to know the name used to invoke the command at terminal level.

/bin/ /sbin/ /usr/bin/ and /usr/sbin/ should contain all binaries for installed applications.

As far as finding out some of the more obscure names for programs you'd either need to search google or a trick I like, if you already have a menu option for said launcher is to copy it to the desktop and right click -> properties to find out what command is used to invoke it.

---

