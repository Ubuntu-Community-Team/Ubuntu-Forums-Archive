---
title: "Gnome-Panel doesn't start on login"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Grundoko on 2010-11-28
I've had this problem multiple times on multiple different computers, on multiple different installs of Ubuntu 10.10.

It seems to only happen in Ubuntu 10.10, and not in other distros like Debian, or even Linux Mint 10 which is based on Ubuntu 10.10.


When I login, I'm greeted by my wallpaper, and nothing else. Gnome-Panel does not launch. I can use the hotkey (Ctrl + Alt + T) and then launch gnome-panel manually, and it works fine. It is not malfunctioning, but when I login, it doesn't start automatically.

I'm not 100% sure, but it seems to happen after I install my graphics driver, since that's the last thing I did before my last reboot.

I have tried resetting my gconf settings, which brought everything back to defaults, but gnome-panel still does not start on login.

Before you ask, gnome-panel is showing in the required-components in gconf-editor.


Any suggestions? I could always put it under Startup Applications, but I'll never live with myself knowing something isn't quite working right =/

---

### Post by wojox on 2010-11-28
Run these two commands from your terminal. You may need to log out and back in.


```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

### Post by ClyN3il on 2011-03-22
I'm having the same problem (in Maverick)... resetting gconf settings didn't help...

---

### Post by Arijit_Kundu on 2011-03-22
May be this can help: run gconf-editor in a terminal. Then go to /desktop/gnome/session/required_components

see the name 'panel' and confirm that gnome-panel is written as its value.

---

### Post by Biokiller2510 on 2011-05-30
Hello folks, i hope I'm not to late on this matter.

I had the same problem after i upgraded to Ubuntu 10.10 and i managed to figure a work-around for this problem, it worked for me and it has to work for you guys:

1- Open System -> Preferences -> Startup Applications
2- Click Add
3- Write Panel in the name
4- In the Command write: bash -c "gnome-panel"
5- Add a Comment if you want to (e.g: WIN!)
6- Click Add and Restart

Regards,
Pedro.

---

### Post by speedyboiz on 2013-02-19
> **wojox said:**
> Run these two commands from your terminal. You may need to log out and back in.


```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

Yes, it's work :)

Thanks

---

### Post by wildmanne39 on 2013-02-19
Old thread closed.

---

