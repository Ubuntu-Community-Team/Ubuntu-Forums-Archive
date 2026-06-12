---
title: "[SOLVED] My first Ubuntu problem"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by mayagrafix on 2008-12-25
When I log in using Xfce all I see is my desktop background, NO menu bars or status bars, just one big color screen.

The apps seem to work fine accessing via right click or middle click desktop menus.

When I click on the panel button in th Xfce Settings Manger nothing happens. All other buttons work fine.

If I log in using Gnome desktop environment everything is A-OK.

Thanks for the help and Happy Holidays!
:popcorn:

---

### Post by taurus on 2008-12-25
How did you install Xfce?  I assume you initially installed Ubuntu and then installed Xfce window manager with

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by mayagrafix on 2008-12-25
I used Synaptic Package Manager.

Ran Ubuntu for a couple of months, the added Xfce and KDE with SPM. Xfce has run just fine for about 3 weeks no problems, until last night.

Should I re-install using the code given?

---

### Post by tc3000 on 2008-12-25
Does this happen ever time you log in to xfce?

---

### Post by mayagrafix on 2008-12-25
As of last night, YES. Did the usual, log out, log in again, then reboot couple of times, no joy with Xfce.

Before last night, Xfce ran flawlessly. Was very happy with it since I am running on a PII laptop (only need for web and audio streaming using Rhythimbox). But I can log out and relog to Gnome and everything is fine there.

Thanks u guys for the help, happy holidays!

---

### Post by plucky on 2008-12-25
Open a terminal window and use ```
xfce4-panel &
exit
``` should restart the Xubuntu panels.

You need to type **exit** to close the terminal window or else the panels will disappear.

Logout and back in and see if that has fixed the panels problem.

Good Luck

---

### Post by mayagrafix on 2008-12-25
Yeay! that solved the problem. Thanks plucky!!

---

