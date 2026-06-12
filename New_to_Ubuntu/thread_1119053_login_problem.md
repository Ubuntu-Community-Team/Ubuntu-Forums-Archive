---
title: "login problem"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by blackmagic12345 on 2009-04-07
Hey,

First off, i'm a complete newbie to Kubuntu, so this may be a common issue.

Anyways, i have recently installed Kubuntu 8.10 "in Windows"
I leave for a week, and when i come back (yes i am sure that no one has been on there), i cannot login using ANY setting (KDE, Default, and Failsafe) onto my account. The screen does the thing with the little pictures for about 2-3 seconds, then the screen goes black with nothing but the arrow visible. I then do ctrl+alt+del to logout and instead of logging out, i get some odd-looking assortment of 8-bit icons flashing on my screen. Then, of course, i press and hold the power button on my computer to shut it down.

Any help is appreciated

---

### Post by Zeedok on 2009-04-08
Hey, Welcome to Ubuntu - or Kubuntu at least.  


I encountered a similar problem when i was forst starting and in my case I couldn't log in because my home folder (and consequently my ubuntu partition) was full.  I had been downloading some stuff and left for work when I got back I couldn't log back in.

How big did you make your partition during the installation?

Without a guarantee of success . . . try:

```
CTRL+ALT+F1
```

this will put you at a command line. Then

```
sudo aptitude clean
```

This will clean out some stuff that is non-essential.  Once (provided) you get back in try increasing the size of your partition.

---

