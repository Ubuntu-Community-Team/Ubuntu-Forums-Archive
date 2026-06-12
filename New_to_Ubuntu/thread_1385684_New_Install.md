---
title: "New Install"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by teck0101 on 2010-01-19
Hello, I just installed Xubuntu on an IBM ThinkPad. I'm also a new to linux. I'm able to log in and I get to the desktop but my task bar on the bottom of the screen has vertical lines and when I click on what I think should be the start button I get a big black rectangle with white dots.  I'm lost and I don't know what to do next. I've tried searching through all the post but I've not found a solution. Any help would be greatly appreciated. Thank you.

---

### Post by utnubuuser on 2010-01-19
Hi - Which model thinkpad?  Which graphics card?  It's most likely just a card configuration issue,  -- my x31 produced the same result until I created an xorg.conf file in /etc/X11  -  this is the content of the xorg.conf file:> #to avoid unreadable windows.
Section "Device"
Identifier "Radeon 7500"
Driver "ati"
BusID "PCI:1:0:0"
Option "RenderAccel" "false"
My card is actually a ati M6 Ly 7200, but the above code cured the problem.

---

