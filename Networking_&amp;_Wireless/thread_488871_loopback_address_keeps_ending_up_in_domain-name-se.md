---
title: "loopback address keeps ending up in domain-name-servers in dhcpd.conf"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by CGAllred on 2007-06-30
I have a Ubuntu 7.04 box that I recently set up to provide DHCP, DNS and NAT to my local network.  It replaced an older Fedora Core 3 box that had been doing the same job for several years.  In my dhcpd.conf file is this line:

```
option domain-name-servers 192.168.0.1, 68.238.128.12, 68.238.64.12;
```

Or at least, that's what the line is supposed to read.  What's happening is that every few days, 192.168.0.1 gets replaced by 127.0.0.1, which of course hoses name resolution on my home network, as each machine thinks it is supposed to consult itself for a DNS lookup.

The mangling of my dhcpd.conf file seems to correspond to a restart of dhcpd.  When I restart it manually though, the configuration remains unmolested.  Something else is changing the file and restarting the DHCP server.  I tried chmod'ing /etc/dhcp/dhcpd.conf 444, but something (clearly running as root) overwrote it anyway, and chmod'ed it back to 644 in the process.

I'm not new to Linux, but am new to Ubuntu, so I could be missing something in the Ubuntu environment.

Can anybody tell me what's going on here?

---

