---
title: "ipv6 only in 15.05"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by pbrille on 2015-04-27
Hi,

I'm trying to use ubuntu 15.05 in an IPv6 only environment ( yes, there are already IPv6 only environments).

When I setup /etc/network/interfaces like this all is fine: (I installed a dhcpv4 server temporarily :-))

```
auto eth0
iface eth0 inet dhcp
iface eth0 inet6 dhcp
iface eth0 inet6 auto

```

When I set:
```
auto eth0
iface eth0 inet manual
iface eth0 inet6 dhcp
iface eth0 inet6 auto

```

also tried:
```
auto eth0
iface eth0 inet6 dhcp

```

I won't get a stateful or stateless  IPv6 address nor an IPv6 default gateway.
Syslog tells me something like:
> networking[801]: /sbin/dhclient-script: 55: /sbin/dhclient-script: shopt: not found
networking[801]: /sbin/dhclient-script: 55: /sbin/dhclient-script: [[: not found
networking[801]: /sbin/dhclient-script: 55: /sbin/dhclient-script: shopt not found

---

### Post by pbrille on 2015-05-03
I really did not expect too much feedback to that kind of problem, but can't anybody reproduce this?

---

### Post by PaulW2U on 2015-05-03
> **pbrille said:**
> I really did not expect too much feedback to that kind of problem, but can't anybody reproduce this?

May be there was some confusion over the use of "15.05". Did you mean to use "Ubuntu 15.04" in the thread title?

Perhaps you should alert a moderator to change the title of the thread if you can't do this yourself.

---

### Post by pbrille on 2015-05-12
I think the more important thing is that IPv6 network is xxxxxx up in 15.0(!>4<!)

---

