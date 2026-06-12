---
title: "Wireless problem"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by ThenonS on 2007-05-20
I`m Having trouble with my wireless (go figure). been trying to sort it for 2 days with no luck.
I`m using ndiswrapper but its saying my driver is invalid
Here is waht comes up when I run  sudo lshw -C network

       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@03:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:febf0000-febfffff iomemory:febe0000-febeffff irq:11

I rly want this sorted becouse Its the only thing wrong with my system and I don`t like a 15m cable running through my house :).

all feed back is apprieciated

---

### Post by neocookie on 2007-05-21
I've also been having problems with my marvell card. I think its the same version. I've switched to windows until a suitable fix is found - a full week of no internet is hard going when you're a freelance web developer!

I'd recommend doing daily searches for Marvell, Libertas, and the model number (88w8335). You might find someone's managed to solve the problems you've been having. For me, it was that iwconfig wasn't setting/holding the essid (or any other params, for that matter) when the mode was "managed". "ad-hoc" would work, but since I was connecting to an access-point (tried 3 in all, with different/no encryptions) I couldn't get anywhere. Working on windows for the moment, but hope to move back once I've billed some more work and have the time to sort out the issues.

---

