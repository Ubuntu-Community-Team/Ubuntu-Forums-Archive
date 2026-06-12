---
title: "Will not assign IPV4 address"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by dav7612r on 2007-10-11
Under eth0 it is only showing an IPV6 address.
I checked the interface file and it's set to give an IPV4 address.

How do i get an IPV4 address with DHCP?

I can't connect to anything with IPV6.

---

### Post by Lambert on 2007-10-12
> **dav7612r said:**
> Under eth0 it is only showing an IPV6 address.
I checked the interface file and it's set to give an IPV4 address.

How do i get an IPV4 address with DHCP?

I can't connect to anything with IPV6.

When the interface is brought up, it automatically runs dhcp scripts.

To manually run dhcp you run the following command from a terminal.

```

sudo dhclient eth0

```

Your pc then sends out dhcpdiscover packets to your network connections.

what is eth0 wire or wireless connection?

---

