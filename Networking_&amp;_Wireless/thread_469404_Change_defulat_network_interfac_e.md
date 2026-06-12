---
title: "Change defulat network interfac e"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by etechship on 2007-06-09
You know, when you first install the server edition of Ubuntu, you select a default interface. What if you want to change that?

---

### Post by thelinuxguy on 2007-06-10
> **etechship said:**
> You know, when you first install the server edition of Ubuntu, you select a default interface. What if you want to change that?

```

sudo route del default
sudo route add default netmask 255.255.255.0 eth1

```

---

