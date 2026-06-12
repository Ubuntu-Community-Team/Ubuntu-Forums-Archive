---
title: "Unable to get network manager icon to display and function in tool bar"
date: 2024-10-18
forum: Networking &amp; Wireless
---

### Post by shankara2 on 2024-10-18
I have been scrolling through the forums to correct the problem with limited success.  I've gotten the network manager icon to display with no functionality.  I double checked the appropriate packages were installed.  I double checked the network manager would activate on startup.

I'm running Ubuntu 22.04.5 LTS with the XCFE 4.16 desktop.  Below is the contents of my /etc/xdg/autostart/nm-applet.desktop.save file.  There is probably something simple that I'm missing.  I would appreciate any help.

[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=dbus-launch nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=nm-applet

Many Thanks

---

### Post by bobunderwood99 on 2024-10-18
Should the end of the desktop file name be ".save"?

/etc/xdg/autostart/nm-applet.desktop

---

