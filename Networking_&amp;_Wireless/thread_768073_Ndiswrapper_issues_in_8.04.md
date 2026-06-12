---
title: "Ndiswrapper issues in 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by rjdohnert on 2008-04-26
Whenever I try to load the Windows drivers for any of my cards in ndisrwapper , ndiswrapper locks up the system.  i tried a card that is natively supported and the system chugs along without issue.  There is a major problem with ndiswrapper that ships with Hardy.

---

### Post by FredB on 2008-04-26
> **rjdohnert said:**
> Whenever I try to load the Windows drivers for any of my cards in ndisrwapper , ndiswrapper locks up the system.  i tried a card that is natively supported and the system chugs along without issue.  There is a major problem with ndiswrapper that ships with Hardy.
We are not wizard to guess your hardware. Can you be more specific, please ?

---

### Post by sbrbot on 2008-04-26
_Ubuntu 8.04_ (like Fedora 8 and other newer Linu distibutions) supports b43 driver and you do _not need ndiswrapper_ for _Broadcom_ wireless cards anymore! You just need to extract (using b43-fwcutter tool) Broadcom wireless card firmware into /lib/firmware directory (default directory for firmwares).

---

### Post by Sl@y3D for my n@me on 2008-04-26
I'm having the same problems. My adapter is a Netgear WG111T. When I try to connect to a wireless network, the whole operating system freezes and I can't do anything. Works perfectly on 7.10.

---

### Post by rjdohnert on 2008-04-26
> **Sl@y3D for my n@me said:**
> I'm having the same problems. My adapter is a Netgear WG111T. When I try to connect to a wireless network, the whole operating system freezes and I can't do anything. Works perfectly on 7.10.

Thats exactly one of them, the other is the DWL-G120 from D-Link, the other is a Netgear WG121 and last but not least the ZyXEL M202

---

