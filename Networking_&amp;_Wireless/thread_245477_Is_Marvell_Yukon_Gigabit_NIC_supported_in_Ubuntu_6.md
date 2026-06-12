---
title: "Is Marvell Yukon Gigabit NIC supported in Ubuntu 64?"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by carboto on 2006-08-27
I set the network card to obtain IP through DHCP. It doesn't work. I change to a static IP address, it still does not work. Since it works in SUSE Linux Enterprise Desktop 10 (64 bits), it should work in Ubuntu as well. I'm very puzzled. Does someone have the same problem?

NIC is Marvell Yukon 88E8001 Gigabit Ethernet.

---

### Post by Ausus on 2006-08-28
Hi carboto,

Well I dont use the ethernet card.
But my system see the specific card.
My mobo ASUS A8N32 SLI Deluxe.
I'm not connected to a network, stand alone system.

Regards

---

### Post by carboto on 2006-08-28
So, what do you use it for?

---

### Post by jespdj on 2006-09-13
> **carboto said:**
> I set the network card to obtain IP through DHCP. It doesn't work. I change to a static IP address, it still does not work. Since it works in SUSE Linux Enterprise Desktop 10 (64 bits), it should work in Ubuntu as well. I'm very puzzled. Does someone have the same problem?

NIC is Marvell Yukon 88E8001 Gigabit Ethernet.

Yes, it is supported!

I have an Intel Core 2 Duo E6600 + Asus P5B Deluxe. This motherboard contains  two Ethernet controllers: a Marvell Yukon 88E8001 (PCI) and a Marvell Yukon 88E8056 (PCI-E).

My problem is that the 88E8001 works, but the 88E8056 does not. See [my thread](http://ubuntuforums.org/showthread.php?t=256867&highlight=Marvell).

---

