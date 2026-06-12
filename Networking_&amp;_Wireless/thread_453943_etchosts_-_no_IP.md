---
title: "/etc/hosts - no IP"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by vjeko on 2007-05-24
Hello,

I was wondering if anybody knows how to omit host's IP address from /etc/hosts file, and instead use its domain name, such that when I make a request:

ssh user@host-alias

is automatically translated to:

ssh [email]user@host.domain.supe[/email]rdomain

... without me giving away its IP address. Also, i do not know if this is possible... but I would like to be able to omit IP address only in some cases. Apparently this could be achieved by modifying /etc/hosts.conf file, however this file is poorly documented. Any help would be appreciated!

~vi

---

### Post by gustavoberman on 2007-05-25
in /etc/hosts you can have:

ip address - fqdn - aliases

so you can do:

ip address   host.domain.superdomain  host-alias

---

### Post by vjeko on 2007-05-25
Hmh... but the problem is that the IP address is constantly changing...
Once again... I am wondering if it is possible to omit the IP address, and instead use *just* its domain name.

---

### Post by jonallport on 2007-05-25
Just to clarify,

You want to put an alias into the hosts file which resolves to a FQDN which is then looked up in DNS?

Sound like you ned to move up the chain and put the alias into the DNS domain.

If you don't have access to the DNS server then all I can suggest is to run a local caching DNS server and manipulate the forward lookup tables to include your alias then refer to you local DNS for lookups.

Hope that helps

---

### Post by vjeko on 2007-05-25
Thank you. :) I'll check that out.

---

