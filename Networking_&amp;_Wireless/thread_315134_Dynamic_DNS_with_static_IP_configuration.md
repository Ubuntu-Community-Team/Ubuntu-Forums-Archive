---
title: "Dynamic DNS with static IP configuration"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by nsvora on 2006-12-08
Hi All,
I have a Linux machine having static IP configuration ( without DHCP). And if this configuration is changed, should this information be updated in the DNS server?

In short, does Dynamic DNS make sense with static IP configuration?

Any comment in this regard is highly appreciated.

With Regards,
nsv

---

### Post by PilotJLR on 2006-12-08
DDNS doesn't update itself... you can either update it manually, or install a daemon like inadyn, which will check your IP every minute and automatically update if it changes.

And to clarify, the static IP you are referring to is your public IP address, right? In other words, it does NOT start with a 192.168.x.y (or 10.x.y.z or 172.[16-31].x.y)??

---

### Post by az on 2006-12-08
> **nsvora said:**
> Hi All,
I have a Linux machine having static IP configuration ( without DHCP). And if this configuration is changed, should this information be updated in the DNS server?

In short, does Dynamic DNS make sense with static IP configuration?

Any comment in this regard is highly appreciated.

With Regards,
nsv

The Dynamic DNS providers I know of will kick you off if your IP address does not change every so often (30 days, I think)

---

