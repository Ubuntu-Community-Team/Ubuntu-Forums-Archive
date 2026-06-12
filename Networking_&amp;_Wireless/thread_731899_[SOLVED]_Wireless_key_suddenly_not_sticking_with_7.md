---
title: "[SOLVED] Wireless key suddenly not sticking with 7.10"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by Kensey on 2008-03-22
In  the last couple of days, I think after a round of updates, Ubuntu has stopped connecting automatically to my wireless network.  If I click the wireless-network icon in the menubar, the connection properties come up, then if I click Configure, I see the correct SSID and encryption type and a masked key.  If I re-enter the key, the network connects fine, but next time I log out and log in to my laptop it isn't connected again.

My wireless key is stored in GNOME Keyring Manager; I granted permission for it to always be accessible to the wireless network manager, and it's still there, but I guess for some reason either it's no longer accessible, the network-manager no longer knows to get it there, or for some reason the network-manager is no longer trying to connect to the wireless network on login.

Any ideas?

---

### Post by EricDB on 2008-03-22
After several months of fighting NetworkManager on this sort of thing, (plus other issues like not being able to tell it **not** to auto-connect to a particular network) I moved to  [Wicd]("http://wicd.sourceforge.net/").  Since then, I've mostly forgotten about my wireless since it really "just works".

---

### Post by Kensey on 2008-04-17
It bothered me that the "solution" was to dump the standard utility without knowing what the actual problem was, so I kept poking at this.  As it turns out, apparently the issue is that something removed the symlink in /etc/rc2.d for the "networking" init script.

I reinstalled network-manager-gnome (which uninstalled Wicd), reestablished the runlevel 2 networking init script symlink as "S12networking":

$ sudo ln -s /etc/init.d/networking /etc/rc2.d/S12networking

...rebooted, and voila, my wireless works seamlessly again with the standard Network Manager.

Now I'm forced to wonder, which update or new package removed the networking symlink in the first place, and what packager thought it would be a good idea to do that without so much as a by-your-leave??

---

