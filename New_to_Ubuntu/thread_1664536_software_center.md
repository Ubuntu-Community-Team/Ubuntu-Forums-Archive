---
title: "software center"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by iroquois on 2011-01-11
How do i find where my ubuntu software center downloads go? For e.g.,i downloaded a bandwidth monitor program called "nload".Now i haven't got a clue where it is.

---

### Post by Paqman on 2011-01-11
[nload seems to be a command line app]("http://packages.ubuntu.com/maverick/nload"). As such it won't be in a menu, you'll have to run it from a terminal window. Apps should tell you if they're command-line only in the description.

---

### Post by Rubi1200 on 2011-01-11
If it is not under one of the menu categories, it is likely a command line program.

From the terminal:
```
nload
```

If that does not work:
```
locate nload
``` to try and find it.

---

### Post by jbrice on 2011-01-11
Is your problem that nload has not added itself to an Application menu? Programs that do not have a graphic interface (i.e. do not use a "Window") - and nload is one of these - don't do this, as these are just accessed by typing the program name in at a terminal window.

---

