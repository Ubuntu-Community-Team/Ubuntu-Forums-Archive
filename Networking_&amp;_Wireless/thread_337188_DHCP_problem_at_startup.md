---
title: "DHCP problem at startup"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by theoldwiseking on 2007-01-12
I connect to internet via DSL connection. ny ethernet card is detected correctly, and it receives configuration from the router by DHCP. I installed ubuntu, but it each time I start the OS, it doesn't receive configuration, so I cannot connect to internet, I have to run sudo dhclient to receive the configuration, and then connect to internet.

---

### Post by Iowan on 2007-01-12
Post your **/etc/network/interfaces** file - or at least verify that there's a line similar to
```
auto eth0
```

---

