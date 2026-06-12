---
title: "DNS: Automatic DNS record"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-09-29
How do you configure DNS so that it automatically creates an entry for a machine that joins a network?

For example, my school is a Windoze network and we all log into our laptops with our school username and password which is similar to the machine name.  I understand that - there are probably DNS entries in the DNS server for each machine on campus; I got that.

What confuses me is I have a couple of machines that I brought in for my own personal use, unknown by the school, and I can access them via name resolution anywhere on campus.  A typical user's laptop is something like curtiss78.csntprod.morrisville.edu - the user's campus login name of curtiss78 and it's on the csntprod.morrisville.edu domain.  And of course I could type:
```

ping curtiss78

```

and it would auto-complete the rest of the name and return the ip address as well as showing a ping to the host.  How do I set that up in named or bind?

---

### Post by MaindotC on 2008-11-19
bump

---

