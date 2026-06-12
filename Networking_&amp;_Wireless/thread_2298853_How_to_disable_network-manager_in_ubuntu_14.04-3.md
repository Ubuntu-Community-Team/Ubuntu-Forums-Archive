---
title: "How to disable network-manager in ubuntu 14.04-3"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by ice-simx on 2015-10-14
Hi,

want to manage my machine remotely and want to disable network-manager, and make entry in /etc/network/interface file for static route entry.

for current session can disable using:
# service network-manager stop

but upon reboot, it starts again.
also i have created file using command, but no success:
# echo manual | tee /etc/init/network-manager.override

i don't want to uninstall it, but to disable it only like in RHEL with "chkconfig service off" command.

---

### Post by TheFu on 2015-10-14
What about **update-rc.d**?
I just purge  network-manager. Much easier that way.

---

