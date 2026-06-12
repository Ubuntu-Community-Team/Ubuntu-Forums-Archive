---
title: "Adding a program to startup via terminal"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by typal on 2010-07-27
I'm making a script to run after a fresh install. I'd like to have a couple programs automatically run on startup. This is fairly simple using the gnome GUI (System > Preferences > Startup Applications), but I'm not sure how to add a program with just a terminal command. What is the best method?
I'm running 10.04, so you know.

Thank you in advance
T

---

### Post by sandyd on 2010-07-27
> **typal said:**
> I'm making a script to run after a fresh install. I'd like to have a couple programs automatically run on startup. This is fairly simple using the gnome GUI (System > Preferences > Startup Applications), but I'm not sure how to add a program with just a terminal command. What is the best method?
I'm running 10.04, so you know.

Thank you in advance
T
nano /etc/rc.local
use either
```

/bin/bash [commands]
or
/bin/sh -c [command]
```

---

### Post by typal on 2010-07-27
Thank you for the quick response. But, I'd like a method that isn't user-dependent(so I can start the script I'm currently writing and walk away). Is that possible?

---

### Post by sisco311 on 2010-07-27
> **typal said:**
> I'm making a script to run after a fresh install. I'd like to have a couple programs automatically run on startup. This is fairly simple using the gnome GUI (System > Preferences > Startup Applications), but I'm not sure how to add a program with just a terminal command. What is the best method?
I'm running 10.04, so you know.

Thank you in advance
T

You have to create .desktop file in ~/.config/autostart/


```
cat << EOF >> ~/.config/autostart/**name**.desktop
[Desktop Entry]
Type=Application
Exec=**command**
Name=**name**
Comment=**whatever** 
EOF
```

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---

### Post by typal on 2010-07-27
Thank you Sisco, that works. This is the first I've seen of the Here Tag.

---

