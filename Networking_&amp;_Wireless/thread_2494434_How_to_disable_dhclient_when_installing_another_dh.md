---
title: "How to disable dhclient when installing another dhcp software"
date: 2024-01-16
forum: Networking &amp; Wireless
---

### Post by Irihapeti on 2024-01-16
I have a PC Engines single board computer running Ubuntu 22.04 which I've been using as my router. Recently, I've been playing with IPv6 and discovered that there are problems with dhclient in handling IPv6 prefixes. There are a number of other dhcp packages available, but I can't remove dhclient; it wants to take half the networking system with it. Presumably, it's not a good idea to run two dhcp programs, so how do I disable dhclient (and not the rest of the stack) and allow another program to take over?

---

### Post by SeijiSensei on 2024-01-16
How about assigning static addresses instead of using DHCP?

---

### Post by Irihapeti on 2024-01-16
Is this on the lan side or on the wan? Because the ISP only offers DHCPv6, and I gather that's fairly common.

---

### Post by SeijiSensei on 2024-01-17
If you're dependent on your ISP, then I don't know of a solution.

---

### Post by Irihapeti on 2024-01-18
Thanks. Not to worry. I went back over a how-to I'd been using and discovered that I'd missed out a section. Once I'd done that bit, it worked.

And incidentally, I discovered that removing dhclient on a server only removes ubuntu-minimal, unless, I suppose, you've installed masses of other packages that depend on dhclient. dhclient is being replaced in Noble which should make it easier when the time comes to upgrade.

---

