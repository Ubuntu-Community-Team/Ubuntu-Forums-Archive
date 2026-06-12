---
title: "Unable to connect ISP"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-04-08
Hi all,

Ubuntu 12.04 64bit

Cable connection - (FTTH) Fibre Optic Network
ISP -> PC

/etc/network/interfaces```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
     address xxx.xxx.xxx.xxx
     nameserver xxx.xxx.xxx.xxx
     nameserver xxx.xxx.xxx.xxx
     netmask xxx.xxx.xxx.xxx
     broadcast xxx.xxx.xxx.xxx
     gateway xxx.xxx.xxx.xxx

```

Unable to connect ISP.  But can ping gateway.  Please help.  Thanks

Rgds
satimis

---

### Post by lukeiamyourfather on 2014-04-08
Turn it off and on again. If that doesn't work then call your ISP because that's why you pay them.

---

### Post by satimis on 2014-04-08
> **lukeiamyourfather said:**
> Turn it off and on again. If that doesn't work then call your ISP because that's why you pay them.
Hi,

Problem solved

/etc/network/interfaces```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
     address xxx.xxx.xxx.xxx
     dns-nameservers xxx.xxx.xxx.xxx  xxx.xxx.xxx.xxx
     netmask xxx.xxx.xxx.xxx
     broadcast xxx.xxx.xxx.xxx
     gateway xxx.xxx.xxx.xxx

```

Thanks

satimis

---

### Post by lukeiamyourfather on 2014-04-11
My bad, I thought you were trying to diagnose issue with ISP, not a configuration file. I'm glad you got it working!

---

