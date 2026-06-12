---
title: "Wireless causes lock-up"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by nauziem on 2010-04-03
My system is an Asus Eee 1005P running UNR 9.10

According to terminal responses:
AR 9285 Wireless Network Adapter (PCI-Express)
Driver = ath9k
Atheros Communications Inc.

The system has a function key to disable wireless, when wireless is disabled the netbook works 100% fine, when it is enabled however, it connects to my router (displaying a confirmaation message), then the system locks-up.

Nothing clicked on the desktop has any effect. Menus opened from the system tray freeze on the screen after an interaction ends. Disabling the wireless does not stop the problem, the only way to restore the system to regular function is to reboot.

edit: I used Update Manager earlier today and downloaded/installed before the problem took hold

I've been trying to find a solution to this, but am clutching at straws, any help greatly appreciated :)

---

### Post by nauziem on 2010-04-03
Update: the crash happens when the netbook is connected to the router via ethernet cable too... heh, this should make things challenging.

---

### Post by nauziem on 2010-04-03
After using the following in terminal, issue seems to be resolved.
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux backports-modules-wireless-karmic

Source: [http://ubuntuforums.org/showthread.php?t=1309605](http://ubuntuforums.org/showthread.php?t=1309605)

For the sake of caution I'll give it a day or two and report back :)

---

### Post by nauziem on 2010-04-05
Issue seems to be resolved. :)

---

### Post by shebaw on 2010-04-05
The default drivers for the Atheros 9k wireless cards are real pain in the @$$!!! The backport modules fix the problems but often break the ATi graphics card drivers.

---

### Post by nauziem on 2010-04-05
Heh, glad im on a netbook with no such luxury as a graphics card then... that would not be fun :S

---

