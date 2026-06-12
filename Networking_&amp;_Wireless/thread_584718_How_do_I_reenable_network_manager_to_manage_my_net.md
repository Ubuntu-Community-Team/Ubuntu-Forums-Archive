---
title: "How do I reenable network manager to manage my network after manually configuring it?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by wersdaluv on 2007-10-21
I manually configured my network. Now, Network Manager does not manage my wireless network anymore. 

How do I re-enable network manager to manage my wireless network?

---

### Post by jnorthr on 2007-10-21
try
sudo /etc/init.d/networking restart
this script may rebuild it's internal tables and if that does not work try to reboot your system.

---

### Post by wersdaluv on 2007-10-21
> **jnorthr said:**
> try
sudo /etc/init.d/networking restart
this script may rebuild it's internal tables and if that does not work try to reboot your system.

Tried the script and rebooting, but they didn't work. :(

Thanks for the reply anyway! :KS

---

