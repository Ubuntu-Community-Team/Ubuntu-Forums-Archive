---
title: "Starting multiple X servers"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by prashant112358 on 2009-05-20
Hi all,


How can I start multiple X servers by logging into same user and using same desktop environment like KDE or GNOME.
Is this possible by editing .xauthority, .xinitrc etc files???
Pls, help urgently.

THANKS IN ADVANCE

---

### Post by ibuclaw on 2009-05-20
You can reference this post I made several months ago: [http://ubuntuforums.org/showpost.php?p=6748933&postcount=17](http://ubuntuforums.org/showpost.php?p=6748933&postcount=17)


But the general step-by-step you go about it is:
```
sudo gedit /etc/X11/Xwrapper.config
```
Change 'allowed_users=console' to:
```
allowed_users=anybody
```


Then
```
gedit ~/.xinitrc
```
and put in the apps you wish to start on the new X server.

A basic Gnome Desktop would be:
```

##!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-window-manager &
{
    (gnome-panel 2> /dev/null &)
}

```


Save, then type in:
```
startx -- :1 vt12
```
To start a new X server on tty12 (Ctrl+Alt+F12 to switch to it).
By normal convention, you can use anything from **vt8** to **vt12** for extra X servers, and for each X server you add, you increment the display number **:1** to **:2** and so forth

Regards
Iain

---

