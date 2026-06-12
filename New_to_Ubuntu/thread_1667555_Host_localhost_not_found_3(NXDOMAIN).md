---
title: "Host localhost not found: 3(NXDOMAIN)"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by mattismyname on 2011-01-15
My system's DNS resolver is somehow unable to find the localhost entry I have in /etc/hosts.  I am not sure what the problem might be.

In /etc/hosts:
127.0.0.1	localhost

In /etc/nsswitch.conf:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

In /etc/host.conf:
order hosts,bind

When I do an strace on "host localhost" command, it appears to go straight to DNS.  It never opens /etc/hosts, /etc/nsswitch.conf, or /etc/host.conf.  I'm stumped!

---

### Post by mattismyname on 2011-01-15
Ok, this was a stupid question.  Apparently the 'host' command only uses DNS...it does not use nsswitch to search multiple services.

localhost resolves just fine by any program not hardcoded to use DNS.

---

