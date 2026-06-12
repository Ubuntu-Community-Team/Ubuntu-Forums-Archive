---
title: "wlan-ng setup for Microsoft wireless card"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by Mike Buksas on 2005-05-03
Hi all. I've installed wlan-ng via synaptic and am trying to use a Microsoft PCMCIA wireless adapter MN-520 (hey, they make decent hardware  ;-) )

The installation went fine, the card is supported. It appears in  /etc/pcmcia/wlan-ng.conf. The right info appears when I do cardctrl ident. Everything looks *great.*

But I don't get a wlan0 interface. Nothing appears in network-admin (eth0 and the modem are there) Trying to ifup wlan0 is unhelpful:
  [FONT=Courier New]Ignoring unknown interface wlan0=wlan0.[/FONT]
And adding wlan0 by hand to /etc/network/interfaces doesn't work either.

Also, my wireless acces point has security off (temporary!) and I get two beeps when I plug the card in.  I also had the card working under Fedora Core 1, so I know the hardware is okay.

What else do I need to do to configure wlan-ng?

Thanks!

---

