---
title: "Network Manager and VPN Tunnel"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by bluevoodoo1 on 2007-03-11
Is there a way to _not_ tunnel all traffic through a pptp VPN connection setup with Network Manager?

---

### Post by x64Jimbo on 2007-03-11
There's an option to only use the VPN for connections to certain IP addresses/ranges. Did you try that?

---

### Post by bluevoodoo1 on 2007-03-12
> **x64Jimbo said:**
> There's an option to only use the VPN for connections to certain IP addresses/ranges. Did you try that?

Well, anytime I try to add an IP under the Routing tab the "Apply" button at the bottom gets greyed out. Is there another option I'm missing? Thanks.

---

### Post by x64Jimbo on 2007-03-12
I'm talking about an option under the "Configure VPN" portion of the NetworkManager menu. If you edit your connection properties, there should be an option in there to "Only use VPN connection for these IP addresses"

---

### Post by Reedbeta on 2007-03-12
You have to enter an IP address range, e.g. 12.34.0.0/16 (this means to use the tunnel for any IPs starting with 12.34; the 16 is the number of bits of the address to use, so 8 bits for each tuple).

---

### Post by bluevoodoo1 on 2007-03-12
I got it working now! Thanks for the help!

---

