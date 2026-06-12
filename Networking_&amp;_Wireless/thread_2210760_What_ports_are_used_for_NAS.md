---
title: "What ports are used for NAS?"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by soupisgood on 2014-03-12
Trying to configure network assisted storage through my wireless router. It works flawlessly with the ubuntu firewall turned off but as soon as i turn it on it denies me access. Tried adding the smb:/// ports (137, 138 & TCP ports 137, 139 and 445) to no avail.

update: Disabling the outgoing section of my firewall fied the issue.. Unfortunately, this seems like a security vulnerability. At-least it narrows down the issue to an outgoing port.

update2: Deleting the rules and adding them manually for both incoming and outgoing traffic solved the issue. Aparently the default SAMBA firewall option does not work and entries must be added manually.

---

