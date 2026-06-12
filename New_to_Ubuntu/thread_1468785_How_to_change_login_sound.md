---
title: "How to change login sound?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ajk95 on 2010-05-01
I like Ubuntu, but one of the things that drives my crazy is the login sound! How do I change it :confused:?

---

### Post by ibuclaw on 2010-05-01
There is no simple interface to change the login sound (yet), but one method you can use is opening a terminal, and running (copy and paste)
```
sudo cp /usr/share/applications/gnome-volume-control.desktop /usr/share/gdm/autostart/LoginWindow/
```
What this does is copy the Gnome Volume Control desktop item into the Login Manager's autostart programs list.

Logout, and a sound properties window will open at the login screen. You can change the sound theme here - or disable it completely. Once finished, close the window and login as usual.

Then open a terminal again and delete the file you copied previously.
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-volume-control.desktop
```

Regards
Iain

---

