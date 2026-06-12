---
title: "WPC55AG (Atheros Chipset) - PCI Wireless Card"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by DarthDie on 2007-02-18
Hi all, im new to ubuntu (and linux for that matter) and i am trying to get wireless internet working on it with a linksys WPC55AG v1.2 wireless card , i have succesfully installed ndiswrapper and installed the driver for the card using it, but it wont show up in admin->networking. Can someone help me get it working?

---

### Post by spd106 on 2007-02-18
I don't think you need ndiswrapper, your card should be supported by the madwifi driver. Just check that the linux-restricted-modules package has been installed (use Synaptic) and you should find that there is an interface called ath0.

---

### Post by DarthDie on 2007-02-18
Ok thanks - I checked for it and it wasnt installed - installing now will edit.
Thanks!I can now see it in admin-networking...now to get it working :D

---

