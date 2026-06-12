---
title: "Where do Startup Applications get run ?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by D_frag on 2010-02-07
I was trying to add some programs to run from startup by adding lines to /etc/rc.local but apparently that doesn't work. When i tried the GUI option , by going to System > Preferences > Startup Applications and added them it worked . That didnt add anything to /etc/rc.local . Does anyone know where does ubuntu add the startup application. Basically what script is Startup Applications editing ? 


Thanks

---

### Post by skymera on 2010-02-07
Not 100% sure where they would be stored.

Im guessing somewhere in your Home folder.

---

### Post by Morbius1 on 2010-02-07
They're scattered all over the darn place. The two you have some kind of control over are located here:

/home/*user_name*/.config/autostart
/etc/xdg/autostart

But they don't work quite like you'd expect. For example I have one for Firefox in /home/morbius/.config/autostart/Firefox.desktop. It doesn't run on start up. Why? 

If you look at the entry it looks like this:
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=firefox
Name[en_US]=Firefox
Exec=firefox
Name=Firefox
Icon=firefox
Comment[en_US]=
[COLOR=Blue]X-GNOME-Autostart-enabled=false[/COLOR]
```If I go to System > Preferences > Startup Applications and check it off it changes [COLOR=Blue]false[/COLOR] to [COLOR=Blue]true [COLOR=Black]and it will launch at startup[/COLOR][/COLOR].

---

### Post by 3rdalbum on 2010-02-07
'Startup Applications' work after you have logged in. They can use the GUI. The rc.local is run before the GUI is started, and the contents are run as root.

---

### Post by pedro3005 on 2010-02-07
Also, the reason rc.local didn't work is you probably didn't make it executable. Try:
```
sudo chmod +x /etc/rc.local
```

---

