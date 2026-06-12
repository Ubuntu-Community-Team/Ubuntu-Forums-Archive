---
title: "How to set dhcp_keepresolv = yes"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by z3d0 on 2006-10-22
With slackware I added

```
DHCP_KEEPRESOLV[0]="yes"
```

in my /etc/rc.d/rc.inet1.conf and I must do the same with ubuntu. I know that I have to edit /etc/network/interfaces but I don't know exactly what I have to write. (man interfaces didn't help me)
I need this because otherwise at each reboot the data in the /etc/resolv.conf file are changed with the default...

---

### Post by z3d0 on 2006-10-23
any suggestion?

---

### Post by Iowan on 2006-10-24
> **z3d0 said:**
> With slackware I added

```
DHCP_KEEPRESOLV[0]="yes"
```

in my /etc/rc.d/rc.inet1.conf and I must do the same with ubuntu. I know that I have to edit /etc/network/interfaces but I don't know exactly what I have to write. (man interfaces didn't help me)
I need this because otherwise at each reboot the data in the /etc/resolv.conf file are changed with the default...
I'm not familiar with that option, but it *looks* like something (or similar to something) that might go in the **/etc/dhcp3/dhclient.conf **file.
You might try **man dhclient.conf** for more info.

---

