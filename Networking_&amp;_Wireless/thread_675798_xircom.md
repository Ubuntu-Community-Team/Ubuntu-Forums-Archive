---
title: "xircom"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by PhilipGanchev on 2008-01-23
After resuming from sleep or suspend, my PCMCIA ethernet card is dead. It works again if I remove and reinsert the driver module, xircom_cb. Is there a way to fix this or to remove/reinsert automatically on sleep/hibernate? Even if I add "xircom_cb" under MODULES in /etc/default/acpi-support, it still does not work: the dmesg output is attached.

I'm running Ubuntu Feisty (Linux 2.6.20-16-generic #2 SMP) on an IBM Thinkpad A21m.

% lspci | grep -i ethernet 
06:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)

I can't find any relevant info on the web.  Should I file a bug somewhere?

---

### Post by bwtranch on 2008-01-23
I would search and/or file a bug report with launchpad.

---

