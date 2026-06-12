---
title: "IPv6, interfaces and resolv.conf"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by dmrazor on 2013-12-02
I'm running ubuntu server 12.04.3 LTS and have recently activited IPv6. The name resolution for IPv6 is driving me bonkers. From what I read here: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution") this information should be read from /etc/network/interfaces which looks like this:

```
# The primary network interface
# IPv4 config
auto eth0
iface eth0 inet static
        address 192.168.10.12
        netmask 255.255.255.0
        gateway 192.168.10.1
        dns-nameservers 192.168.10.12 194.109.6.66 194.109.9.99

# IPv6 config (gateway derived from Fritzbox)
iface eth0 inet6 static
        pre-up modprobe ipv6
        address 2001:xxx:yyy:1::12
        netmask 64
        gateway 2001:xxx:yyy:1::1
        dns-nameservers 2001:xxx:yyy:1::12 2001:888:0:6::66 2001:888:0:9::99
```

No matter what I try, the only info that is being read from the interfaces file and put in /etc/resolv.conf is the IPv4 dns-servers. Found some messages pointing to a possible bug here. Is that the case and if so, what's a good workaround. If not... am I being really stupid and overlooking something obvious?

Thanks for any help,
Raz

---

### Post by sanderj on 2013-12-02
You do not need a DNS server with an IPv6 address to do AAAA resolving; you can do that over IPv4. Proof:

```
$ host ipv6.google.com 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

ipv6.google.com is an alias for ipv6.l.google.com.
ipv6.l.google.com has IPv6 address 2a00:1450:4013:c01::69
sander@flappie:~$
```

---

### Post by dmrazor on 2013-12-04
Ok. Still doesn't explain why resolvconf isn't doing what it says it does, but good enough for now. Thanks.

---

