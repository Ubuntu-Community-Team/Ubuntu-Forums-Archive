---
title: "remove qwibber and evolution without removing desktop?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by iansane on 2011-06-02
Hi,

I was cleaning up my system of things i don't use on it and decided to remove evolution and gwibber. gwibber removes indicator applets and evolution removes ubuntu-desktop. I did it anyway :lolflag:

Well while I still had a desktop I tried going to synaptic and installing ubuntu-desktop and it said it will also install gwibber and a list of gwibber services. I don't want that so I restarted just to see what happens and big surprise, I had no panels, bars, or menus. 

I had to do a ctrl+alt+t to get a terminal and install ubuntu-desktop which this time installed all the qwibber, evolution, and a bunch of other packages. I have my desktop back but along with all the junk I don't need.

So my question is, is there a way to remove qwibber and evolution or at least make them completely dissapear from my site and never start background processes without loosing ubuntu-desktop?

Thanks

---

### Post by uRock on 2011-06-02
You can remove all of the gwibber packages via Synaptic Package Manager and you can remove ```
evolution
``` ```
evolution-indicator
``` ```
evolution-common
``` without any issues.

---

### Post by iansane on 2011-06-03
thanks uRock. I removed those packages plus several others checking closely to make sure what else would be removed and was able to remove a lot more without loosing the desktop or indicator applet.

I googled around and found out more about how many packages are dependant or have dependencies related to the ubuntu-desktop package. I wish there was a way to remove only pieces of the ubuntu desktop package cause really if you think about good coding practices (encapsulation, separation of functionality, etc.) nothing with "evolution" in the package name should be required for anything else but evolution. Shared libs are fine and understandable but there should be no trace of the word evolution in any files required to make the panel bar, indicator, gnome-applets, or the menu still work. Simply remove the evolution files from the above packages and leave the rest. Oh well, I'm just a beginner/intermediate coder so I'll admit I would be totally lost trying to code something as complex as a desk top environment.

---

