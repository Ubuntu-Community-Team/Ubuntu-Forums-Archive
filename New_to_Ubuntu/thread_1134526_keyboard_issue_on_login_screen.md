---
title: "keyboard issue on login screen"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by plasmarox on 2009-04-23
Hi all :)

When i set up my ubuntu 9.04, i must have selected the wrong keyboard layout. Not to worry, preferences>keyboard>layouts>change layout>apply system-wide.... right?

Wrong - my password has a # in it, but this is shift-3 on a USA keyboard setup, and has its own key on UK keyboards. 

The issue is i can't change the keyboard layout for the login screen - i got quite worried when i couldnt log in!

How can i change keyboard layout for the login screen?

---

### Post by mprince on 2009-04-23
.

---

### Post by mprince on 2009-04-23
Can you login at all? If so you could change the keyboard layout in xorg.
```
sudo gedit /etc/X11/xorg.conf
```


Change this:
```
Option "XkbLayout" "us"
```


To this:
```
Option "XkbLayout" "gb"
```


You'd think it would be uk, but it's gb...

---

