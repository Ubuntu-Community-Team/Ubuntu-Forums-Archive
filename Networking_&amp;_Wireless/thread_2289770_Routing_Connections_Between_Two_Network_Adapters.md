---
title: "Routing Connections Between Two Network Adapters"
date: 2015-08-06
forum: Networking &amp; Wireless
---

### Post by tehtotalpwnage on 2015-08-06
So here's just an idea or a concept that I'm curious about. My desktop computer has two ethernet LAN ports that I can potentially use to connect to my home network. Is it possible to set up a configuration in a way that I can have both connected to my network and be able to decide which connection uses which interface.

Example: If I'm running a webserver and browsing the internet with a VPN, I want the webserver to use one LAN port and the VPN to use the other port to not interfere with my webserver.

Would this be something that'd be possible to set up?

---

### Post by TheFu on 2015-08-07
Look up a VPN with a split tunnel.

---

### Post by tehtotalpwnage on 2015-08-07
> **TheFu said:**
> Look up a VPN with a split tunnel.
Makes sense, but I honestly am TERRIBLE with OVPN and routing beyond ufw and port forwarding. Is there a guide online that can break things down for me?

---

### Post by TheFu on 2015-08-07
I learned by reading the manpages. The openvpn manpage is excellent. Routing knowledge is a different matter. Picked it up by working with some very large-scale networking experts for a decade. None of that helps you but it explains why I don't have any guides to recommend.

---

### Post by tehtotalpwnage on 2015-08-07
Eh, figures. I'll see what I can dig up. Thanks anyway! I'll edit my post if I can find a solution.

---

