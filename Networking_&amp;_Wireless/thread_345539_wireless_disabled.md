---
title: "wireless disabled?"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Baruch on 2007-01-24
I have a wireless USR 5416 PCI card. I finally got the drivers installed, but now when I run ```
lshw -C network
``` instead of saying ```
*-network UNCLAIMED
``` it says ```
*-network DISABLED
``` How can I enable it?
BTW, I'm running Ubuntu Server - Edgy, so I only have a console.

---

### Post by spd106 on 2007-01-24
Try enabling the interface with **sudo ifconfig ethX up**, or if it exists in the /etc/network/interfaces file run **sudo ifup ethX**.

---

### Post by Baruch on 2007-01-24
> **spd106 said:**
> Try enabling the interface with **sudo ifconfig ethX up**, or if it exists in the /etc/network/interfaces file run **sudo ifup ethX**.

Thanks! It worked. But what is this interfaces file?

---

### Post by spd106 on 2007-01-24
Check out **man interfaces**

It's where the settings are stored for each network interface. If it has a line "auto ethX" then your interface will be activated on boot.

---

