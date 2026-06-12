---
title: "Natty ( 11.04 ) add new session during login"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by gillza on 2011-06-04
Dear all,

My apologies if this is a really silly question but could some one explain how to add a custom session during the login prompt (besides, ubuntu, ubuntu classic etc...)?

I have created an .session entry in /usr/share/gnome-session/sessions/ but have no idea what to do beyond this point. 

Thank you!

---

### Post by heyandy889 on 2011-06-04
Not a silly question. Should be attainable. I bet that there is file somewhere where you can copy in the name of your file.

um, sorry for the vague answer, but I don't really know. Heh.

---

### Post by gillza on 2011-06-05
Ok I figured it out:
in /usr/share/gnome-session/sessions I have created new classic-gnome-metacity.session file with the following:

```

[GNOME Session]
Name=Classic GNOME Metacity
Required=windowmanager;panel;filemanager;
Required-windowmanager=metacity
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;

```

Then in /usr/share/xsessions created gnome-metacity.desktop with the following: 

```
[Desktop Entry]
Name=Ubuntu Metacity
Comment=This session logs you into GNOME with the metacity WM
Exec=gnome-session --session=classic-gnome-metacity
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0
```

Save and restart and in the login menu (bottom) we now see a new entry: Ubuntu Metacity

P.S. btw /usr/share/gnome-session/sessions/2d-gnome.session is already set with metacity as window manager so what I did was educational but not necessary :)

---

