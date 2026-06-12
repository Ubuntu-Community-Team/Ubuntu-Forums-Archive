---
title: "Help with wireless PCMCIA card please"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by zaphodz on 2008-08-24
Background:
I have an old Netgear FM114P router. The wireless connection was flaky so I thought I'd pull it apart and see if the antenna wire was loose. Interestingly I found it contained a PCMCIA card.

[[IMG]http://img300.imageshack.us/img300/8942/pcmciadetailszy2.th.jpg[/IMG]](http://img300.imageshack.us/my.php?image=pcmciadetailszy2.jpg)[[IMG]http://img291.imageshack.us/img291/2959/pcmciatopsx8.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=pcmciatopsx8.jpg)

The card seems to be a Z Com PRISM 2.5 card XI-325 M4Y-000325

Info on the card here:
[http://freepages.misc.rootsweb.ancestry.com/~wb4kdi/PC/pcmcia/PRISM/models.html](http://freepages.misc.rootsweb.ancestry.com/~wb4kdi/PC/pcmcia/PRISM/models.html)
[http://www.netstumbler.org/f9/xi-325-help-13508/](http://www.netstumbler.org/f9/xi-325-help-13508/)

I have an IBM X20 laptop running Xubuntu 8.04.1 that I would like to use the card in.

[[IMG]http://img409.imageshack.us/img409/7879/x20bu1.th.jpg[/IMG]](http://img409.imageshack.us/my.php?image=x20bu1.jpg)

When I plug the card in, the lights turn on.

[[IMG]http://img403.imageshack.us/img403/8561/pcmcialightsno7.th.jpg[/IMG]](http://img403.imageshack.us/my.php?image=pcmcialightsno7.jpg)

No wireless connection becomes available though.

I've been following the wireless guide here to get it going:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

sudo pccardctl ident =

```
x20@x20-laptop:~$ sudo pccardctl ident
Socket 0:
  product info: " ", "IEEE 802.11 Wireless LAN/PC Card", "", ""
  manfid: 0xd601, 0x0005
  function: 6 (network)
Socket 1:
  no product info available
```

sudo lshw -C network =

```
x20@x20-laptop:~$ sudo lshw -C network
  *-network               
       description: IEEE 802.11 Wireless LAN/PC Card
       physical id: 0
       slot: Socket 0
  *-network
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 20
       serial:
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.4 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
```


I thought it wasn't loading a driver. I found this page: [http://linux-wless.passys.nl/query_part.php?brandname=Z-Com](http://linux-wless.passys.nl/query_part.php?brandname=Z-Com)

and installed hostapd via the synaptic repository.

I blacklisted the orinoco drivers and rebooted. Still no wireless.

Does anyone have any suggestions as to how to get this wifi PCMCIA card working?

Any help would be greatly appreciated :)

---

