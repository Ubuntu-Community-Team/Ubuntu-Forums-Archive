---
title: "Network device sharing"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by jokr004 on 2006-09-24
What is the easiest way to share network connections in ubuntu?  I have tried firestarter which was unsuccessful.

---

### Post by talrasha on 2006-09-24
Firestarter??? I think Firestarter is for firewalls.

And if you want to share network resources try using SAMBA.

---

### Post by jokr004 on 2006-09-24
> **talrasha said:**
> Firestarter??? I think Firestarter is for firewalls.

And if you want to share network resources try using SAMBA.

Firestarter can share connections too, and I wants talking about SAMBA shares.
Actually sharing the connections, like a router.

---

### Post by spd106 on 2006-09-24
As far as I know firestarter is just a config tool for the kernel's built-in routing software (iptables). So if it doesn't work then you probably have deeper problems.

That said, you could also try a proxy server like Squid. It takes more setting up, but it is more advanced. There's also a package called ipmasq but I've not used it yet.

If you really want to learn to be a linux network pro then you should look into adding iptables rules directly.

---

