---
title: "How do you change wireless standards?"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by MasterNetra on 2015-04-01
I find my wireless strength to be much weaker in Mint/Ubuntu then in windows, with the wireless signal getting dropped often in Ubuntu, which never occurs in windows. I was looking around and I hear mention about wireless standards and was wondering how would I change which standard is being used? I have no Idea what windows 8.1 is using from my wireless card. Thanks in advance.

---

### Post by michi1983 on 2015-04-01
What you mean with wireless standards? The protocol?
This sounds to me like a driver issue to be honest.

---

### Post by MasterNetra on 2015-04-01
I mean like from using N to using b or g, I had read it's doable but didn't say how.

---

### Post by changingstate on 2015-04-04
Set the bitrates.  [https://wireless.wiki.kernel.org/en/users/documentation/iw](https://wireless.wiki.kernel.org/en/users/documentation/iw)

---

### Post by TheFu on 2015-04-06
> **MasterNetra said:**
> I mean like from using N to using b or g, I had read it's doable but didn't say how.

You buy new wifi equipment that supports the newer standards.  Both the computer and the AP/router need to support the same standard or you won't see any improvement. There are local considerations too - how many wifi networks and devices are in the area?  If the area is full of traffic, microwaves and you can only 2.4Ghz bands, there may not be much you can do to get better results.  OTOH, 5Ghz bands usually aren't used much at all, so equipment that works on those bands can get great throughput - provided there aren't walls between the sending and receiving devices. 5Ghz doesn't like walls or any obstructions much; the range is less.

Like others have said - this sounds like a driver configuration issue.  Not all wifi chips are well supported under Linux, so it may or may not be possible to get the same results as you see with highly tuned, Windows, drivers.

Of course, your current computer wifi might support the newer standards already, so it would just take an upgrade to the router/AP.  Under 802.11n standards, there are many substandards, so don't get burned.  There are N-75, N-150, N-300, N-450, N-600 standards which roughly equate to the theoretical maximum throughput. Assume 50% of the max with 1 device. 25% with 2 devices, etc. ... For example, I have a Dell laptop that has an N-compliant wifi card, but it is only 75Mbps, which isn't much use. I should have paid the extra $20 to get a N-300 wifi card.

---

