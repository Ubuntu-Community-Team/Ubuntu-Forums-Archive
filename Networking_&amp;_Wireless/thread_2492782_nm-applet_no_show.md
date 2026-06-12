---
title: "nm-applet no show"
date: 2023-11-22
forum: Networking &amp; Wireless
---

### Post by VMC on 2023-11-22
On Xubuntu, nm-applet doesn't not show up on the panel. It did show up on first panel profile change, but never again.
I found a solution online:

> change '/etc/xdg/autostart/nm-applet.desktop', Exec=nm-applet to Exec=dbus-launch nm-applet.

Has anyone else has issue of nm-applet not showing on panel? I don't remember in the past this being an issue.
Some have said the above change didn't work for them.

---

### Post by #&amp;thj^% on 2023-11-22
It's always shown here, from Jammy to Noble and beyond. :)
```
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=nm-applet
```
possible trouble shooting needed.

---

