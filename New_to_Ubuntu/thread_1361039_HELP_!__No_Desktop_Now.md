---
title: "HELP !  No Desktop Now"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by johnfarrow on 2009-12-21
I was trying to get the display  on an external monitor and somehow I messed up the display.  Now all I get is the little bit at the top of the screen and cant don anything.  I tried to fix it with the Live CD and that works but doesn't stick.
  Is there anyway I can type blind and the terminal and reset the display?  Its 9.04 version

---

### Post by LowSky on 2009-12-21
look on keyboard for a key that loks like a monitor, hit the Fn key and that monitor icon and it might switch to the other screen

---

### Post by Gone fishing on 2009-12-21
If you start in recovery mode doesn't 9.04 have the option of reconfiguring the x server? If not start in recovery mode start in a terminal and run sudo dpkg-reconfigure xserver-xorg

---

### Post by johnfarrow on 2009-12-21
That switches the little sliver of video from the laptop to the external monitor, but thats all.  If I click where I think "switch User" is on the top right and I find it then the screen goes back to normal for for the "guest User", but when I log out of Guess guess user, the problem returns

---

### Post by johnfarrow on 2009-12-21
To Gone Fishing.

That worked!  Thanks a Million.  You saved my bacon!

---

