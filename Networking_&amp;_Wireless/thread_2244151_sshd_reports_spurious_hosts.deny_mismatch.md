---
title: "sshd reports spurious hosts.deny mismatch"
date: 2014-09-14
forum: Networking &amp; Wireless
---

### Post by jwbrase on 2014-09-14
I have a laptop and a desktop/server on a home LAN behind an AT&T U-verse router/modem.

My hosts.deny file on the desktop is set up to allow the laptop to connect to the desktop:

```
sshd: ALL EXCEPT [other whitelisted hostnames] laptop-hostname
```

When I attempt to connect to the desktop from the laptop, I get the following in auth.log:

```
sshd[30720]: warning: /etc/hosts.deny, line 18: host name/name mismatch: laptop-hostname != laptop-hostname.attlocal.net
sshd[30720]: refused connect from [laptops local IP address]
```

I tried adding laptop-hostname.attlocal.net to the ALL EXCEPT directive in hosts.deny, but get the same error in auth.log.

The laptop can login via ssh without issue if I ssh to my public IP address (the router port-forwards ssh to the desktop).

Any idea as to how to get sshd to behave?

---

### Post by Lars Noodén on 2014-09-15
From the error message it looks like a problem in how /etc/hosts.deny or /etc/hosts.allow is configured.  Try using the other name, either laptop-hostname or laptop-hostname.attlocal.net and see if [hosts.deny](http://manpages.ubuntu.com/manpages/trusty/en/man5/hosts_access.5.html) then allows you in.

---

### Post by jwbrase on 2014-09-15
hosts.allow is empty, hosts.deny whitelists hosts for sshd with an ALL EXCEPT directive. Both the bare hostname and the *.attlocal.net hostname are whitelisted in hosts.deny.

---

### Post by Lars Noodén on 2014-09-15
I haven't used hosts_access in ages, but it may be that it only recognizes actual real DNS data when resolving hostnames.

---

