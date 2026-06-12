---
title: "Bonding 4 ethernet cards and procurve 1800"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by pixelinmotion on 2008-05-07
Hello all,

I´m trying to bond 4 1Gb ethernet cards (intel 82572EI), I have an  integrated ethernet card too from the motherboard.

I´ve gone throught some tutorials, and I have managed to have a bond0 with the 4 1Gb cards with an ip which I can ping, the problem is that once I disconect the cable from the eth0 (motherboard) I can no longer ping bond0.

So I´m going always trought the ethernet port on the motherboard.

My switch is an HP Procurve 1800 which supports dynamic bonding and fixed trunks.

I´m on Ubuntu Desktop 7.10

Any ideas?

Thanks

It worked, I just missed commenting the primary adapter line.

---

