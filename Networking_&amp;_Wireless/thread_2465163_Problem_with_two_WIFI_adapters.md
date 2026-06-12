---
title: "Problem with two WIFI adapters"
date: 2021-07-23
forum: Networking &amp; Wireless
---

### Post by thumper76 on 2021-07-23
Using Ubuntu 20.04 Desktop. I have two WIFI adapters:PCI and USB. NetworkManager seems to default to PCI and I have a real problem using the USB adapter. With a combination of command line and NetworkManager's gui I'm able to get it working, but at the first opportunity it reverts to PCI. How to I get NetworkManager to accept the WIFI apapter I choose?

---

### Post by morrownr on 2021-07-23
Use the "Forget Connection" button for any connections that you don't want to be available.

I'd give you a step by step but I am on one of the distros that is Ubuntu inside but uses a different gui for the networking. I'll bet you can find it.

---

### Post by thumper76 on 2021-07-26
Thanks. I have found the "forget connection" button and that solves the problem. There doesn't seem to a way from the command line.

---

