---
title: "Wired Networking Stopped Working After 18.04 Updates"
date: 2019-11-27
forum: Networking &amp; Wireless
---

### Post by scottydel on 2019-11-27
Ubuntu newb here.  Just installed 18.04 from USB onto my Windows 10 machine (dual boot).  All was great after install.  Launched Ubuntu, and Wired Networking worked.  Installed a couple apps (VS Code, Chromium, something else?), then Ubuntu prompted for some updates to Ubuntu itself, which I accepted and downloaded->installed.  One of the apps I installed, can't remember which one, required a reboot.  After reboot, Ubuntu launched but Wired Networking no longer worked.  My network card is a Realtek PCIe GBE Family Controller.  Did not know how to uninstall or revert updates to bring back to original state.

Dell XPS 8700.

Windows 10 boots fine, and the wired networking still works there, so this issue is something with Ubuntu.

Appreciate any help!

---

### Post by Skaperen on 2019-11-27
can you describe what you tried to do that got the results which "no longer worked" resulted from.  i'm curious what layer or component of your network is not working.  there are many things that could cause failure in many things.  can you open a terminal program to get a command line prompt?  do you have a 2nd computer on the same LAN (probably not since are doing dual-boot)?

---

### Post by scottydel on 2019-11-28
I didn't try to do anything in particular, it was just that the status bar at the top showed the disconnected icon for networking.  After a minute, a small popup appeared at the top with something like "networking not authenticated".  I used my phone's internet to try and do some trouble shooting to no avail.  No other computers wired into the LAN.  I could open a terminal.

However, since I just booted into Ubuntu to take a closer look and answer your questions, wired networking is now working again.

Nothing changed between original post and now.  I can't explain it.  Maybe it just needed an additional reboot.

---

