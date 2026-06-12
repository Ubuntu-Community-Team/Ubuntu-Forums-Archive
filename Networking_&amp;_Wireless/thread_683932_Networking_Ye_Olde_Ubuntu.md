---
title: "Networking Ye Olde Ubuntu"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by snafle on 2008-01-31
I've got a computer running Ubuntu 5.04 and am trying to network it- only problem is, to install the drivers I found I need to use make, and that can only be acquired with apt-get.... which needs networking.... which needs etc. 

I've got two cards- a realtek RTL-8169 and a 3Com 3Csoho100b-tc. The 3com appears to have a module/drive- Tulip? But it doesn't work, and I can't work out how to make it work. Any help would be much appreciated.

---

### Post by Hightide on 2008-01-31
Hi snafle

there is much better networking support on 7.10. would not consider upgrading?

sorry for being presumptious

regards

:lolflag:

---

### Post by snafle on 2008-01-31
Definitely considered it, but both of my discs has corrupted themselves, and the HD that had them on had a bit of a run in with the stairs (horiffic, it was). Add to that incredibly slow internets and I'm in a bit of bind.

---

### Post by christhemonkey on 2008-01-31
The only way i could think to get these old packages (as support for version 5.04 has been discontinued) is to go to this page:
[http://packages.ubuntu.com](http://packages.ubuntu.com)
and search for make, then painstakingly go through all the dependencies (and the dependencies dependencies and the etc...) and write each one of them down and what repository it is in (main, multiverse, restriced, universe).

Then go to this site:
[http://old-releases.ubuntu.com/ubuntu/pool/](http://old-releases.ubuntu.com/ubuntu/pool/)

And go through the list getting each .deb package, then transfer them to the breezy pc and install them like this:
```
sudo dpkg -i ./*.deb 
```


Have fun with that!!!

---

### Post by snafle on 2008-01-31
I think I might accidently leave my laptop in school accidently connected to the wifi. Accidently dling 7.10...

Quite the string of accidents and mishaps!

---

