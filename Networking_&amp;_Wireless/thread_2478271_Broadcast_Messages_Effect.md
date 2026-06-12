---
title: "Broadcast Messages Effect"
date: 2022-08-21
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-08-21
With the increasing popularity of IoTs a simple home network can have a considerable amount of devices connected.

My router is capable of running VLANs so I have separated my own so that (if I remember) I can keep my personal computing separate from the other stuff.  I do this more for a security angle rather than anticipating a speed advantage.

How much of an overhead is a network of up to 25 devices on broadcast addresses, does it make that much difference and is there any significant advantage of my separating my network in to two VLANs?

My VLANs are separate subnets and devices from each are isolated from each other.

Geoff

---

### Post by TheFu on 2022-08-23
VLANs are not security. They are tagging, a suggestion, only.  Never consider VLAN subnets to be separate, since they all use the same physical transport, which has limitations.
If you want security, use physically separate LAN equipment.

If you place all devices for 1 VLAN on 1 router port, then the router, should not send traffic for that single VLAN down other ports, so some level of security could be achieved.
Broadcast packets - "I'm here" have a minimal impact on a switched network, unlike the old days of pure ethernet when we used hubs.  However, wifi is like a hub and broadcasts can matter to total bandwidth.  How much depends on local interference, wifi network performance, how many different channels can be used and which devices support those channels.

Remember that compromised devices on the same physical transport, VLAN or not, can see each other's traffic.  That probably gets forgotten by most people, who over simplify "different VLANs" are security aids.  They can be, but aren't always.

---

### Post by Geoff_Lane on 2022-08-23
Mine seem to be able to group any of the four ethernet ports to a different subnet as well as if I assign an additional SSID can group that with either subnet.  Have the choice at setup to isolate each group, not sure why one would choose to create a separate subnet and not isolate it but I don't claim to know that much about the various layers of network levels.

Geoff

---

