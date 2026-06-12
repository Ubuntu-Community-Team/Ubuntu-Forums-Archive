---
title: "can't login"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-07-12
for some reason, today after I enter a username and password, ubuntu desktop 11.04 keeps displaying the log in screen and won't let me in.   I tried many users including root and same thing.  I know the password is correct.
 
I'm using VirtualBox on Windows 7 laptop running ubuntu 11.04.
 
Do you have any idea?

---

### Post by Peter09 on 2011-07-12
While booting hold down the shift key and get to recovery mode. Initially try the repair broken packages option in the menu. If this does not work then, do it a gain but  drop to command shell with networking and type ```
startx
```. See what happens.

---

