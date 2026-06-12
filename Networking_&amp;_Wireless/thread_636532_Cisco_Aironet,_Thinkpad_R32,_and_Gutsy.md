---
title: "Cisco Aironet, Thinkpad R32, and Gutsy"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by namenlos on 2007-12-09
Hi all. Starting with Feisty my cisco aironet 340 would not work properly in Thinkpad R32. The card would associate with an access point, but would not go any further. My WRT54G would recognize that the card was associated in the web interface.I tried for a few days to fix it and then finally gave up. Just yesterday I upgraded to Gutsy hoping that the problem had been solved. Upon rebooting the same problem presented itself again. Long story short, most of the users I found with this problem were working with Thinkpads, most of which have an infrared port. Removing the modules that support infrared fixed the problem. I did so by adding
```
blacklist nsc_ircc
blacklist irtty_sir
blacklist sir_dev
blacklist irda
```
to /etc/modprobe.d/blacklist .
Hopefully this helps some people out.

---

