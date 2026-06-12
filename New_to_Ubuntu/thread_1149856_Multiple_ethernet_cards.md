---
title: "Multiple ethernet cards"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Celauran on 2009-05-05
I've got 5 ethernet devices on my machine -- one on-board Intel and a four-port Adaptec card -- but the ethx numbering isn't sequential. That is to say, on the four-port card, one port is eth0 and the one adjacent is eth2. Is there any way to specify/map which card should be which device? Ideally, I'd like to have the on-board as eth0 and the 4-port card as eth1 through eth4.

Google hasn't turned up anything yet, so if anyone has done this (or something similar) before, a nudge in the right direction would be appreciated. Thanks.

---

### Post by Celauran on 2009-05-06
Alright, got it sorted. Just needed to edit /etc/udev/rules.d/70-persistent-net.rules and rearrange things to my liking.

---

