---
title: "Connection Manager in Gnome keeps connecting to neighbour's Wi-Fi"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by softtower on 2008-10-14
My stupid connection manager (under Gnome in 8.04) keeps connecting to my neighbor's open Wi-Fi which pisses me off.

I tried deleting his network using "Edit Wireless Networks" feature but eventually it reappears and the laptop connects to it. 

I am tired of manually disconnecting and reconnecting to my own. Is there any way to just shut it off completely? Or, perhaps, set a priority to different wifi spots?

Thank you.

---

### Post by mssever on 2008-10-15
> **softtower said:**
> My stupid connection manager (under Gnome in 8.04) keeps connecting to my neighbor's open Wi-Fi which pisses me off.

I tried deleting his network using "Edit Wireless Networks" feature but eventually it reappears and the laptop connects to it. 

I am tired of manually disconnecting and reconnecting to my own. Is there any way to just shut it off completely? Or, perhaps, set a priority to different wifi spots?

Thank you.Your neighbor should secure his network. :)

You didn't mention whether you're using NetworkManager or something else. I'm assuming NetworkManager. If you open up gconf-editor and look under /system/networking/wireless/networks, you'll see all the known networks. You can delete the entry for your neighbor's network.

---

