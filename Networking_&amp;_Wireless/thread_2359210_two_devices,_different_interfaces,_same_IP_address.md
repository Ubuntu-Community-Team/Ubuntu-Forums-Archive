---
title: "two devices, different interfaces, same IP address"
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2017-04-21
I connect two devices that have the same hard-coded IP addresses via USB and they show up as different interfaces, usb0 and usb1 each interface with its own IP address, but on the same sub-net.

Is there a way I can address them individually? I'm specifically wanting to ftp files to them (they have ftp servers running, which work fine when I connect one-at-a-time).

I'm thinking/guessing not, but I wonder if there are any clever tricks. For example, perhaps something with NAT on each port...have a VM running NAT for each interface, doing NAT for the IP address, like having a one port router on each device? Perhaps docker would work better? It all sounds a bit complicated...anything simpler?

Max.

---

### Post by SeijiSensei on 2017-04-21
Unless you "bond" the interfaces together there is little to be gained from having them both on the same subnet, and routing problems can arise if you do.  Choose one or the other, or look into [bonding]("https://help.ubuntu.com/community/UbuntuBonding").

---

### Post by davidmaxwaterman on 2017-04-21
Fortunately, I don't want any routing...apart from being able to distinguish between the hosts on each interface. I simply need to be able to ftp files from the host to each server. Perhaps that is 'little' in some people's eye, but it is my only objective.

If I had each plugged into a nat router, and then the router plugged into my host, then it would work, right; since the routers would translate from the common IP address to a unique one, and ftp would be able to address each router individually since their IP addresses would be given out by my host's DHCP server.

That's kind of why I was considering having VMs or docker images (I've no experience of them)...they'd each be configured to see only one of the USB interfaces and so there would be no routing problems.

Would that not work? Is there a simpler way?

(I'll look at bonding, but it seems like it would only make the situation worse - ie I can't distinguish between devices even by the interface they're connected to...broadcast mode sounds interesting)

Max.

---

### Post by davidmaxwaterman on 2017-04-21
> **SeijiSensei said:**
> Unless you "bond" the interfaces together there is little to be gained from having them both on the same subnet, and routing problems can arise if you do.  Choose one or the other, or look into [bonding]("https://help.ubuntu.com/community/UbuntuBonding").

Actually, what you suggest is interesting. I suppose it could work just doing one at a time, and switching between them using routing. I don't think there is much advantage in trying to transfer over the same USB cable to multiple hosts at once (perhaps that's what you meant?), so one at a time might work fine, and automating the route change seems easy enough. Yes, I'll give that a try.

The broadcast mode of bonding might be worth investigating (perhaps in the case of using multiple usb connections/controllers), but it does seem somewhat complex.

Thanks!

---

