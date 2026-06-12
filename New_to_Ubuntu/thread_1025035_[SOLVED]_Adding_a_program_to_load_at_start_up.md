---
title: "[SOLVED] Adding a program to load at start up"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-29
I have recently installed this program called 'xbindkeys' that is very handy. How can I go about adding this to my programs loaded on startup in Gnome?

~Jeff

---

### Post by adult swim on 2008-12-29
youll need to go to system>preferences>sessions and click add
for name and comment, you can type in whatever you want.  for command youll need to put in xbindkeys

---

### Post by blueridgedog on 2008-12-29
You can try System -> Preferences -> Sessions and add it as a startup program.  

Alternatively you can add the command you want to a startup file called rc.local that resides in /etc/init.d, however, I would try the gui method first.

---

### Post by beastrace91 on 2008-12-29
Thats for the quick response :)

~Jeff

---

