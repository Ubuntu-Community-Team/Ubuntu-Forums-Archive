---
title: "promiscuous mode - MSI gx600 (Realtek PCI-E Ethernet)"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by Krakos on 2008-10-08
Hi all!

I would like to ask you how to get my network card running in promiscuous mode. As I know it is Realtek PCI-E Ethernet. On MSI GX600PX.
If somebody have it done, maybe can help me.

Thanks a lot

---

### Post by Chris_82 on 2010-12-22
With ifconfig.
The manual says:

[I][-]promisc
Enable or disable the promiscuous mode  of  the  interface.
If selected, all packets on the network will be received by the interface.[/I]

So the command is if your interface name is eth0.

```
ifconfig eth0 promisc
```
You have to do this having the appropriate privileges i.e. probably sudo.

To find out about your interface type ifconfig without arguments:
```
ifconfig
```

ps: yes this post is very old but I wanted to complete it in case somebody else stumbles upon it.

cheers.

---

