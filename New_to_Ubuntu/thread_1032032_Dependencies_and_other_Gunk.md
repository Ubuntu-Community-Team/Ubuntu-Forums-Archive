---
title: "Dependencies and other Gunk"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-05
When I install programs through add/remove, they take a certain amount of space for the download and installation. However, upon removal only a small percentage of this space is freed (also subsequent installations are much quicker and download less files than the initial ones). 

This is especially true for KDE/Qt programs like Dolphin, VLC and Superkaramba (all 25MB+ downloads initially, and <5 MB every subsequent installation). 

I presume this is because dependencies are not uninstalled and so do not have to be downloaded again. How do I hunt down and clear these dependencies? I tried using synaptic but there is no way to know if a programs dependency is also being used for some other program.

I noticed a lot of people on this forum do not prefer to install KDE/Qt apps because it clutters their computer with KDE libraries. Is this a big issue? As I understand it, installing 5-10 KDE apps will bring in less than 1 GB of libraries which seems not a lot. Am I missing something here and is my HDD being eaten whilst I top up on Qt apps.

Thanks

P.S The only difference between Synaptic and Add/remove is that Synaptic is more advanced and allows you to individually handle an apps' associated files right?

---

### Post by gettinoriginal on 2009-01-05
Here is a link for streamlining Ubuntu:
[http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/](http://edhewitt.co.uk/2008/10/27/streamlining-ubuntu/)
Also, if you install "gtkorphan" from synaptic, then any unused dependencies, left behind by uninstalling a program or app, are listed under System > Admin > Remove Orphaned Packages.

I do not know about KDE, as the only KDE I have is Amarok

---

### Post by adult swim on 2009-01-05
to get rid of all dependencies not being used anymore, go to a terminal and run ```
sudo apt-get autoremove
``` that should track them all down for you

---

### Post by Andy06 on 2009-01-19
Ok I found out why not everything isn't removed.

Synaptic puts everything (even when you uninstall it) into a cache. This cache will be cleared automatically when new stuff comes in. But by default if you install a new app and its associated libraries and then uninstall it, installing it again won't download as many of these files due to them already being in the cache. 

The cache can be cleared manually through synaptic options.

I was getting worried that Synaptic was leaving heaps of dependencies on my computer.

---

