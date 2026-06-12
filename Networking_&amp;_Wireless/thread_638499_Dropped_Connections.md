---
title: "Dropped Connections"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Raptor45 on 2007-12-12
I have a Lenovo T61 with the Intel AGN wireless card.

Everything connects fine. However the connection drops sometimes, frequently when using update manager. Simply doing apt-get update will cause it most of the time. This is always coupled with the following message in kern.log, syslog, and debug :

```
wlan0: CTS protection disabled 
```

After this I am unable to reconnect for a long time without restarting. If I kill apt-get quickly enough the connection comes back in a minute or so, and logs report CTS protection enabled.

Any help?

EDIT: The connection doesn't really drop, network-manager still shows full bars, just no traffic is sent.

---

### Post by Raptor45 on 2007-12-14
Any ideas from anyone?

---

