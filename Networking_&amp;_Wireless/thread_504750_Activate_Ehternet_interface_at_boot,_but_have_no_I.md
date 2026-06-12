---
title: "Activate Ehternet interface at boot, but have no IP address?"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2007-07-19
So I have multiple 10/100 Ethernet interfaces in my Ubuntu box, and I want a specific one to come up at boot and not be assigned an IP address.  I'm using this interface for bridging with vmware and some various traffic sniffing, and I just would rather it not have an IP.  How do I accomplish this?

---

### Post by SupaRice on 2007-07-23
*bump*

Anyone?

---

### Post by Mr. C. on 2007-07-24
Disable the NIC you dont want used Network Manager.  Or remove the **auto** keyword from the appropriate interface in /etc/network/interfaces.

You're short on details, so that's the best answer I can give.

MrC

---

