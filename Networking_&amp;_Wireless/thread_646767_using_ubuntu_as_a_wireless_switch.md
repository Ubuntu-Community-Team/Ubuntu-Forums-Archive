---
title: "using ubuntu as a wireless switch"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by glok_twen on 2007-12-21
hi. i have an ubuntu box with 2 nic's, one wireless and one wired. i have the wireless nic successfully linked to the wireless lan and can browse. i have the wired one connected to a switch and want to let other machines hardwired to that same switch rout through the ubuntu box that's wirelessly connected via the first nic to my router. can't get this to work.

right now from my ubuntu i can:
- browse externally
- ping the nic on another hardwired node connected to the switch

from the hardwired node i can:
- ping the hardwired nic on ubnutu
- ping the wireless nic on ubuntu
- BUT i can not ping from all the way through the ubuntu machine to the router. nor can i get external.

can you tell what i mis-configured?

---

### Post by dannyboy79 on 2007-12-21
there's an option in firestarter to share internet connection. this should also help if you don't use firestarter:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=firestarter+internet+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=firestarter+internet+sharing)

---

