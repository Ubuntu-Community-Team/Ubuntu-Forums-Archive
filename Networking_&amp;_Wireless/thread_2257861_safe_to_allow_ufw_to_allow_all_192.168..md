---
title: "safe to allow ufw to allow all 192.168."
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2014-12-23
On my local network, I have several devices that have dynamic IP addresses. These device need to be able to access a media server sitting behind ufw. Currently I have to change the allow list every time a devices moves. Would it be unsafe (or possible) to allow ufw to allow access from any device on the local network? I live in the sticks, so neighbors don't bother me. I just want to block traffic from the internet.

---

### Post by steeldriver on 2014-12-23
Remember that (unless you have explicitly forwarded ports on your router), NAT already provides one layer of blocking for incoming traffic from outside your LAN

Nevertheless, yes you can set an address range with UFW using CIDR 'slash' notation in the 'from' field e.g.

```

ufw allow from 192.168.1.0/24 to any port 5901

```

You probably don't need a class C mask (192.168.0.0/16) and I've never tried using one in ufw but I can't see any reason why it wouldn't work if you really need it.

---

### Post by rebeltaz on 2014-12-23
Cool. Thank you! That is going to make life so much easier!

---

