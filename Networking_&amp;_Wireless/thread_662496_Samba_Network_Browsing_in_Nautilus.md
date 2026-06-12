---
title: "Samba Network Browsing in Nautilus"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Bocy75 on 2008-01-09
Hi everyone!

First of all, sorry for my english, its not the best yet :)
I  have a  Ubuntu 7.10 box, and after messing around with samba configurations, i hopelessly screwed them up, so i decided to completely remove all the samba packages from  Synaptic, (what a mistake!) and after a reboot i reinstalled libsmbclient, samba, samba-common, smbclient packages. Everything works well, i can acces to windows shares from terminal, but not from nautilus anymore...
When opening Nautilus - Network, i  see the "windows network" icon, but when clicking on it, nothing happens. No error msg, nothing...
After that i completely removed all the nautilus packages, and reinstalled them, but no affect.
i also tried to use other samba browsers, such as xsmbrowser, linneighborhood, etc., but natutilus is far more better for me.
Any ideas would be greatly appretiated.

---

### Post by Brandon.Viking on 2008-01-09
I think from memory that Nautilus uses the gnome-vfs stuff. Perhaps you uninstalled that without realising through a dependency. Just a suggestion on what to check. Hope that helps.

Brandon.

---

### Post by Bocy75 on 2008-01-09
Thank you very much, you made my day! :)
The missing package was** libgnomevfs2-extra**

---

