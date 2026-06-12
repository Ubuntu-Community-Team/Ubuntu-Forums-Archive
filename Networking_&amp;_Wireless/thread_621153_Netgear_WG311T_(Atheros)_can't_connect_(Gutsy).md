---
title: "Netgear WG311T (Atheros) can't connect (Gutsy)"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Simoo on 2007-11-23
To go with a fresh install of Ubuntu Gutsy I bought a Netgear WG311T card from [http://efficientpc.co.uk](http://efficientpc.co.uk) as they assured me they put them in all their builds with great success (WPA etc.)

However I can not get it to work! The network manager in the top right finds both networks in the area, with differing strengths, so I am sure the card is set up on a hardware level, but won't connect to either. One is WPA encrypted the other is unsecured.

When ever a connection, to either, is attempted the little dots never flash green and the blue circle keeps rotating until it fails. 

All is well if I plug in an Ethernet cable from the same router.

Incidentally, I can connect to both networks with my Apple and with XP duel booting from the machine in question.

I have tried manually editing the '/etc/network/interfaces' file and using 'sudo ifup ath0' but it never obtains an ip address. My /etc/resolv.conf' has the correct routers ip address.

If anyone can help it would be great as I am completely stuck!

Thanks

Simon

P.S. Oh yeah, the only other thing I did was get all the recent updates (via Ethernet) and install 'madwifi-tools' although I didn't know what to with them... or where they are!

---

