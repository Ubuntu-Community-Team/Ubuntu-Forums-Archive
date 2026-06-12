---
title: "wireless card"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by mr.farenheit on 2007-05-09
i have an internal wireless card in my notebook. it shows that ubuntu is reading it in the terminal, but is there a way to show its current status? i tried using the kwifi feature but that only looks for a pcmcia slot card.is there a program i should use to view my cards status or can i config kwifi?

---

### Post by jpeddicord on 2007-05-10
Try this:
```
iwlist CARD scan
```
Replace CARD with the the ID of your wireless chip in the system, such as 'eth1'.

Jacob
UAResolved

---

