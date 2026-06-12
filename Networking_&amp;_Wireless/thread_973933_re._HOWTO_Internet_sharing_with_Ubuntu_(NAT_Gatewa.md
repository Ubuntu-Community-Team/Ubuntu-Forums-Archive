---
title: "re. HOWTO: Internet sharing with Ubuntu (NAT Gateway)"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by gardengxc on 2008-11-07
in this post it tells me to alter my sysctl.conf file.
but when I look I doesn't have the lines...

#net.ipv4.conf.default.forwarding=1
#net.ipv4.conf.all.forwarding=1

---

### Post by kerpow on 2008-11-07
Does it have this section:

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1

If so I would uncomment them instead.

(FYI: If this is to share an Internet connection you are much better of getting a modem with a built in router if you can, it offers better security.)

---

### Post by gardengxc on 2008-11-07
> **kerpow said:**
> 
(FYI: If this is to share an Internet connection you are much better of getting a modem with a built in router if you can, it offers better security.)
its temporary.
don't want to invest good money for something I'll use once.

---

