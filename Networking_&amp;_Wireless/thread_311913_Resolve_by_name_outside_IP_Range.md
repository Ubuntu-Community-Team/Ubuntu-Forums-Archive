---
title: "Resolve by name outside IP Range"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by viveknz76 on 2006-12-03
Hi,

How can I resolve the PCs outside the IP range by name?  I am currently able to resolve them by IP addresses. I can resolve the PCs within my IP range by name and IP address.

Thanks

---

### Post by spd106 on 2006-12-03
Get a DNS/WINS server.

Otherwise try static naming by adding them to the /etc/hosts file.

---

### Post by viveknz76 on 2006-12-03
The machines that are out of IP range are located in different regions but connected to the domain controller via vpn.  Where do I need the dns/wins?

---

