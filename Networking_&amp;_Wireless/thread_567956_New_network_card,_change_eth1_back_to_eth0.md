---
title: "New network card, change eth1 back to eth0?"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by rogblake on 2007-10-05
I swapped out my malfunctioning Realtek network card for an Intel unit. My Dapper system detected the new card OK, but set it up as eth1 instead of eth0. Since this is the only NIC in this computer, I would like to change it back to eth0 -- where is this configured? (In older Linux distributions it would be an alias in /etc/modprobe.conf or modules.conf, but that does not seem to be the case here.)

---

### Post by kevdog on 2007-10-05
Check out /etc/iftab!!

---

### Post by rogblake on 2007-10-05
> **kevdog said:**
> Check out /etc/iftab!!

Thank! I entered the mac address of the new card for eth0, rebooted, and that did the trick!

---

