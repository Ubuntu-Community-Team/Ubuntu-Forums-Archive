---
title: "For not using wifi and hotspot at the same time"
date: 2024-08-29
forum: Networking &amp; Wireless
---

### Post by abgup1540 on 2024-08-29
I have installed Ubuntu 24.04 LTS, but I am experiencing an issue where I cannot use both Wi-Fi and the hotspot feature simultaneously. It appears that enabling one disables the other. Could you provide guidance on how to resolve this issue?

---

### Post by currentshaft on 2024-08-29
Some wireless cards don't support concurrent mode. Which card are you using?

---

### Post by abgup1540 on 2024-08-30
When I ran the command "lspci' in the terminal and saw the network controller it showed "Intel Corporation Wi-Fi 6 AX201 (rev 20)" . If this is not related to the wireless card then please send me how could I check the wireless card information.

---

### Post by currentshaft on 2024-08-30
iw list

Look for "Supported interface modes"

---

