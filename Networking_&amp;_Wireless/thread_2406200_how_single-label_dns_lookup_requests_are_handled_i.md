---
title: "how single-label dns lookup requests are handled in systemd-resolved?"
date: 2018-11-17
forum: Networking &amp; Wireless
---

### Post by solaroi on 2018-11-17
I looked into the systemd-networkd and systemd-resolved:
[http://manpages.ubuntu.com/manpages/bionic/man5/systemd.network.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/systemd.network.5.html)
[http://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html)
and are confused by some words here: 
systemd-resolved: 
Single-label names are routed to all local interfaces capable of IP multicasting, using the LLMNR protocol.
Lookups for a hostname ending in one of the per-interface domains are exclusively routed to the matching interfaces.

systemd-networkd: domain
Both "search" and "routing-only" domains are used for routing of DNS queries: look-ups for host names ending in those domains 
(hence also single label names, if any "search domains" are listed), are routed to the DNS servers configured for this interface.

my question is: for hosts with a bunch of interfaces configured with "search domains" and LLMNR enabled, where will the single-label lookup requests go?

---

### Post by SeijiSensei on 2018-11-17
What's a "single-label" name?  Do you mean an "unqualified" name like "mycomputer" rather than a "fully-qualified" name like "mycomputer.example.com"?  You can handle unqualified names by adding entries to /etc/hosts.

If you have a search domain in /etc/resolv.conf, it will use the nameserver defined there:

```

search example.com
nameserver 10.10.10.10

```

That applies to all interfaces on the machine.

---

