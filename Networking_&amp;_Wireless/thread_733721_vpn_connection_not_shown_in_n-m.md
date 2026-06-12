---
title: "vpn connection not shown in n-m"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by _ai on 2008-03-24
I'm using hardy beta.
I install the pptp packages and am able to configure a new vpn connection with the network manager applet.  However, this new connection does not appear under VPN connection (like it does under Gutsy).   The connection can be edited, however, and I can find the files for it under ~/.gconf

Did the location where these are shown change?  I didn't find any recent posts/bug reports about this....

dpkg --list | grep network-manager
ii  network-manager                            0.6.6-0ubuntu2                network management framework daemon
ii  network-manager-gnome                      0.6.6-0ubuntu1                network management framework (GNOME frontend
ii  network-manager-pptp                       0.6.5+svnhead2574-0ubuntu1    network management framework (PPTP plugin)

---

### Post by bdk6m2007 on 2008-03-28
I've got the exact same problem here.  :(

---

### Post by bdk6m2007 on 2008-03-28
I uninstalled network-manager-pptp and installed network-manager-vpnc to try a diffferent VPN and it worked as expected.  Looks to me like a bug with the network-manager-pptp package.  You should probably file a bug.

---

