---
title: "Weak Signal on Ubuntu..."
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by GSF1200S on 2007-04-07
If im running XP, the wireless signal strength of my home network is full (5 bars). Whenever I boot Ubuntu, I usually have 2 of 4 bars, and the actual percentage listed averages around 48-52%. 

Im not an idiot. A wireless card is just a receiver.. it doesnt send out a signal, as the router does that. So this just doesnt make sense.. The signal is bound to be the same strength. Maybe windows just says 5 bars until the very end of the network range where the bars quickly drop off, whereas the madwifi drivers are a little more realistic? The funny thing is, I actually detect MORE networks using Ubuntu than I do with windows..

Any ideas?

---

### Post by SishGupta on 2007-04-07
Yeah I've always thought this was a little strange and it has been the same for me since dapper.

Right next to my router (a literal 3 feet away) i get 75-85% max strength, but in windows it is 95%+

I am using an atheros based card as well.

Honestly it doesn't feel like the strength is the same either. It actually feels like i get that 15-25% less strength when i use ubuntu. Placebo effect perhaps, but I doubt it.

---

### Post by GSF1200S on 2007-04-07
> **SishGupta said:**
> Yeah I've always thought this was a little strange and it has been the same for me since dapper.

Right next to my router (a literal 3 feet away) i get 75-85% max strength, but in windows it is 95%+

I am using an atheros based card as well.

Honestly it doesn't feel like the strength is the same either. It actually feels like i get that 15-25% less strength when i use ubuntu. Placebo effect perhaps, but I doubt it.

weird.. It doesnt seem like my internet is any slower, but im currently sitting 3 feet from my router and im at 2 of 4 bars.. it says 48%...

---

### Post by josephus on 2007-04-07
i think it just has something to do with how madwifi and microsoft divers report information.  i've played around with both madwifi drivers and ndiswrapper and the link quality is always 100/100 with ndiswrapper, and much lower with madwifi.   The received signal strength is the same with both drivers, but the ndiswrapper of my windows drivers don't seem to report noise information correctly, being stuck at -256dBm.

---

