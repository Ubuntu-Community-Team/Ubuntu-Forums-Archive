---
title: "Performing Xorg configuration"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-09-30
Hi guys.

I have severe performance issues with the Radeon 7500 chip in my laptop. I've found a guide explaining how to fix this performance problem, but it targets an older version of Ubuntu when we still had xorg.conf files:

[http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

Essentially, I was hoping someone could explain how I institute these changes in the latest version of Ubuntu! :) Performance is mind-bogglingly slow at the moment.

---

### Post by mikewhatever on 2010-09-30
**gksudo gedit /etc/X11/xorg.conf**

That will create a blank xorg.conf and open it in the text editor.
Copy/paste what the guide suggests into it, save and close.
To restart xserver, simply logout.

---

### Post by realzippy on 2010-09-30
Basically you had to log out,login at shell,stop gdm (or whatever using)

**sudo Xorg -configure**

creates new xorg.conf in your home directory which fits your hardware,then make radeon depending changes..install
[xorg-edgers]("https://launchpad.net/~xorg-edgers") ati stuff.

read e.g.
[http://www.x.org/wiki/ConfigurationHelp](http://www.x.org/wiki/ConfigurationHelp)

---

