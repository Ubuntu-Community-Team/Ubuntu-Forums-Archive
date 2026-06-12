---
title: "run a file when a folder changes size"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by jgioannini on 2009-07-22
hi everyone,
I was wondering if it were possible to run a file (or two) when a folder gets larger or smaller.
thanks

---

### Post by Durden on 2009-07-22
I don't believe so. On a Mac you could do something like this with an Applescript, not sure if there is something like this for gnome.

---

### Post by jgioannini on 2009-07-22
thanks Durden, 
but, I do not have to do this in gnome it could be in the shell or in a 3rd party app

---

### Post by Durden on 2009-07-22
The problem is the filemanager needs to have "hooks" in it for a script to know when something is resized and then execute something. I am not aware of any said "hooks" in any of the file managers available.

You could try asking in the developer forums to see what some of them think. I suppose you might be able to do something like this with the KDE 4 Plasma Folderview widget. I however wouldn't know where to begin.

---

### Post by credobyte on 2009-07-22
Theoretically, yes .. practically - you need an application which will "listen" to this folder ( recursively scanning files and summarizing their size ). Haven't heard about this kind of software :roll:

---

### Post by Whiffle on 2009-07-22
You're looking for inotify, and inotify-tools 

Have a look through this thread:
[http://ubuntuforums.org/showthread.php?t=950939](http://ubuntuforums.org/showthread.php?t=950939)

---

### Post by jgioannini on 2009-07-22
thanks

---

