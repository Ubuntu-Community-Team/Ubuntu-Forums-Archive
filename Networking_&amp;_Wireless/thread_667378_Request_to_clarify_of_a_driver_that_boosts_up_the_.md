---
title: "Request to clarify of a driver that boosts up the network on Ubuntu 7.10"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by BhRaviKiran on 2008-01-14
Hi,
    We have downloaded Ubuntu 7.10 from Ubuntu download section and burnt to the CD and installed successfully. When we tried to set up the network, we came to know that a network driver software by name
" RTL 8169 for Ubuntu 7.10" need to be installed such that interner and network facilities can be provided.

Could anybody tell us where i can find RTL 8169 from Ubuntu 7.10.

Similarly, is there any combination by name RTL 8169/8110 for Ubuntu 7.10?

Thanks in advance and we are in a pressure situation please do the needful.

Thanks & Regards,
Ravi.

---

### Post by tgalati4 on 2008-01-15
From a terminal, post the output of:

>lspci -v

We need the actual output to determine the type of network chipset and thus the appropriate driver.

---

