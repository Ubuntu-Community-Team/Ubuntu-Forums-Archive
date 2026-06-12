---
title: "snaptic script failing to creat"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by degarb on 2010-12-16
I hate spending days and weeks installing extensions & software, after the initial hour or so of a fresh OS install.  The machines are cripples out of the box, and require patches and sw reinstalls to get back up on feet.  Often, you don't realize it at first, until, "wait I am missing something, oh!, another thing.  What? I can't do this or that. Time to pull out another installer." And, another.

Anyway, I write on a Ubu 9 laptop (no reason to upgrade and break my machine), and wish to save a script of **all** manually installed wmv codecs, plugins for browser, etc.  So, if I ever can get the Ubu 10 installed on my desktop, I can just run the script and be done with it. 

But, it is failing.  Apparently, at least.  In Snaptic, I select manual installs, go to left pane and select all, then create script and save.   The only contents of the script, though, reads "!# bin/sh". Just one line!  Hardly worth writing home about.

Thanks!

---

### Post by Wtower on 2010-12-16
You are right. Check out this thread: [http://ubuntuforums.org/showthread.php?t=166736](http://ubuntuforums.org/showthread.php?t=166736)

Regards

---

### Post by Verbeck on 2010-12-16
it only saves changes you've selected like mark for upgrade, install, removal before applying them

---

### Post by degarb on 2010-12-16
> **Verbeck said:**
> it only saves changes you've selected like mark for upgrade, install, removal before applying them

Surely then, there must be a program that can generate such a script.  [<opinion> IMHO, I hardly think a person can operate a real machine, relying on it to do 1000 unofficial tasks, and not expect such a script maker.  For example, tabs and control clicking links into background tabs was considered weird and unnecessary back in the 90s and early 0's, and required an Opera installation. There are an infinite number of current, and future, ideas that need new programs, outside the standard Office/internet/media apps we get out of box. I couldn't live without tabs.  Yes, I do think many network engineers and programmers, lack the imagination that makes one rely on a customized stack of packages and tweaks that can number into the hundreds. It is a matter of vision, against shoe leather needs and wishes.</opinion>]

Un-accept-a-ble! Anyone with a script generator?

---

### Post by degarb on 2010-12-16
Is there some official, or has anyone, with a good reputation, a script to install all codecs and plugins (abobe, wm9 plugin, mp3)?

---

### Post by Verbeck on 2010-12-17
> **degarb said:**
> Surely then, there must be a program that can  generate such a script.
in the save dialogue box, check 'save full state, not only changes'


> **degarb said:**
> Is there some official, or has anyone, with a good reputation, a script to install all codecs and plugins (abobe, wm9 plugin, mp3)?
just install the *ubuntu-restricted-extras* package
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by QLee on 2010-12-17
[QUOTE=degarb]Is there some official, or has anyone, with a good reputation, a script to install all codecs and plugins (abobe, wm9 plugin, mp3)?[/QUOTE]

I'm not an official, and not really sure about my reputation (lots of people don't like me) but you could consider the old way of making sure a new install had all the packages installed that were on the old install.

The GUI way as mention by Verbeck should be the easiest.


(This might be too difficult and confusing for inexperienced users, in which case they should not attempt it.)

The oldschool way:

dpkg --get-selections > Systemselections (or whatever filename you choose to use)

That will output a list of what is installed on your system to the file.

Then on the new system, where you have copied the file:
dpkg --set-selections < Systemselections

[Here is where the method requires that you are willing to install a new application on your system because dselect is not on a default Ubuntu install. I'm not going to include how to install dselect, anyone using this should already know how to install software]

apt-get dselect-upgrade (with sudo)

...or, using dselect in interactive mode , with the command, dselect, by choosing, "3. [I]nstall"   (with sudo)


I'm not going to write a script for you, but there you have the building blocks if you want to write your own.

---

