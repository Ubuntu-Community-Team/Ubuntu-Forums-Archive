---
title: "improve wlan reception"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-28
Dear forum,

I've got a wlan device downstairs in the house and am trying to connect my desktop upstairs to it. The hub is a fritz box and the connector a DWA140.

My Ubuntu system sees about 7 networks from up to 600m away (through 2 concrete walls).

Why can't I see the router that is just downstairs?

If I put my laptop next to the desktop wireless adapter I can see the router signal 96% according to netmanager.

---

### Post by winotree on 2009-10-28
My little device can *see* other WLANs at a quarter-mile, similar to what yours does so having to stand next to the unit to get a decent signal makes no sense.

Don't know for a fact but an obvious first thought would be the wiring in the house that runs between the ceiling and floor -- that and any air conditioning ducts, etc., normally found in homes.  At least that's the answer to a test question on the MCSA.  :|

---

### Post by Soul-Sing on 2009-10-28
Maybe this site is helpful to solve your problem:
[http://www.freeantennas.com/](http://www.freeantennas.com/)

---

### Post by QLee on 2009-10-28
You might try changing to broadcast a different channel on the AP, if all or some of those other networks are on the same channel as yours there could be interference and those *might* be stronger than yours coming through a floor with wiring, as suggested by winotree.

Changing the orientation of the unit and different places in the room are worth trying also.

I seem to remember seeing this kind of report previously, there may be some wireless interfaces that have a known problem, I can't remember, perhaps you could try a forum search with your specific card as keyword.

---

### Post by RichardCL on 2009-10-29
> **winotree said:**
>  that and any air conditioning ducts, etc., normally found in homes.  At least that's the answer to a test question on the MCSA.  :|

10 points then for winotree and Qlee. My apartment is an old factory building and it turns out that the floors are made with pre-stressed concrete that also contains some waste steel.

I had enough of the wlan, after trying the antenna reflectors and moving the device all over the place. All the other devices are sharing channels 6-10 whereas I'm on channel 1. I even tried 5GHz band.

Then trying to route network cable, I wrecked 4 Tungsten carbide Hilti bits and realized just how much steel must be in that gallery floor!

Thanks for the tips. I'm now faced with the prospect of routing miles of CAT5 cable through the walls.

---

### Post by kerry_s on 2009-10-29
you can try looking at ethernet over power line adapters, i use several in are home to reach the downstairs, there just as fast as wired.

---

### Post by winotree on 2009-10-29
> ....My apartment is an old factory building and it turns out that the floors are made with pre-stressed concrete that also contains some waste steel.... Oh, man!  :shock:  I never would have guessed it was *that* bad!  This may sound really off-the-wall *but why don't you just run that cable out the window and in through the other window downstairs to the router* -- the cable is [for all practical purposes] waterproof, isn't it?  It'd be easier; it'd be cheaper;  > ....I'm now faced with the prospect of routing miles of CAT5 cable through the walls.... and you may have already thought of this, eh?  :-s  ;)

---

### Post by RichardCL on 2009-10-30
Turns out that I got lucky. After the reply from kerry_s I realised that there are still some power cables running through the building that are no longer in use. They aren't useful for Networking (not shielded or twisted) but I can use them to route the whole DSL upstairs. Downstairs only DECT signal is used for telephone functions. For some reason the DECT signal passes through the floor without problem.

---

