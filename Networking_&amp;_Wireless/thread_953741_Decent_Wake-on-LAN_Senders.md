---
title: "Decent Wake-on-LAN Senders"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by pteri498 on 2008-10-20
Hi. I've been all over the internet and I can't find a wake-on-LAN magic packet sender that does what I need it to.

The host computer will wake up from a full power-off with WOL for Windows from within the network. However, I would like the same ability from outside the network.

I would like to know if you guys know any good WoL senders. Preferably something that I can compile myself, as the other computer (at my school) is a Fedora Core 9 system with no root access.

Thank you!

---

### Post by fwre01 on 2008-10-20
would an online WOL system do? like this [http://wakeonlan.me/](http://wakeonlan.me/)

I searched on wikipedia and found a couple of WOL programs that had the source availible, perhaps that would do it? i think the wikipedia article also gives information on the nat rules you need.

---

### Post by PinkFloyd102489 on 2008-10-20
Ubuntu has "wakeonlan" and "etherwake". There's also a program called "shutdown-at-night" that shuts the remote machine down at night and wakes it up in the morning.

Source for these would be easy to find.

---

