---
title: "Wireshark as root"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by davidsrsb on 2009-11-05
Ubuntu 9.10
The Wireshark package installs as a user program and when selected from the menu, cannot see any interfaces - fairly useless

Edit the menu command entry to:
gksu -u root /usr/bin/wireshark

When selected you will be prompted for password and a pop up box will appear BEHIND (annoying!) the wireshark window warning that running as root is dangerous. This has to be cancelled

---

### Post by MelDJ on 2009-11-05
i think it will always come up as its in the programme and because running as root is unadvisable. maybe see in settings

---

### Post by davidsrsb on 2009-11-05
Running as root is essential to see the interfaces and Ubuntu does the safe and correct thing and makes you enter the password

What is annoying is that the nag warning appears behind the wireshark window but stops further actions until it has been closed. More than once I have thought that X11 has locked up until I spot the tab at the bottom of the screen

---

### Post by ukripper on 2009-11-05
> **davidsrsb said:**
> Running as root is essential to see the interfaces and Ubuntu does the safe and correct thing and makes you enter the password

What is annoying is that the nag warning appears behind the wireshark window but stops further actions until it has been closed. More than once I have thought that X11 has locked up until I spot the tab at the bottom of the screen

You can  crontab it for root to run if you like.

---

