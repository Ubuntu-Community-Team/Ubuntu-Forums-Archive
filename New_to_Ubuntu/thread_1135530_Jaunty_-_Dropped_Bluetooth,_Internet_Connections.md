---
title: "Jaunty - Dropped Bluetooth, Internet Connections"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by clintbradford on 2009-04-24
Installed new version yesterday via Ubuntu's system upgrade. My system used to drop Internet connection about every ten minutes for thirty seconds or so, then re-connect by itself. Not it drops out every five minutes or so.

And, after having flawless Bluetooth mouse performance with the last version, Jaunty now drops Bluetooth mouse and keyboard connection, forcing re-boots of the system.

Any hints?

---

### Post by geoffatmk on 2009-04-26
Similar problem.  Dell bluetooth mouse has worked fine under Intrepid but upgrade to Jaunty (Via package manager) is causing problems.  If I leave the machine idle for more than ten minutes, the connection is lost and I cannot reconnect.  Have to delete mouse and reconnect which is time consuming and will stop me upgrading all other machines until I find a solution.

Is there a way to automate the Bluetooth search and connect so that although the mouse is idle the PC thinks it is active?

Can anyone offer any ideas?

---

### Post by dougsnell on 2009-04-26
FWIW, I had this resolved for 8.10, and with 9.04 the fix is not the same.  The article I had marked to resolve this was ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234202](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234202)).

For anyone who can offer insight into this (and FWIW), I'm using Bluetooth via a USB dongle adapter.  I can re-produce the problem if I manually stop/start/restart the Bluetooth services (some articles suggest it will work if you stop/start instead of restarting ... that is not true).  It also forgets the settings if you reboot (I had never fixed that, but didn't reboot very often).

---

