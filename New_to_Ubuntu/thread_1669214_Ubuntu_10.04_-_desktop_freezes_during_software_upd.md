---
title: "Ubuntu 10.04 - desktop freezes during software updates"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by kkartha on 2011-01-17
I recently installed Ubuntu 10.04 LTS (32 bit) on my desktop. I have been using 9.10 for over a year without any problems until the installation of  release 10.04.
While trying to software upgrades, I get the following error message:
[B]<< E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B] >>

Tried dpkg --configure -a  from the terminal.
This command also freezes the system (mouse, keyboard and everything).
Pl. help, I am a newbie to Unix/Linux.
Thanks & rgds,
-KK

---

### Post by hansolo4949 on 2011-01-17
Okay, try this:


open up a terminal, run sudo apt-get update

then run sudo apt-get upgrade

If you want, you should run sudo apt-get autoremove to clean things up before you do that.

---

