---
title: "start up sound effects"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by ub9876 on 2010-12-14
how do you change out the ubuntu sound at start up..
that african stuff..

---

### Post by Ligerzero_942 on 2010-12-14
Start at the top Gnome bar and go System > Administration > Login Screen.

Unlock it and you will have the option to turn the Login sound off.

---

### Post by Verbeck on 2010-12-14
to change it, go to system>preferences>startup applications and edit 'gnome login sound'

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
to
/usr/bin/canberra-gtk-play --file='/path/to/file.mp3'

---

### Post by ub9876 on 2010-12-14
isnt there a simple sounds choice for a different sound like bells or 
something...

---

### Post by Frogs Hair on 2010-12-14
There are system sounds at the link but I have never installed them , some may have instructions under comments or a read me enclosed with the file. 
[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by rburkartjo on 2010-12-16
ub go to system/pref/sounds you can change the alert sounds

---

