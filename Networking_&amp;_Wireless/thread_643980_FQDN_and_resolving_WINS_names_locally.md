---
title: "FQDN and resolving WINS names locally"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by ThatOtherGuy435 on 2007-12-18
I have one of my linux boxes (Inside of a virtual machine) that was orginially insalled with a domain 'somewhere.com'. I have installed SAMBA on it and enabled the WINS server, but instead of resolving hostnames locally, it tries to resolve with witht he FQDN; i.e. ping 'tgweb' tries to ping against 'tgweb.somewhere.com'.

I realize that I could specify tgweb.local every time, but the whole idea behind having the WINS server is that I can shorten the typing!

My other linux boxes have all previously been installed without the Domain filled in; I have not been able to find where to change this!

For practical purposes, this box doesn't need to have a fqdn, as there are no mail servers or anything running on it. I just need it to be able to resolve things locally first, then past the gateway.

Thanks!
-TOG

---

### Post by ThatOtherGuy435 on 2007-12-23
For those who may be later looking for a solution, I got it to work by installing winbind, and editing /etc/nsswitch.conf to include wins in it's lookups.

---

