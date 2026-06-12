---
title: "Refreshing environment variables for X without a restart"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by egervari on 2010-10-12
Hi, how do I refresh the environment variables stored in /etc/environment for X? For example, IntelliJ IDEA reads a maven home environment variable, as well as others, to detect software. These environment variables are not installed - you have to set them yourself.

How do I refresh them in X so that I can just re-start IDEA and they will be found? 

I've googled this, and lots of people say stuff like "source ./etc/environment". While source is not found, even if it were, that would only work for the terminal - not X. 

I basically want to refresh them globally - X and all future terminal windows.

Windows has this feature believe it or not, so I figure ubuntu must have too, no?

---

### Post by wishyjr on 2010-10-15
hmmm i think to restart X you need to do the following...

at the desktop press: Ctrl, Alt and F1. This will just you to a terminal prompt.

then enter this command: 

sudo /etc/init.d/gdm restart (for Gnome)
or 
sudo /etc/init.d/kdm restart (for KDE)

this should restart X. If it doesn't return you back to the desktop press: Ctrl, Alt and F7


hope that's what you're looking for.
Cheers

---

