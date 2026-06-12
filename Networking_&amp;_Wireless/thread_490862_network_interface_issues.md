---
title: "network interface issues"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by dcorwin822 on 2007-07-02
hi i'm running LAMP ubuntu on a computer of mine... the motherboard i was originally using had a onboard nic... cool...  than the motherboard died... not cool...  so i was lucky to be able to replace it with the exact same model motherboard :-)  than came issues.... now  ETH0 is assigned to a mac address on the old motherboard!!!  Eth1 is the add-on card and eth2 is the new motherboard's onboard nic.  WTF is up with that??? and how do i correct it? help!

---

### Post by kevdog on 2007-07-03
Try editing the /etc/iftab file

gksu gedit /etc/network/interfaces.

Delete the old MAC address, and then change the interface names associated with the remaining MAC addresses.

---

### Post by dcorwin822 on 2007-07-03
awesome worked like a charm!

---

