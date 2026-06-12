---
title: "Wireless Again"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by tdell on 2006-08-21
OK. I have found ut my wireless card IS supported. I downloaded linux-wlan-ng-0.2.3 ran it and followed the setup instructions. I then have a wireless connection, however I lose it on a re-boot and have to go through the configuration process again to get a wireless connect????

Any ideas how how to get it to start on booting?

---

### Post by lupine_nickt on 2006-08-21
Place your configuration details into /etc/network/interfaces (edit it as root)

Something like this:-
```

auto <ethname>
iface <ethname> inet dhcp 
    wireless-essid bobsyouruncle

```

is generally enough to get it working; although you may need to add wireless-key (for WEP), etc. to get it running to taste. 

Google will give you plenty of sample configs.

xF,

...Nick

---

### Post by tdell on 2006-08-21
> **lupine_nickt said:**
> Place your configuration details into /etc/network/interfaces (edit it as root)

Something like this:-
```

auto <ethname>
iface <ethname> inet dhcp 
    wireless-essid bobsyouruncle

```

is generally enough to get it working; although you may need to add wireless-key (for WEP), etc. to get it running to taste. 

Google will give you plenty of sample configs.

xF,

...Nick
It is already there, but still does not start

---

### Post by tdell on 2006-08-27
OK I have given up and gone back to SUSE, while it has a coulpe of problems it configured my wireless and printer out of the box!

---

