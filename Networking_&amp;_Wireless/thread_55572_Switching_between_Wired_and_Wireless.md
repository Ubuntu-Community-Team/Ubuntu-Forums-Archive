---
title: "Switching between Wired and Wireless"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by NMUrugbysteve on 2005-08-09
Is there an easy way to switch from a wireless connection to a wired one on a Thinkpad R51? I try to enable my wired after using a wireless connection, it enables, but then neither connection works. I know this is a total noob question and I apologize in advance.

---

### Post by StacyWebb on 2005-08-09
from a terminal

sudo ifdown wlan0
sudo ifup eth0

then vice versa to switch back to wireless (assuming that wlan0 is you wirless card)

---

### Post by NMUrugbysteve on 2005-08-09
[QUOTE=StacyWebb]from a terminal

sudo ifdown wlan0
sudo ifup eth0

then vice versa to switch back to wireless (assuming that wlan0 is you wirless card)[/QUOTE]
 Thanks, I"ll try this when I get home to my comp.

---

