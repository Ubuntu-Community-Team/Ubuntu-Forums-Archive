---
title: "Eth0 alternatively disabled and enabled on boot"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by barry1234 on 2016-09-11
Hi there,

I have an old laptop running Ubuntu server 14.04. When I boot, eth0 alternatively works and doesn't work. In other words: on the first boot, eth0 works. When I reboot, it doesn't even show up in ifconfig. When I reboot again, eth0 works again. The problem might be related to the bios, since every time I go into the BIOS on boot to make sure the PCI lan is enabled, the count increases (e.g., if I'm rebooting on a turn where eth0 shouldn't work and I go into the BIOS, eth0 works).

Anyhow, when eth0 isn't working, it doesn't show up in ifconfig, it isn't in lpci and [dmesg | grep Ethernet] doesn't return any results.

What could cause this?

---

### Post by wildmanne39 on 2016-09-11
Have you tried another pci slot? cleaned the card ends and the slot? it sounds like it may be going out. It would show up in lspci unless it is turned off in the bios or not seated in the pci slot correctly or is not working properly.

---

### Post by barry1234 on 2016-09-11
> **Wild Man said:**
> Have you tried another pci slot? cleaned the card ends and the slot? it sounds like it may be going out. It would show up in lspci unless it is turned off in the bios or not seated in the pci slot correctly or is not working properly.
Thanks for the feedback. It's an old laptop, so I can't remove the network adapter or move it to another slot, nor clean the contacts.

Besides, if it were a hardware problem, like a bad contact, you'd expect the card to randomly give out, or at least after some movement or a jolt or something like that. Now, it's not random; it happens completely predictably on every other boot.

---

