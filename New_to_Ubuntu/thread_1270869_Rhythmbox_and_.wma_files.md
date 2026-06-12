---
title: "Rhythmbox and .wma files"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-20
Hi there,

Is it possible for Rhythmbox to play .wma files? Most of my music is in mp3 format, but every now and then on shuffle it'll come across a .wma song and freeze then crash. I think it's because I do not have the w32codecs installed.

I tried to install them following [this guide]("http://www.ubuntuforums.org/showthread.php?t=70227&highlight=play+wma+music+files") but all of the mirrors and download sites are down.

---

### Post by Liolikas on 2009-09-20
Pages are not down they are just redesigned here new main page:
[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)
I hope you can find what you need now yourself in it somehow.:popcorn:

---

### Post by humphreybc on 2009-09-20
Seems I already have the w64codecs installed thanks to Medibuntu... so howcome Rhythmbox still freezes when it trys to play a .wma file?

---

### Post by sideaway on 2009-09-20
strange issue... Maybe gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-plugins-ugly can help?

---

### Post by humphreybc on 2009-09-20
> **sideaway said:**
> strange issue... Maybe gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-plugins-ugly can help?

```

benjamin@benjamin-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
Password or swipe finger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
benjamin@benjamin-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Liolikas on 2009-09-20
Try other player. Possibly your player bug report it.

---

### Post by sideaway on 2009-09-20
have you tried playing the .wmas with other players that use gstreamer? it may not be the codecs causing the freeze...

---

