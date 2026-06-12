---
title: "Samba and cups slow down startup process"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Jochus on 2007-02-14
I have a samba server configured which gets automaticly mounted at /mnt/server
I also have a Windows printer (on that same physical server) which is configured in CUPS.

When I boot Ubuntu on my notebook, the startup is really slow because it stops for a very long time at bringing up Samba and Cups.
The problem is: I surf wireless. So there's no internet connection during startup When I put the LAN-cable in my eth0 BEFORE booting, startup process is really quick.

Is there a way to solve this problem?

---

### Post by mssever on 2007-02-14
It definitely sounds like CUPS and Samba are both timing out looking for a network. Try using network-manager-gnome (sudo aptitude install network-manager-gnome) to configure your wireless. On my system, all the network stuff automatically waits for wireless to become available. So my samba shares don't get mounted until after I log in.

---

