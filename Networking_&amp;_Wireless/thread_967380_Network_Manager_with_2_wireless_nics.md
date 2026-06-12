---
title: "Network Manager with 2 wireless nics?"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by kmand on 2008-11-02
My laptop has a built in G nic, and I also have a USB N nic. At home I have an N access point and use the USB. When I go mobile I would rather just use the built in G.

The 8.10 Network Manager lets me select between wired and wireless, but I don't see how to switch between different wireless nics. I would like to make it use the N if its plugged in.

Any suggestions.

---

### Post by kmand on 2008-11-03
I found an error I had made in /etc/modules, now both the G and N nics come up at boot, and are managed by Network Manager.

The Gui lets you choose between wireless and wired. Once you pick wireless it connects both NICS. There is a choice bullet for each ssid it sees for each, but no choice for disable one of them.

Of course I can manually down the one I don't want (the G) with ifconfig, but then I have to also manually add a default route through the N.

I guess I can live without using the GUI to choose, but I'm surprised there isn't some provision.

---

