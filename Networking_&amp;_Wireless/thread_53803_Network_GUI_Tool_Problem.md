---
title: "Network GUI Tool Problem"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by mr_stabby on 2005-08-02
Hello,

This may be an unusual question but where can I find the Network Administration Tool? It used to be accessible via the Gnome menu in System -> Administration but it seems to have vanished along with many of the other options (possibly due to using XFCE for a while/using a crappy programs to mess with .desktop files?)

Thanks in advance,
Louis

---

### Post by Sam on 2005-08-02
```
$ gksudo network-admin
```


And to recreate the launcher
```
$ sudo gedit /usr/share/applications/network.desktop
```
Paste this
```
[Desktop Entry]
Name=Networking
Comment=Configure network devices and connections
Exec=gksudo network-admin
Icon=/usr/share/gnome-system-tools/pixmaps/network.png
Terminal=false
Type=Application
Categories=Application;System;Settings
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-system-tools
X-GNOME-Bugzilla-Component=network-admin
X-GNOME-Bugzilla-Version=1.2.0
StartupNotify=true
Encoding=UTF-8
```

---

### Post by mr_stabby on 2005-08-02
ah network-admin, brilliant.

Thank you very much (and very concise post btw :D)
Cheers,
Louis

---

### Post by mr_stabby on 2005-08-03
Thanks for your post, but it seems that I still can't get to the Network GUI program... when I attempt to execute the command, gksudo prompts me for the password as per and then halts. It doesn't give the gksudo "command not found" warning but nothing much happens. Can't see any related processes running either.

Any help appreciated,
Louis

---

