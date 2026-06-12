---
title: "Lubuntu 14.04 has no internet connection"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by f-lobo on 2016-06-22
Hi:

I just upgrade Lubuntu 14.04.4 from former versions. Previously wired and wreless connection works fine, but now if I login in Lubuntu dekstop network manager does not work. However if I login recuperation panel from GRUB and activate network and after resume network manager works correctly.

How can get this login directly in Lubuntu desktop?

Thank you very much. And I apologize my poor english.

---

### Post by ajgreeny on 2016-06-22
I seem to remember there was a problem with network-manager not being started automatically in Lubuntu 14.04.
See [http://ubuntuforums.org/showthread.php?t=2234388](http://ubuntuforums.org/showthread.php?t=2234388)

Go to Preferences ->Default applications for LXSession -> Autostart tab.

Check that **network** is enabled in the tick-box, and if it is not add it manually.

---

### Post by f-lobo on 2016-06-23
Thank you, but i already tried this solution without success. Network is ticked in autostart tab, and network icon is in the panel but network is not active.

---

