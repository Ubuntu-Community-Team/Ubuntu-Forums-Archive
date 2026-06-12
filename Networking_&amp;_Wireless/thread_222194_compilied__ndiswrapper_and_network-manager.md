---
title: "compilied  ndiswrapper and network-manager"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by discord on 2006-07-24
I compiled ndiswrapper due to the old version in the repos not supporting my card. It seems to work allright except with network-manager. We have discovered that the problem is the card will not be set by the calls that network-manager dameon makes for the card to set ssid, etc. Is there any specific change between the source version that would make this not work for my card?

---

### Post by reacocard on 2006-07-24
well, the network-manager in the repos is a bit out-of-date too. the latest version is 0.6.4, the repos have 0.6.2. you could try compiling that too.

---

