---
title: "routing dhcp requests"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-02-25
I am having trouble getting my clients a DHCP address.  in my routing table I have this:
```
destination gateway genmask
0.0.0.0 192.168.0.1 0.0.0.0
```

When I attempt to request a dhcp address, I see on the server:
```
IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOT/DHCP Request from mac
```

dhcp is listening on the right interface.  I am not sure why the server is not responding.

---

### Post by wildmanne39 on 2018-02-25
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-02-26
Are you using isc-dhcp-server?

What do you see in the logs when a machine makes a request?

Any firewall in place?

---

### Post by SeijiSensei on 2018-03-01
Somehow this is now marked [SOLVED] though the OP has not come back to explain what the problem was or its solution.

---

### Post by DuckHook on 2018-03-01
> **SeijiSensei said:**
> Somehow this is now marked [SOLVED] though the OP has not come back to explain what the problem was or its solution.
OP may have solved the matter. Although it is good netiquette to follow up with the solution, there is no obligation for any forum user to do so.

---

