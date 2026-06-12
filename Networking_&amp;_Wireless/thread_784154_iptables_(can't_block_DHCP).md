---
title: "iptables (can't block DHCP)"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by sprucio on 2008-05-06
I have a default policy on the INPUT chain DROP on my linux machine. Currently, there are no other rules in place.

If I ping or try to SSH into this box, I cannot do so but it appears that DHCP requests are still getting through the firewall.

Shouldn't the default policy DROP everything in this instance?

---

