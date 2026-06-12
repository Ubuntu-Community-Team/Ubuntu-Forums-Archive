---
title: "Bond not using both NICs"
date: 2023-09-05
forum: Networking &amp; Wireless
---

### Post by halozerox on 2023-09-05
Good Day

Requiring some help/clarification on bonding 2 NICs.

I have a bond setup, and using bmon it seems that only one of the NICs is actually doing something.

Added a screenshot of the netplan config.

Thank you in advance for any help.

---

### Post by TheFu on 2023-09-05
Please post text, not images. Help people who pay for bandwidth.  Plus, it makes it easier to point out issues when a text copy/paste can be used.

The typical issue with bonding is a simple misunderstanding.  Bonding doesn't make single-threaded throughput faster. It is still limited to what a single NIC can provide.  However, if there are multiple processes pushing/receiving network traffic, then the total bandwidth for the system should expand to the bond capacity, assuming each of the processes is pushing that amount of data and other factors aren't limiting it.

It should also be obvious that bonding requires network equipment that supports the protocol. Without that, it doesn't work, regardless of your OS configuration.  That network equipment is usually the cut off between "managed switches" and "unmanaged switches."  Managed switches almost all support "Link Aggregation."   Look for "IEEE 802.3ad" support in the switch specifications.

Also, if the MTU is modified, ensure that all the network equipment can support the new size.  Often, there are devices that fudge a bit on the exact size supported so we need to reduce the MTU just a bit to ensure it all fits.

---

### Post by halozerox on 2023-09-06
Thank you, maybe that is the case. Veeam is set to use multiple threads, but could be that the NIC is not saturated enough to require the second NIC?

---

### Post by TheFu on 2023-09-06
> **halozerox said:**
> Thank you, maybe that is the case. Veeam is set to use multiple threads, but could be that the NIC is not saturated enough to require the second NIC?

I've used Veeam to backup ESXi VMs for a client.  Meh. It is expensive for what is easily better achieved using F/LOSS. In short, I wasn't impressed, but that was in 2010, perhaps it is better now.

I have an APU2 router (low power, 12W) at home running OPNSense with an AMD 4core 64-bit CPU with 3 Intel i210 NICs. This is a flavor of BSD.  Anyway, single threaded performance on the GigE NICs caps out around 350 Mbps, but if I startup multiple transfers and multiple connections are used, then I can saturate the GigE NIC to over 920 Mbps.  More cores get involved.  I strongly suspect this is what you are experiencing, but it is impossible to say since no data has been shared to prove or disprove it.

---

