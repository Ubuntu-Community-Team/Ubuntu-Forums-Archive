---
title: "public IP help"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by dd1313 on 2007-10-11
Just answering a question for test.please help

what is the public IP that is picked up by a pc if it cannot contact the server or there is a conflict on the network. ( 169 range )

Thanks Guys

Dd

---

### Post by milosz.galazka on 2007-10-11
Generally you get ip address from 169.254.0.1 to 169.254.255.254 if your dhcp client failed to get ip address...

You will find answers for test [here]("http://en.wikipedia.org/wiki/IP_address")

---

### Post by HermanAB on 2007-10-11
It is the Microsoft zeroconf crap, which some idiot ported to Linux where it is equally useless.  Turn the avahi-daemon off to get rid of it.

---

