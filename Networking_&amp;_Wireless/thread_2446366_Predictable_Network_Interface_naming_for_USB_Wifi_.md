---
title: "Predictable Network Interface naming for USB Wifi Network Interfaces?"
date: 2020-06-29
forum: Networking &amp; Wireless
---

### Post by durexlw on 2020-06-29
OS: Ubuntu server 20.04

I have two USB Wifi network cards, one internal interface. Long story short: sometimes the internal card is called wlan0, other times wlan1, ... when I add or remove cards, the naming becomes completely unpredictable.

I have read documentations saying that there is something like a 'predictable naming' convention. What confuses me is that whenever I read the documentation (see: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)), it says it should be disabled and therefore in place by default, but it doesn't seem to be. If I look in '[COLOR=#2E1A05][FONT=monospace]/etc/systemd/network/', I don't see any rules defined either. [/FONT][/COLOR]Needless to say I'm confused.

**What I would like to become is that all NIC's always have the same name, regardless if one is unplugged or not. The names can be based on MAC or usb-portnumber. Either way, if I plug in a card, I'd like it to have the same name each time, preferably on MAC address.**

P.S. I realize with NetworkManager I can assign profiles/connection based on mac address, however I want to use networkd for managing my connections;
P.S2. When it comes to netplan: the documentation says that can filter based on MAC address or driver, but for networkd, it says I can only match on names... which kinda defies the whole purpose.

I'd really appreciate if someone could shed some light on this.

---

