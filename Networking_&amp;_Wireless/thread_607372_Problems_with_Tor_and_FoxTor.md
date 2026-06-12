---
title: "Problems with Tor and FoxTor"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-11-08
I have tor installed, along with privoxy, but I can't hide my IP address. I use FoxTor and the TorButton plugins to firefox to manage this and it doesn't change my IP. FoxTor reports me as being masked and unmasked, IP addresses are the same, and the Tor button doesn't report anything.

Anyone know how to fix this? Tor is running.

---

### Post by Biggus on 2007-11-09
I've never used foxtor, or tor buttons or anything else though.

I just make sure that my proxy settings are set to localhost, and port 8118 (9050 for socks)

---

### Post by malfist on 2007-11-09
Problem fixed, disable FoxTor, doesn't work. Uncomment the correct lines (described on privoxy's webpage) for port forwarding and now the TorButton works.

---

