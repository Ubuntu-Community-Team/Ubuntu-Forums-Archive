---
title: "BIND9 Subdomain"
date: 2024-01-01
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2024-01-01
Hi

I need to define an sub domain.
It should have the name "cl01" in the domain darkwing.net.

When I searched the net how to set it up, I found three ways:


gns.darkwing.net. A 192.168.101.100
$ORIGIN cl01.darkwing.net.
@      IN         NS        gns.darkwing.net.


$ORIGIN cl01.darkwing.net.
@IN NS gns.cl01.darkwing.net.
gns.darkwing.net. IN A 192.168.101.100


cl01-gns-vip    A  192.168.101.100
cl01.darkwing.net  NS   cl01-gns-vip.darkwing.net

None of these are accepted by ORACLE GNS which requests an Subdomain delegation.

Can anyone tell me, which way is the correct way to setup

Cheers and have a great 2024
Christian

---

### Post by SeijiSensei on 2024-01-02
I don't know anything about ORACLE, but usually you need to have a separate nameserver for the subdomain. Then you can have entries like

```

cl01     IN     NS   ip.of.dns.server

```

These refer requests for something.cl01.darkwing.net to ip.of.dns.server for resolution.

---

