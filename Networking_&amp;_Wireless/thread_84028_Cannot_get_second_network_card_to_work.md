---
title: "Cannot get second network card to work"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by g-joey on 2005-10-30
Hi,

I am running a (samba) server which is connected via a WLAN card to my router. Some Linux and Windows clients connect to this server, and all is working fine :-)

Now I decided to connect this machine to another server via the on-board LAN chipset. The chipset is supported, it gets an IP address and comes up without errors.

But as long as this card is active, I cannot establish any connections, neither via WLAN nor via LAN. I'm sure I missind something in the configuration, but what?

//Joe

---

### Post by spd106 on 2005-10-31
We need a bit more information about the setup.
Can you ping any of the other hosts?

How have you set up the ip addresses? Do they all connect to the wifi routers dns server?

Are they all on the same subnet or do you need to bridge the networks? Do use firestarter?

You may need to change the /etc/hosts or /etc/resolv.conf files, to make sure use the correct default gateway and so they can discover the network hosts.

---

### Post by mips on 2005-10-31
If both devices are in the same IP subnet then it wont work.

---

