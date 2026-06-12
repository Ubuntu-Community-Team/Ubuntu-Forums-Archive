---
title: "Speedup mouse double click"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by phil66 on 2009-05-14
Ubuntu Hardy

I need to speed up the mouse double click so that I can open a posted transaction in Moneydance financial manager.

Need the file path and the script to enter in the file.
Also need the amount of miliseconds to use.

Thanks for the help

---

### Post by coffeeaddict22 on 2009-05-14
Simplest option for a single user is System/Preferences/Mouse; its' the bottom option on the first page.

---

### Post by freeman2000 on 2009-05-14
What's wrong with using the GUI?  Go to  System -->  Preferences -->  Mouse.  You can make adjustments there.  Good luck.

Gosh coffee... you got me.  I can't type fast enuff.

---

### Post by coffeeaddict22 on 2009-05-15
you need more/ better coffee...

---

### Post by phil66 on 2009-05-15
Hey guys great suggestion but I need the script to add to another distro.

I know it will work in the other distro used it before but lost the command.

---

### Post by coffeeaddict22 on 2009-05-16
Ummm.. you might not like the news, but the times they are a'changin.  xorg.conf used to be the best way to set input device modifications.  Since 8.10, Ubuntu has been using HAL- have a look at [the debian guide]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") and [some info in the Ubuntu wiki.]("https://wiki.ubuntu.com/X/Config/Input")  Aside from that, unfortunately the documentation is a bit sparse, so I can't help.  It might be possible to get it out of the Gnome source code, but I'm not smart enough to be able to find the source.  

In addition, if your other distro hasn't moved to HAL, you'll need to do it the xorg.conf way.

---

