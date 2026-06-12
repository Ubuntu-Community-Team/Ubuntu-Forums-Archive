---
title: "VPN setup at home"
date: 2021-09-23
forum: Networking &amp; Wireless
---

### Post by loyd222 on 2021-09-23
Dear all, 
I think I have similar question or issue. I have setup a VPN connection on my router. within my home network I have raspberry and other Ubuntu server. When I am at home I can access both on HTTP, SSH, etc. when I am outside and using the VPN connection, my client IP is changed from 10.0.0. to 10.8.0.
From the VPN tunnel I can access the raspberry over HTTP, SSH etc, but the Ubuntu is completely invisible. The current workaround I am using is that I login over SSH to raspberry and then connecting to Ubuntu. 
Any idea what is blocking me of connecting the Ubuntu server ?
TIA

---

### Post by QIII on 2021-09-23
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2465711").

Please do not hijack the threads of other users.  That inevitably causes confusion as people try to help and end up answering two questions at once.  Both you and the OP of the original thread deserve individual attention.

While your issue appears to indicate similar symptoms, the underlying cause may be entirely different.

---

### Post by TheFu on 2021-09-23
Did you setup routing between the 2 subnets?

Would be good to tell people which VPN software is being used (don't make us guess) and to post the config files and routing tables.  Are you using wireguard, IPSec or something else?

---

