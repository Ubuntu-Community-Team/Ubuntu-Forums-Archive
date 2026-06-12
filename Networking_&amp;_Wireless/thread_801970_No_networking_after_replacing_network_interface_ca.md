---
title: "No networking after replacing network interface card (NIC) ubuntu 8.04"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by ispyisail on 2008-05-21
Hi All

I've just upgraded to ubuntu server 8.04 LTS and all was well untill i decided to upgarde my NIC.

After replacing my network card there was no networking anymore.

I put the old card back in and the network worked again.

After much research i found the solution:

[https://bugs.launchpad.net/ubuntu/+bug/214789](https://bugs.launchpad.net/ubuntu/+bug/214789)

> There is /etc/udev/rules.d/70-persistent-net.rules which lists the old MAC as eth0 and prevents the new card from becoming eth0.

There is /etc/network interfaces that lists all the eth intefaces generated so far (up to eth1) as "iface ethx inet dhcp".

Basically when ubuntu is installed it creates a link between the NIC MAC address and eth(x) and when a new NIC is installed the MAC address is associated with the next free eth(x) so eth0 (first card) now becomes eth1 (new card)

If you want the new card to become eth0 you need to edit /etc/udev/rules.d/70-persistent-net.rules Delete all the old rules then reboot.

Hopefully this post will save somebody some time.

More insite on this issue would be apperciated

Thanks

---

