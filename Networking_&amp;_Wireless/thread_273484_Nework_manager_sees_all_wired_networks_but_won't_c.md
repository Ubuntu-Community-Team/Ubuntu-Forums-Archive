---
title: "Nework manager sees all wired networks but won't connect?"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by joergenlie on 2006-10-08
Finally I got network manager to work, I thought](*,) 

I can see all the networks but there is no chance in connecting to them. I have removed everything but "lo" in the interfaces file, but still nothing. One strange thing though: when I try to connect to my home network, and after typing the wep key, the icon is spinning. When I move the cursor over it it says vaiting for key for my neighbours network which has no encryption? And when I try to connect to my neighbours network it says waiting to connect to my home network, which has encryption?

If there's a real mixup the answer is that nm tries to asks me to encrypt my neighbours network(but with the name of my home network) instead of mine and vice versa. Thats an annoying issue. Anyway any suggestions?

Jørgen 
fredrikstad 
Norge

---

### Post by joergenlie on 2006-10-16
Finally I managed to get it to work by using fwcutter instead of ndiswrapper, but now my network connection is really slow in comparison to using ndiswrapper. What the h... is this. i cant believe my eyes. Either its fast internet connection but no network manager or slow connection with network manager?

Any others experienced this, and/or have a solution?

Jørgen

---

### Post by ricks1950 on 2006-10-17
Network manager doesn't work for every configuration.  See the Mark Shuttleworth interview in Linux Format -- he says it works about 70% of the time.  It works on one of my laptops, but not the other, seems to depend on the card.

---

