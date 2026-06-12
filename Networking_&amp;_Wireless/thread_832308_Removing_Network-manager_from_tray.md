---
title: "Removing Network-manager from tray?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by antm88 on 2008-06-17
Hi, is there a way of accessing the menu which you get from left clicking on the network manager tray icon? I want to run my computer ultra minimalistic (no panels) but i need access to that menu to choose wireless networks, enable VPN etc.

Thanks, Ant

---

### Post by rlzyoner on 2008-06-17
You could do the necessary tasks from the terminal.

eg 

iwlist scanning (to scan foe wireless networks in range)
iwconfig mode Managed (set mode)
iwconfig essid ESSIDTOCONNECTTO (connect to a network etc)

More commands would be needed but you get what I mean

---

### Post by antm88 on 2008-06-17
Ok fair enough, I had hoped there was some way of launching the same dialogue. I'll stick with the panel config for now. It seems a bit strange that the network-manager is not integrated into the main menu.
Thanks for your help!

---

### Post by rlzyoner on 2008-06-17
There may be (probably is) an easier way of doing it, i just aint too sure

---

