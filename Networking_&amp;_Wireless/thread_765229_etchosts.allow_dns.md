---
title: "/etc/hosts.allow dns"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by skunkwerk on 2008-04-24
I added an entry to my hosts.allow file

ALL: %.domain.com

problem is, when I try to connect from subdomain.domain.com it says 'ip address not allowed to connect to this machine'
i.e. ubuntu doesn't seem to be doing the reverse IP address to domain name lookup to see if it matches domain.com

any suggestions?

thanks

---

### Post by Iowan on 2008-04-24
From the **man** page:>   /etc/hosts.deny:
          ALL: some.host.name, .some.domain
          ALL EXCEPT in.fingerd: other.host.name, [COLOR="Red"].other.domain[/COLOR]
OK, so this was from **hosts.deny** instead of **hosts.allow** - the key item is that the local network uses just a dot prefix.

Having never used either **hosts** file, I cannot honestly say what the % expansions do...

---

### Post by skunkwerk on 2008-04-24
sorry, the original post should have been:

.domain.com
not %.domain.com

the man page says:
the pattern '.tue.nl´ matches the host name 'wzv.win.tue.nl´

which is all well and good...
my problem is my machine does not seem to be doing a dns lookup for the ip address that tries to connect, so it never matches that listing in etc/hosts.allow

thanks

---

