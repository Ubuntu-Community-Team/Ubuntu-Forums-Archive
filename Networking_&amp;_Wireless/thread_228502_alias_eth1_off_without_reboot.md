---
title: "alias eth1 off without reboot?"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by tripleee on 2006-08-03
Because the SiS network card on my motherboard (ASUS K8S-MX) wasn't working, I have another network card which I'm perfectly happy with. However, now that I installed Dapper, the SiS card is at least recognized, and now I get lots of warnings about eth1 ("eth1: PHY reset until link up." several times a minute, plus DHCP notices every once in a while).

Is there a way to disable eth1 without rebooting? I'm not asking because I desperately need to avoid a reboot, it's just that I recall I have done it before and now I can't figure out for the world of me how it was done. "modprobe alias eth1 off" or insmod was what I thought would work, but no (regardless of whether I quote the alias stanza).

On a related note, would you recommend that I put this in its own file in e.g. /etc/modutils/eth1-disable.local or some such, or edit /etc/modules, or should I put this somewhere else entirely?

---

