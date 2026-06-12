---
title: "Linux compatible 802.11n-draft pcmcia cards"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by sheldonl on 2007-03-01
Hello,

I'm wondering if anyone knows which 802.11n (Draft) wireless pcmcia cards are known to work with Linux (either through ndiswrapper or natively/with fwcutter). Particularly I'm looking at buying the D-Link DWA-652 Xtreme N notebook adapter as the "
D-Link DIR-655 Xtreme N Gigabit Router" looks to be one of the best out there (and my router is currently dying a horrible death.)

Thanks in advance.

---

### Post by spd106 on 2007-03-03
I can't say I've heard of any native drivers for draft-n cards yet. There may be a web site out there that I haven't seen yet.

I do have a couple of thoughts about the d-link card though.

1. It doesn't work in the 5GHz band. If I was going to spend that much on a new card I'd want dual band capabilities. Particularly with the channel bonding, the 2.4 GHz band is going to get awfully crowded.

2. I have reservations about achieving the advertised performance with a card that uses the old 32bit cardbus connection. It probably won't see any great improvement over an 11g card.


The madwifi project is unlikely to support 11n any time soon, Intel are still a while off from releasing anything and they have a good track record with linux driver support. So unless Broadcom or some other manufacturer suddenly do us all a favour I don't hold much hope for the near future.

---

### Post by motin on 2007-03-28
I am choosing amongst the current draft n11 routers:
[LIST]
[*]Buffalo Airstation Nfiniti router
[*]D-Link N 650 router
[*]Trendnet N-Draft router TEW-631BRP
[*]Belkin N1 router
[*]Linksys WRT300N Draft N router
[*]Netgear WNR834B RangeMax Next router
[/LIST]

But in our case (Ubuntu-users) we need to choose not by performance, but by compatibility... especially when the different routers by rule works best only with the corresponding PC-Card / USB Card from the same manufacturer. 

So - Does anyone know if any of the following router's corresponding PC-Cards and/or USB-Cards work at any level (b/g is enough if it is likely n11 will be supported in the future)?

---

### Post by motin on 2007-03-28
I just found [http://linuxdevices.com/news/NS9921542023.html](http://linuxdevices.com/news/NS9921542023.html) through kc@freenode:#wireless (thanks), where Broadcom claims their first n-draft card is supported on Linux systems. 

Kind of in the dark about the rest. Anyone has more info?

---

### Post by spd106 on 2007-03-30
Good news everyone!

The madwifi project have announced experimental support for Atheros 11n based cards, specifically those using the AR5008. 

See [http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n](http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n)

---

### Post by motin on 2007-03-31
> **spd106 said:**
> Good news everyone!

The madwifi project have announced experimental support for Atheros 11n based cards, specifically those using the AR5008. 

See [http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n](http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n)

That is good news!

Can you or someone else tell us non-wifi champs what this actually means in support for respective cards to this router list:
    * Buffalo Airstation Nfiniti router
    * D-Link N 650 router
    * Trendnet N-Draft router TEW-631BRP
    * Belkin N1 router
    * Linksys WRT300N Draft N router
    * Netgear WNR834B RangeMax Next router
?

---

### Post by lx73 on 2007-06-04
The D-Link DIR-655

seems to have the Atheros AR5008 chipset

[http://www.itweek.co.uk/personal-computer-world/hardware/2187987/link-dir-655-xtreme-n-wireless](http://www.itweek.co.uk/personal-computer-world/hardware/2187987/link-dir-655-xtreme-n-wireless)

---

