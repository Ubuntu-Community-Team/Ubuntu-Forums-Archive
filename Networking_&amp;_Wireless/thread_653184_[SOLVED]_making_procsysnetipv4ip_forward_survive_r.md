---
title: "[SOLVED] making /proc/sys/net/ipv4/ip_forward survive reboot in Gutsy"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by alina.bolero on 2007-12-29
I've just reinstalled my former FC5 firewall box with Gutsy.  What is the accepted way to make the "1" entry in /proc/sys/net/ipv4/ip_forward survive a reboot?

I tried to set it in /etc/sysctl.conf
```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

```

but that did not seem to help.

-Alina

---

### Post by alina.bolero on 2007-12-29
broke down and decided to RTFM  (i.e. man ifup & man interfaces)

found that sticking this at the end of the eth0 section of my /etc/network/interfaces did the trick:
```

post-up echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

### Post by david3d on 2008-02-04
Here's another solution.

As you've come to find out in Gusty uncommenting the default ip_forwarding line in /etc/sysctl.conf doesn't work properly.  After a reboot /proc/sys/ipv4/ip_forward will still be 0.

I believe the problem is the line in sysctl.conf.
```

# Default line in sysctl that doesn't work
# net.ipv4.conf.default.forwarding=1

# Corrected line that works
net.ipv4.ip_forward=1

```
--
David

---

