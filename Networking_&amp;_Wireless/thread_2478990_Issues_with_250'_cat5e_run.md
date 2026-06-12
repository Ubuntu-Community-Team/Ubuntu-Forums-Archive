---
title: "Issues with 250' cat5e run"
date: 2022-09-11
forum: Networking &amp; Wireless
---

### Post by JimLS on 2022-09-11
Have a 250' run underground between buildings that I am having trouble with.  It only shows connection at 10Mb and has some dropped packets.  It is in a separate low voltage conduit separated from power wires.  I triple checked the wiring, did tdr testing, reterminated, and tried the same on a spare cable in the same conduit.  Nothing helped.  I think it might just be the consumer switches on each and them being 'green' trying to save power as the cable should be good to 100 m.  So looking at options.  

Before the latest work and testing I shorted the cable about 25' and put the switch right at the entrance to the building which had a bit of improvement but still not good.  

So my options seem to be:

Put in Cat6 cable.  Not sure if this will really help much.

Go optical fiber.  I have a 1" PVC conduit with long sweeps so this looks fairly easy.

Get different end switches.  Either some older 10Mb limited hubs or switches or something that is more commercial and less green.  Not sure how to identify this equipment as being good for long runs.

Use some sort of xDSL or other end equipment designed for longer runs.  Not familiar with this equipment other than knowing something like this exists.

Powerline network equipment.  Would like to avoid as I have some power line signaling stuff already although I might consider this.

I don't need much speed.  10Mb would be good if it was reliable.  A bit more would be better but 100Mb is really more than needed.

---

### Post by TheFu on 2022-09-11
> CAT5e cables are typically 24-gauge twisted pair wires, which can support Gigabit networks at segment distances **up to** 100 m.

Does the cable length work BEFORE it is in the conduit?  Grounding might be needed.

Is MoCA an option? MoCA claims 300' is possible and supports 2.5Gbps.

There's also point-to-point wifi.  Ubiguiti sells this stuff. Probably more than you want to pay, but the 22-24Ghz bandwidth (I don't recall which) can move some data over 100km.  

They used to have small outdoor m2 models that would to 54Mbps connections. This assumes line of sight. For low speed, directional wifi is how I'd do it with small directional antennas.  [https://arstechnica.com/gadgets/2021/08/point-to-point-wi-fi-bridging-between-buildings-the-cheap-and-easy-way/](https://arstechnica.com/gadgets/2021/08/point-to-point-wi-fi-bridging-between-buildings-the-cheap-and-easy-way/)  Looks like they call these devices "wifi outdoor bridges".  [https://www.amazon.com/Wireless-CPE200-High-Gain-Antenna%EF%BC%8C24V-Waterproof/dp/B0B6B5XL9F/](https://www.amazon.com/Wireless-CPE200-High-Gain-Antenna%EF%BC%8C24V-Waterproof/dp/B0B6B5XL9F/) is $77.

Do you have line of sight?

---

### Post by JimLS on 2022-09-11
Didn't try it out of the conduit as I was expecting it to just work.  Grounding?  Ethernet isn't grounded but perhaps you mean a shield.  That shouldn't be needed.  I measured voltage with a voltmeter and a scope and any noise was so low as to be almost undetected.

Yes, cost is a factor.  Looking at prices in the comparison of options.

Don't have line of sight.  Trees in the way.

---

### Post by #&amp;thj^% on 2022-09-11
> **JimLS said:**
> Grounding?  Ethernet isn't grounded but perhaps you mean a shield.  

Yes and No, Its the connector that's grounded. [https://www.truecable.com/blogs/cable-academy/how-to-terminate-a-shielded-cat5e-internal-ground-pass-through-rj45-connector#](https://www.truecable.com/blogs/cable-academy/how-to-terminate-a-shielded-cat5e-internal-ground-pass-through-rj45-connector#)
TheFu has some very helpful suggestions. You probably wouldn't be surprised, but cabling makes a big difference. [https://community.spiceworks.com/topic/2124340-direct-burial-cat5e-grounding](https://community.spiceworks.com/topic/2124340-direct-burial-cat5e-grounding)
Good Luck though. ;)
EDIT: You just can't make this stuff up but, Ok I just asked this, "Is it ok just running the plain cable from one point to the other (outside walls, around 120 feet, and both ends entering the house) and just grounding the point which is nearer to the ground rod? thanks again for any advise. "

Yes, if you ground the lower point to the nearest ground, that should be fine.
Generally CAT5e cable is not shielded so you will have to make sure to buy the shielded variety if you want to shield it. 

The best place to ground the CAT5e cable is to the chassis of the modem. That works well *when the modem is AC powered with an three prong AC cord that then connects to a valid grounded three prong AC outlet*.

If the cable equipment is not grounded at the AC plug then your better bet is to find a way to run the cable inside the walls.

---

### Post by razzmataz on 2022-09-18
Do you have access to a cable tester, or signal injector? It's not a cheap piece of diagnostic equipment, but it will tell you if your cable has problems.

---

### Post by coop589 on 2022-09-26
Can you measure the attenuation of the cable with the equipment you used to measure TDR?  It could either be excessive cable loss or the cable cannot support the higher connection speed due to the cable itself (crosstalk, noise, etc).  If you have access to a spool of wire, you should see how the cable sweeps from any inventory you might have available.  Maybe the issue could be a simple fix like changing the connectors you are using for more robust connectors.  A tool that can sweep CAT5e cables with the pass/fail thresholds will highlight what is wrong with your cable.

Let us know what you find and any resolution that you came up with.

---

