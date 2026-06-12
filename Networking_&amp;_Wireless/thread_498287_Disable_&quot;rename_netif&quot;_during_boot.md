---
title: "Disable &quot;rename_netif&quot; during boot"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Helix. on 2007-07-11
During boot, after "starting network" appears, I get a error.

"rename_netif: error renaming interface wlan0 to eth1"

It hangs on this for a minute or two, then continues to boot.

Since it is not doing anything (wlan0 is still wlan0), how do I stop this from attempting to rename my wireless card during boot?

---

### Post by netztier on 2007-07-11
> **Helix. said:**
> During boot, after "starting network" appears, I get a error.

"rename_netif: error renaming interface wlan0 to eth1"

It hangs on this for a minute or two, then continues to boot.

Since it is not doing anything (wlan0 is still wlan0), how do I stop this from attempting to rename my wireless card during boot?

Find out and note the MAC address of the WLAN card in question, and then take a look at the file **/etc/iftab** to check if there's any weird/incorrect/stale MAC-address to interface name assignments and correct or remove them as appropriate.

Hope this helps

best regards

Marc

---

