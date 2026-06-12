---
title: "wifi routers have crazy unreliability"
date: 2014-11-19
forum: Networking &amp; Wireless
---

### Post by v1nsai2 on 2014-11-19
I recently bought a mid-range price wireless-N router, and have had nothing but problems with it.  My idiot roommate swore that she would take it back and never did, so I'm stuck with it.

Basically, it sometimes works fine, but sometimes it the latency shoots through the roof and it starts dropping packets.  Then just stops.  I've run pings on it directly from my machine and had the latency get as high as over 1000ms with over 10% packet loss.  Then it stops and goes back to normal.

The same thing was happening with our old router as well.  I thought it might have something to do with the fact that we're in an apartment so lots of other wifi traffic.  I used a wifi analyzer and put it on the channel with the least amount of traffic, but even at 6am (no one is using the internet at 6am here it's all college students) it still sometimes does this.  But it also sometimes works fine, even at peak traffic hours when everyone in the complex is probably online.

I've also tried re-flashing the factory firmware from my computer and completely wiping it.  Still the same problems.

My conclusion has been that wifi routers are fickle four-letter-words, but I was wondering if someone with more knowledge of wifi routers could suggest something?  I'm really wondering what's happening here.

---

### Post by slickymaster on 2014-11-19
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by ajgreeny on 2014-11-19
I suspect this is more to do with the wireless adapter in your computer than the router itself.

What wireless card have you got; you can see this from command **lspci** in terminal, and what router do you have?

---

### Post by weatherman2 on 2014-11-19
Routers are not all created equal.  These days, I don't buy anything that can't run TomatoUSB firmware or at least DD-WRT.

I have TomatoUSB running on a Cisco/Linksys E3000 dual band router, and it works very well in an environment with numerous other radios nearby.  My wireless devices can mostly do 5GHZ as well so I use that whenever possible instead of 2.4GHZ to get better speed between my NAS and my devices when transferring files.  But even on 2.4GHZ, reliability is solid - I got many hours without any sort of drop or disconnect.  Once in a great while I have issues, but it's rare.

I like Intel wireless cards.  I've upgraded a few laptops to use the Intel 6235 dual band card with bluetooth.   But as suggested above, tuning the card you have may improve connectivity issues.  Unless you have an HP or Lenovo laptop, you could probably upgrade the wireless card in it if you want to.  Depending on the make/model of laptop, replacing the card may not be very difficult or expensive.

---

### Post by v1nsai2 on 2014-11-19
> **weatherman2 said:**
> Routers are not all created equal.  These days, I don't buy anything that can't run TomatoUSB firmware or at least DD-WRT.

I have TomatoUSB running on a Cisco/Linksys E3000 dual band router, and it works very well in an environment with numerous other radios nearby.  My wireless devices can mostly do 5GHZ as well so I use that whenever possible instead of 2.4GHZ to get better speed between my NAS and my devices when transferring files.  But even on 2.4GHZ, reliability is solid - I got many hours without any sort of drop or disconnect.  Once in a great while I have issues, but it's rare.

I like Intel wireless cards.  I've upgraded a few laptops to use the Intel 6235 dual band card with bluetooth.   But as suggested above, tuning the card you have may improve connectivity issues.  Unless you have an HP or Lenovo laptop, you could probably upgrade the wireless card in it if you want to.  Depending on the make/model of laptop, replacing the card may not be very difficult or expensive.

This one can handle DD-WRT, but is it really better at doing the most basic thing a router can do, y'know....route?  I'd understand if some advanced feature wasn't working correctly, but all I want it to do is pass packets to and from the internet between my computer and maybe 4 other connected endnodes.  Is Linksys that terrible?

I'll have to wait until my roommate isn't around for a few hours to try it.

> **[COLOR=#000000]ajgreeny[/COLOR]][COLOR=#000000]I suspect this is more to do with the wireless adapter in your computer than the router itself.[/COLOR]

[COLOR=#000000]What wireless card have you got said:**
> **lspci in terminal, and what router do you have?**

I suspected that, but I've tried pinging the router from both my Android phone and my iPad also and gotten latency of over 1000ms while standing next to it.

---

