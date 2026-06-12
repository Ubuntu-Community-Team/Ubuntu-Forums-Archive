---
title: "Input Not Supported"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Vendele197 on 2009-07-02
So I just installed Ubuntu 9.04 on my computer.  I'm sick of Windows, and my computer was running horribly slow when I was using XP, so I decided to reformat the entire drive and use Ubuntu exclusively.  I've been using the Ubuntu Pocket Guide for instructions on how to install and so forth and have run into a bit of a snag.

This seems to be a fairly simple problem, but I have no idea how to fix it. I was poking around display settings and decided to change my resolution (not that big a deal, or so I thought).  I changed the resolution to something my monitor apparently does not support and now cannot view anything due to my monitor only displaying "Input Not Supported".  All I need to do is revert my settings back to 1024x768, but I don't know how to do that without being able to see anything... Any suggestions?

If it helps, I'm using an Envision EN-7100s monitor. Thanks.

---

### Post by nothingspecial on 2009-07-02
First backup your xorg.conf just in case.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then to get you back to where you were


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

More detailed instructions [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=83973")

EDIT you`ll have to boot into a terminal (at the login click sessions then choose failsafe terminal) EDIT

---

### Post by Vendele197 on 2009-07-02
Is there a keyboard shortcut to open the terminal? I can see stuff on the monitor as the computer is booting up, but after that, nothing. I chose not to have a password required for log in at the moment, so I'm almost certain Ubuntu is loaded and ready to go; I just can't see anything besides this stupid monitor error message. >.<

---

### Post by nothingspecial on 2009-07-02
Ctrl Alt F1

---

### Post by Vendele197 on 2009-07-02
I believe I have fixed the problem. Thank you very much.

---

### Post by nothingspecial on 2009-07-02
No problem

---

