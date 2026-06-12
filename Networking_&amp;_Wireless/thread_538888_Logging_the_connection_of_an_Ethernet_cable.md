---
title: "Logging the connection of an Ethernet cable?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Catsworth on 2007-08-30
Is there anywhere that I can view a log of the Ethernet adaptor on my laptop to see if it registers the connection of an Ethernet cable?

Thanks :)

---

### Post by noob12 on 2007-08-30
You should normally see the link reported as up/down in the kernel log (dmesg or /var/log/kern.log) when you connect/disconnect the cable.

For example
```

tail -10f /var/log/kern.log

```

Then unplug, replug the cable.

If you want to check the state, you probably just want to use **ethtool**.  For example (for an interface named eth0),
```

sudo ethtool eth0

```

---

