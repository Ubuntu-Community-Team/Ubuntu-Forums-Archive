---
title: "pcmcia 802.11b autodetect system"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by Coops on 2005-07-06
Hi Guys,

Ok I've just upgraded my wlan card - got it working using the rt2500 drivers fine, but I'm now getting confused by how exactly ubuntu auotdetects the network card on boot, and sets up the network. The automatic process doesn't load the iwconfig settings I give it, e.g. mode/essidkey - so I do it my hand once the machine is booted.

So what are the stages ubuntu goes through when loading a found pcmcia 802.11 card? And then I may be able to trackdown the problem.

Thanks,

-Coops

For you info;

Linksys WMP54G PCMCIA card
RT2500 Drivers
Devices loads as ra0 --- (also how can you change this?)
On boot it finds the card + loads the driver + starts a DHCP search, but doesn't use the settings I give it, so doesn't find the network.

```
# cat /etc/network/interfaces
auto lo
iface lo inet loopback

mapping hotplug
script grep
map ra0

iface ra0 inet dhcp
wireless-mode managed
wireless-essid my-networks-essid
wireless-key s:my-key
wireless-nick my-nick
auto ra0

```

---

