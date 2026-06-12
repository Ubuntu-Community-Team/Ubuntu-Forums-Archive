---
title: "dhcp domain definition"
date: 2023-11-29
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2023-11-29
Hi
after some trouble I've got my DDNS system running.
BIND9 and isc-dhcp-server.

This should be the base for ORACLE DNS.

Now to the problem.
I have to define a subdomain, for example cluster.darkwing.net.
The problem is, that ORACLE will send dhcp requests to this subdomain like this.
NODE1-VIP.RACA.cluster.darkwing.net
NODE2-VIP.RACA.cluster.darkwing.net
....
Of course, I could define the domain in dhcp RACA.cluster.darkwing.net.

However, if I setup another cluster the requests would be:
NODE1-VIP.RAC**B**.cluster.darkwing.net
NODE2-VIP.RAC**B**.cluster.darkwing.net
And this will fail, as RACB.cluster.darkwing.net is not defined.
The only solution I have in mind is to define different subnets for each domain.
Is there any other solution to get around this?

Thanks alot

Christian

---

