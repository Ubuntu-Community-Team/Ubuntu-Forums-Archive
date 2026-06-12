---
title: "Netplan config for connecting to fibre using VLAN tagging"
date: 2023-07-15
forum: Networking &amp; Wireless
---

### Post by Irihapeti on 2023-07-15
I am considering changing to a fibre internet connection. My router is a PC Engines sbc running Ubuntu 22.04, using netplan to manage the WAN connection This is currently 4G wireless broadband via a modem in bridge mode.

According to the ISP, I need to set VLAN tagging, VLAN ID 10. The ISP does give a list of settings, but naturally they are for commercial (consumer-grade) routers.

I know that netplan has options for VLAN tagging. My problem is trying to determine whether the underlying ethernet port needs an IP address, or whether IP address management is left entirely to the VLAN. I've seen both used in various sample netplan configs, but no one seems to explain why.

I kind of suspect that, because I'll only ever use the VLAN connection, I don't need the underlying ethernet port to have any IP address. Can anyone clarify this for me?

---

### Post by Irihapeti on 2023-07-20
Bump

---

