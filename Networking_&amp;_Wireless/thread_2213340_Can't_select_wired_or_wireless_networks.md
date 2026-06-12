---
title: "Can't select wired or wireless networks"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by MibunoOokami on 2014-03-26
On my laptop, the toolbar where the battery, volume and blue tooth icons are, a little box type thing has appeared over the network icon and I can no longer select which wifi network I can connect to nor alter any settings there. 

Has this happened to anyone else before and if so, how was the problem overcome? FWIW Restarting does nothing.

---

### Post by varunendra on 2014-03-26
Can you post a screenshot of it please? Cropped of course to keep it small.

Can you still pull down the nm-applet menu and open Network Manager settings ("Edit Connections..") from there?

---

### Post by MibunoOokami on 2014-03-26
I've attached a screenshot. Can't seem to edit connections at all.

---

### Post by varunendra on 2014-03-26
This is usually just a nm-applet or unity GUI glitch, should have automatically fixed itself after a reboot or log-off --> re-log-in.

If not, please try opening "System Monitor" > look for "nm-applet" under the "Processes" tab > right-click it > "Kill Process"

This will kill the process and the icon will disappear from the notification area. Then -

Press "Alt-F2" > type "nm-applet" > click the icon that comes up, or press "Enter".

The icon should be back and usable again.

---

### Post by MibunoOokami on 2014-03-26
Thanks mate, that worked.

---

