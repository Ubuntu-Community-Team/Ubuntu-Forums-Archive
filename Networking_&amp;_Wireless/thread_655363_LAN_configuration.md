---
title: "LAN configuration"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by frank james on 2008-01-01
We have a new motherboard intel DQ35JO and don't seem to be able to configure the LAN for Ubuntu. The BIOS shows the periferal LAN but attempts to enable it get nowhere. The other items such as audio, firewire are all enabable, but the pointer skips over the Lan item and the identification is greyed rather than in blue like the others. Can anyone help please?

---

### Post by Predator[23rd] on 2008-01-01
Hi!

> **frank james said:**
> The BIOS shows the periferal LAN but attempts to enable it get nowhere. The other items such as audio, firewire are all enabable, but the pointer skips over the Lan item and the identification is greyed rather than in blue like the others. Can anyone help please?

Are you talking about BIOS settings here? Or have you already enabled onboard LAN and struggling for correct linux setup?

To see if your hardware is detected by Ubuntu type **cat /proc/net/dev** and check for **eth0** in the "Interface" column (assuming you only have a single ethernet card). if it shows up you are good. if not the chances that your hardware is disabled are very high.

Next step will be making sure you have eth0 also in the */etc/network/interfaces* file:
[I]auto eth0
iface eth0 inet dhcp[/I]
that should be it ...

---

