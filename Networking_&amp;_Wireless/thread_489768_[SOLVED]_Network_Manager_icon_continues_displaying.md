---
title: "[SOLVED] Network Manager icon continues displaying &amp;quot;connecting&amp;quot; even when c"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by jsully1 on 2007-07-01
Hi all,

This isn't a really big issue, but the Network Manager tray icon continues to display the spinning blue comet and two green orbs, and behave like it's not connected, even though I'm connected and browsing the internet right now.  Any ideas? Any more information that would be helpful?  I'm running Feisty and network-manager-gnome version 0.6.4-6ubuntu7.

Thanks!
Sully

---

### Post by jsully1 on 2007-07-02
Anyone have any ideas?  Has anyone even seen this?

---

### Post by jsully1 on 2007-07-04
The issue was that I did a chattr +i /etc/resolv.conf in an attempt to force specific DNS servers - network manager was spazzing because it couldn't update the file.

---

