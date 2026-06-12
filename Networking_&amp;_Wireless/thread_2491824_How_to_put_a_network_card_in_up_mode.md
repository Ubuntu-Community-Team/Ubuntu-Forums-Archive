---
title: "How to put a network card in up mode?"
date: 2023-10-22
forum: Networking &amp; Wireless
---

### Post by hack3rcon on 2023-10-22
Hello,
I want to put my network card in up mode without IP address. For this purpose, I edited the **/etc/network/interfaces** file and added the following lines:
```

auto <interface>
iface <interface> inet dhcp
BOOTPROTO=dhcp

```
Is it OK?


Thank you.

---

### Post by TheFu on 2023-10-22
/etc/network/interfaces has been deprecated since at least 20.04 and perhaps back to 18.04. That file is meaningless.  Canonical switched to netplan, so you'll need to use that instead.
[https://netplan.io/](https://netplan.io/) is the project site and documentation.

I've never used "BOOTPROTO=dhcp".  I avoid using DHCP for my systems.

---

