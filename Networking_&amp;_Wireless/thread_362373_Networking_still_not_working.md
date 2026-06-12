---
title: "Networking still not working?"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Touch.Code on 2007-02-15
Hey,

I can't get the XP wireless laptop to connect with the desktop 6.10 so that the desktop can have internet access.

ROUTER ---->> Laptop(Wirless) ---->> Desktop(Ethernet into laptop)

I do however have a serial cable, but can't figure out hopw to set that up for internet aswell.

Any help/ideas? Thanks

---

### Post by bnuytten on 2007-02-15
Just to be sure: is this a wireless router or not? If it is, you need to use wifi in "Infrastructure" mode. Otherwise you will need to use "Ad Hoc" mode. Other important things to know is the SSID and the Channel of the wireless network.

For further configuration of the wifi network, you will need to convince your laptop to actually forward IP packets. With linux this is quite easy:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
With windows XP you have to adjust the registry...

---

### Post by dmizer on 2007-02-15
i'm sorry but ... you have 3 threads (that i know of) on this subject.  you're better off posting on your old threads.  that way, it's easier for us to go through and make sure that your problem has been resolved.  keep it all together for my reference, your reference, as well as anyone else who may be having the same problem.

your best bet is going to be to buy a crossover cable ... they're not expensive, and it's going to be much less headache for you.

---

### Post by Touch.Code on 2007-02-16
Oh yeah sorry.

Its just my problem changed, but I am sorry, I will post on my old topics from now on.

---

