---
title: "No connection with Huawei E367 dongle, Lubuntu 14.04"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by Hannu Mikael on 2014-05-27
I try ewerything in network connections, but no result.
In Ubuntu and Mint is network icon, where you can create 3G-connection, and E367 works fine, but why I can not do the same in Lubuntu?

---

### Post by Hannu Mikael on 2014-05-28
Terminal code:
nm-applet
Find file:
~/.config/lxsession/Lubuntu/autostart
add to that file:
nm-applet

(all files you can see: Alt + h)
Reboot and now in the panel is nm-applet icon.
Create connection in the same way, like Ubuntu and Mint.

---

