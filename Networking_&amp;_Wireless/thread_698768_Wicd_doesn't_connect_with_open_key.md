---
title: "Wicd doesn't connect with open key"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2008-02-16
I'm using the notorious bcm4318 card, running Gutsy 7.10. After a few fits and starts I got that working a while ago.

My problem is more of an annoyance/bug - when using either Wicd (preferred) or the GNOME network configuration interface, which is that they fail to connect to a network if the key (in my case, a WEP key) is "open" and not "restricted". I can try connecting to a network, but it won't connect until I type in the terminal or edit /etc/network/interfaces :```
sudo iwconfig eth1 key _open_ XXXXXX
```, at which point it works just fine. Neither a saved location in network configuration nor Wicd seem to be able to do this right off the bat - any help on how to?

---

