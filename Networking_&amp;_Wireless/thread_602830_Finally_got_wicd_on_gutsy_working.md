---
title: "Finally got wicd on gutsy working"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Joshua66 on 2007-11-04
Hi,
I upgraded from feisty to gutsy yesterday and my wireless promptly stopped working.
I had been using wicd more or less without problems on feisty.
Upon upgrading, 
'iwlist eth1 scan' worked fine, but 'dhclient' would not seem to be able to talk to the AP and get an IP.  I didn't get any errors, but it just kept retrying with longer and longer timeouts.
Rebooting didn't help.

So on a whim, I uninstalled wicd and reinstalled network-manager/network-manager-gnome, rebooted, and successfully connected to an AP.  Then I uninstalled network-manager/network-manager-gnome, reinstalled wicd, rebooted again, and now wicd seems to be working fine!

I've no idea why this worked, but hope it helps someone.
Josh

---

