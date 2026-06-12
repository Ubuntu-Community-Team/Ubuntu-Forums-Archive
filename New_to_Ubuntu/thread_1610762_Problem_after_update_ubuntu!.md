---
title: "Problem after update ubuntu!"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by tah_206207 on 2010-11-01
Hello dears
my ubuntu after update has a problem that can't log in to ubuntu desktop please help me to solve this problem
this is image of my monitor when problem occoures
[http://img4up.com/up2/422243421714623.jpg](http://img4up.com/up2/422243421714623.jpg)

---

### Post by wishyjr on 2010-11-01
hmm perhaps this might help:

[https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")

i wonder if you need to 'reconfigure X'. Perhaps try this:

- press Ctrl + Alt + F1, this should take you to a terminal based login screen. Log in.

- then enter this command at the terminal:

sudo dpkg-reconfigure xserver-xorg

that might help

cheers
wishy

---

