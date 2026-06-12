---
title: "Why are file dialogs SOOO slow and how can I fix this?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-07
When I have a file dialog box (ie: file -> open) and I get to certain directories, everything becomes really slow. It appears that it is eating up CPU cycles like crazy, and there are just a directory of images (maybe 25, not too large or anything). Another dir that gives me problems has various JAR files and Eclipse goes crazy when I try to add a JAR as the file dialog box just hates it. 

1) Why is it that these file dialog boxes have to scan every file's contents like this, this is just bad design no?

2) How can I turn this off, it is driving me bonkers.

---

### Post by steindor2 on 2010-03-07
> **TurnOfTide said:**
> 
1) Why is it that these file dialog boxes have to scan every file's contents like this, this is just bad design no?

some people, like me for example, find this extreamly useful
> 
2) How can I turn this off, it is driving me bonkers.
get an another file manager, for example PCMan wich can be found under add/remove by searching for file manager

---

### Post by TurnOfTide on 2010-03-07
Will PCMan replace nautilas?? Or will I be fine in that regard?

---

### Post by steindor2 on 2010-03-07
> **TurnOfTide said:**
> Will PCMan replace nautilas?? 
no, they can co-exist just fine, although i recommned setting the on you want to use as default, as right clicking and selecting open with PCMan will probably becone irritating.

---

### Post by twisted_steel on 2010-03-07
Not sure if this will work, but it's worth a shot ...

Open up a terminal and run gconf-editor.  Navigate to desktop/gnome/thumbnailers and check disable_all in the right-hand pane.  You may have to logout and log back in.  You can also disable the thumbnailers for specific files if you look at the folders beneath desktop/gnome/thumbnailers.

---

