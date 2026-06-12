---
title: "Start pcmcia wireless interface at initialization"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by dcordeiro on 2006-08-27
Hi,

I'm using Dapper with a D-Link DWL-G630 wireless pcmcia card.

I've configured WPA to the ath0 interface and it works like a charm.

But I'm unable to start the interface automatically at Ubuntu's initialization. The card is initialized by the pcmiciautils, but it's unable to bring the interface up.

Setting the "auto ath0" in /etc/network/interfaces is the right way to bring up the interface of a pcmcia card in initialization?


Thanks,
Daniel

---

