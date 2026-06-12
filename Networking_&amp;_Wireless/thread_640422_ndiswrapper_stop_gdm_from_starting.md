---
title: "ndiswrapper stop gdm from starting"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2007-12-14
After i installed drivers to my card and loaded the modul and rebooted wont gdm start it simply stop after the boot screen and the only way to get it working again is to make a hard reboot and then enter recovery mode and remove the drivers for the wlan and then can i start ubuntu as normal.

Then in ubuntu can I install the card again and it work as normal, problem is that i need to uninstall it everytime i shutdown the computer.

error msg when i started gdm and loggedin in recovery mode.
[http://img139.imageshack.us/img139/4324/screenshotgy1.png](http://img139.imageshack.us/img139/4324/screenshotgy1.png)

Commands used to install the driver, (easier to understand what i'm doing i think)
sudo ndiswrapper -i ndis/net5211.inf
sudo depmod -a
sudo modprobe ndiswrapper

Commands for remove the driver
sudo ndiswrapper -r net5211


also of important ath_hal is disabled and blacklisted (think it come with each other) since madwifi wont work with my card.

---

### Post by SpinningAround on 2007-12-15
Anyone?

Ides to search for the problems, possible causes, anything?

---

