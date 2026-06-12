---
title: "Remove a wireless AP from network manager?"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by jakev383 on 2007-07-31
I have a couple networks that I've connected to wirh network-manager (Gnome).  I want to remove a couple of the APs from there, since I'm going to be changing the wireless security.  Does anyone know where this data is kept?
Thanks in advance.

---

### Post by spd106 on 2007-08-01
Configuration settings are stored in gconf, just delete the network essid keys.

See this wiki page for details.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by jakev383 on 2007-08-01
Thanks.  Just needed the bump in the right direction.....
For those that can't find it, use your "Configuration Editor" if you have it in the menu, and select System -> Networking -> Wireless -> Networks and you'll see the APs you've connected to and their details.

Thanks again spd106!

---

