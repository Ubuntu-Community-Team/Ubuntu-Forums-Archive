---
title: "Wireless prob: No Free Txdesc free"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by Lylepalooza on 2007-05-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/69717](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/69717) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**Problem: **I am trying to get a **WG311v2** wireless card (Netgear 54mbps) to connect with my Netgear router on Ubuntu Feisty Fawn 2.6.20-15-generic.
I have tried several different methods to fix this (listed below) but always get the repeated line:

**acx: BUG: no free txdesc left**

I have searched through many other posts on the topic and can post them here for reference if needed.

Facts:
My wifi card can see my router and pick up its essid.
Link quality is generally about 50%, and Signal Level is generally around 30%
I have tried removing Network Manager and using WICD, but there was no joy.
I tried reinstalling Network Manager (after a fresh install) but no joy.
The wireless has worked on Ubuntu out of the box, but would drop for a week with the above acx message. When it comes back it is generally for a night and then it is gone for a week. 
I tried changing the options to point to the older driver (1.2.1.34) but that didn't help it either.
My motherboard is miniATX and only has three PCI slots, two of them full. One has the Wifi card and the other has a Digital TV card. When I swapped them, the computer didn't recognise any of the services the TV card provides, but when I swapped it back it did. The wifi card doesn't seem to be recognised any different by hardware monitor in either slot. (I can't put it in the third slot as my agp card's fan is too big).

It would seem that the above would suggest that it is an IRQ conflict, but I am unaware how to change that. It seems to share an IRQ with the onboard LAN.

So perhaps some of the questions would be:
1. How would I go about freeing tx desc? (I am not actually sure what tx desc is as I can't find any reference on it on google).
2. How would I go about giving my wifi card a reserved IRQ, so that it doesn't share it with anything. Would disabling the onboard LAN work? if so, what is the best way to do this?

If anybody wants me to post any log info, let me know which. I am typing this from a downstairs computer so I will have to run back and forth to get the files.

PS There is a bug report attached that gives almost identical info to what is happening with my setup.
Thank you for any assistance you can provide.

---

