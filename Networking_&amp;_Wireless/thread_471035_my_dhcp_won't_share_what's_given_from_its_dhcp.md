---
title: "my dhcp won't share what's given from its dhcp"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by azzid on 2007-06-11
Hi,

I just set up my new firewall. It gets ip and other network settings from the dhcp of my isp. It has a dhcp server running serving out adresses on its other nic. It works fine and all, but there's a little detail in the settings that bugs me.

The following line in /etc/dhcp3/dhcpd.conf

```
option domain-name-servers <ip of a dns server>;
```

I have manually set it to one of the dns-servers of my isp, but is there no way to automatically take it from the info given to the machine by my isp's dhcp?

All the info is readilly available in /etc/resolv.conf, should'nt my dhcp server be able to just forward that info?

---

### Post by kidders on 2007-06-12
Hi there,

Unfortunately, using /etc/resolv.conf that way would probably be unworkable. It just wouldn't be robust enough in practice, and might even have the potential to raise security issues. Normally however, the issue doesn't arise, because it is usual to run your own DNS service ... even if for no other reason than to handle local DNS resolution properly.

Anyhow, the simplest answer to your question that comes to mind is to rewrite /etc/dhcp3/dhcpd.conf every time you restart the DHCP service. Of course, that only half solves the problem, since /etc/resolv.conf could be rewitten at any time, and even if your DHCP server was aware of the change, there would be no way to propagate it until your clients renewed their leases. Essentially, DHCP is not designed to handle arbitrarily changing DNS information.

Given a set of DNS servers from /etc/resolv.conf, rewriting your DHCP server configuration would be a matter of something like **sed 's/\(option domain-name-servers\)[^;]*;/\1 WHATEVER;/' /etc/dhcp3/dhcpd.conf** ... but, to be honest, I wouldn't recommend going down that road because, as I mentioned...
[LIST]
[*]Your DHCP clients' DNS service could still break for short periods whenever your gateway to the internet renews its own DHCP lease.
[*]Even if it could be made to work properly, the solution would still be inferior to the standard way of handling DNS on a network.
[/LIST]

I hope that helps.

---

### Post by azzid on 2007-06-25
Hm, OK, thanks anyway!

---

### Post by kidders on 2007-06-25
No problem. :-)

My best suggestion would be to adopt the standard approach and run a local DNS server to compliment your DHCP service. That way, routinely rewriting named.conf's "forward" directives & restarting DNS could be the server's own DHCP client's job ... and your internal clients' DNS server address would always be the same.

---

