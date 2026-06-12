---
title: "Could not apply changes! Fix broken packages first"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by bros on 2011-02-02
By using **Ubuntu Tweak** - **Update Manager **I got only one package that needs to be update (*upstart, event-based init daemon*). However when I click on the Install Update I'm getting this message in a window:

[CENTER][SIZE=3][COLOR=Red]**Could not apply changes! Fix broken packages first.**[/COLOR]

[/SIZE][LEFT]So now my question is... how do I fix the broken packages?
[/LEFT]
[/CENTER]

---

### Post by davidmohammed on 2011-02-02
open a terminal

type 

sudo apt-get update

sudo apt-get upgrade

any errors?

if it says something like "run sudo dpkg --configure" etc - then run the command as suggested

---

### Post by bros on 2011-02-02
> **davidmohammed said:**
> open a terminal

type 

sudo apt-get update

sudo apt-get upgrade

any errors?

if it says something like "run sudo dpkg --configure" etc - then run the command as suggested


Thank you very much, the problem is solved!:-)

---

### Post by stmiller on 2011-02-02
There was a problem with this ubuntu update coming out before another required update was available along with it. 

All should be resolved now,

[http://ubuntuforums.org/showthread.php?t=1679807](http://ubuntuforums.org/showthread.php?t=1679807)

---

