---
title: "How do I enter KDE or Gnome from the bootup screen"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by spector70 on 2009-06-04
I installed kubuntu and everything was fine, but I wanted to install gnome along with kde.  I was successful at the installation process and thought all was well.

Now when I boot into kubuntu I am presented with a terminal screen and I can not figure out how to enter kde or gnome from this black and white screen.  It gives me no splash screen for kde or gnome.  How do I enter one or the other from this terminal screen at bootup?

I'm a newb converting from Vista.

---

### Post by theozzlives on 2009-06-04
startx

---

### Post by spector70 on 2009-06-04
Thanks.  I'll go try that right now.

---

### Post by aysiu on 2009-06-04
Yeah, it sounds as if something went wrong in the installation process.

If *startx* doesn't work, try ```
sudo /etc/init.d/kdm restart
``` or ```
sudo /etc/init.d/gdm restart
```

---

### Post by bear912 on 2009-06-04
Any luck?

---

### Post by spector70 on 2009-06-04
I used the terminal to install gnome.  I think that the code was:

sudo apt-get install gnome

gnome might have been gdm, I don't remember.

Here's what I get:

startx

*has suspicious mode (not 1777) or is not a directory, aborting.*

Should I be in a certain directory and if so how do I get there?

with:

sudo /etc/init.d/kdm restart

I get:

[I]stopping k display manager

:kdm[/I]

---

