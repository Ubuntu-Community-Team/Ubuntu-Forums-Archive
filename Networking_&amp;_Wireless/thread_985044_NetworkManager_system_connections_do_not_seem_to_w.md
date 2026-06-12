---
title: "NetworkManager: system connections do not seem to work"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Meson on 2008-11-17
When editing a connection for NetworkManager, checking the "System setting" box does not seem to have any effect.  I expect to see such connection listed in /etc/NetworkManager/system-connections, but I don't.

I'd also expect a "System setting" connection to start back up when I resume from suspend BEFORE I log in, but it doesn't.

---

### Post by grenadier32 on 2008-11-27
I appear to have the same problem. Checking "System setting" under a wireless connection doesn't actually save anything; if I check in the same configuration window after hitting OK, it won't still be checked. Maybe the config program needs root or something to save there? Or does it communicate with some sort of daemon?

---

### Post by sshock on 2008-11-30
I noticed the same thing.  Then I found a couple bug reports:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/278216](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/278216)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/293820](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/293820)

So a workaround is to make sure to change some other setting at the same time.

---

