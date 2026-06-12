---
title: "Gutsy Broadcom Restricted Driver Question"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by snl2587 on 2007-10-21
Since I have the absolutely wonderful BCM4318 [AirForce One 54g] 802.11g Wireless LAN card in my laptop, I was wondering if it's better to stick with the ndiswrapper setup I used with Feisty or to use the restricted driver now that I've switched to Gutsy? I have noticed that while I could get 54 mbps with ndiswrapper (or so it claimed) Gutsy says I'm only getting 24 mbps with the restricted driver. I am, however, not experiencing any real problem with either one.

Of course for web browsing this doesn't make a difference....but I was just wondering.

---

### Post by jrharvey on 2007-10-23
I would like to know the answer to this also because while I have not used ndiswrapper I have noticed that the Gutsy restricted driver is lacking a bit. I cannot get more than 15 feet away from a router before all signal is gone. In windows the same card gets more than double that distance and is way faster. I was just curious.

---

### Post by jrharvey on 2007-10-23
I am going to bump this cuz i really want to know :)

---

### Post by snl2587 on 2007-10-23
Yeah, although after I got everything working with Gutsy I noticed that the restricted driver was a lot more flaky than the ndiswrappered driver under Feisty, so although I haven't tried ndiswrapper again since I've been busy I may have answered my own question.

---

### Post by jrharvey on 2007-10-24
has anyone else seen a performance decrease with the gutsy restricted drivers?

---

### Post by danconde on 2007-11-02
I did a fresh install and my wireless connection using the new restricted drivers won't go faster than 24M, even when I leave my notebook besides the router !!! I was using ndiswrapper in my previous install (6.06) and never had problems with speed. I have a broadcom 4318 wireless card.

---

### Post by kevdog on 2007-11-02
Right now the ndiswrapper solution is the way to go if you want performance and reliability.  Hopefully this will change in the future.

---

