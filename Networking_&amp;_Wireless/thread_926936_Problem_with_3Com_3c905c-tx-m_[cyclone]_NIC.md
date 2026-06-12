---
title: "Problem with 3Com 3c905c-tx-m [cyclone] NIC"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by robal on 2008-09-22
Hi,

I'm not a linux expert, so forgive me...  (and I DID search :) )

I have an Ubuntu 8.04 server installation with onboard Realtek card (which works fine) and one additional PCI NIC.

When I put good old 3com Etherlink XL everything works fine.
When I try to change it to newer 3c905c-tx-m 'cyclone', I don't have the connection.

The only diag I know of and could do are:

- lspci:
    reports Ethernet Controller 3c905c-tx/tx-m cyclone rev74
- cat /eth/network/interfaces :
    show only 'eth1' which is my Realtek card
- ifconfig:
    only lo and eth1...

Can someone help me, where should I look for an error ?
The device is there... detected correctly, but no 'eth' interface shows up.

---

